# Spec General — Ecommerce Académico (TINF1113)

**Versión:** 1.0.0  
**Autor:** Hermes 🏔️ (en representación del equipo War Room)  
**Fecha:** 2026-05-26  
**Estado:** BORRADOR — Pendiente aprobación de Cristian  
**Evaluaciones:** Evaluación 4 (curso completo) → Evaluación 5 (equipos de 3)

---

## 1. ¿QUÉ y POR QUÉ?

### Problema

Los estudiantes de TINF1113 requieren un proyecto integrador que abarque el ciclo completo de desarrollo web: desde la estructuración de datos hasta el despliegue con pasarela de pagos real. El curso necesita una aplicación que:

- Permita el trabajo colaborativo de **~36 estudiantes como un solo equipo** (Eval 4).
- Evolucione a **equipos de 3 personas** que extiendan el código base con sus propias funcionalidades (Eval 5).
- Siga la metodología **Discovery → Delivery** con spec-driven development.

### Objetivo General

Construir un ecommerce funcional con catálogo de productos, carrito de compras, autenticación de usuarios, pasarela de pagos Transbank (Webpay Plus) y gestión de inventarios, aplicando los principios de calidad defendible, spec-first e inmediatamente aplicable.

### Objetivos Específicos (Eval 4)

| # | Objetivo | Módulo(s) |
|---|----------|-----------|
| 1 | Implementar catálogo de productos con filtros, búsqueda y vista detalle | A — Catálogo |
| 2 | Desarrollar carrito de compras con persistencia de sesión | B — Carrito |
| 3 | Implementar registro, login y roles de usuario (cliente/admin) | C — Autenticación |
| 4 | Construir flujo de checkout con datos de envío | D — Checkout |
| 5 | Integrar pasarela de pagos Transbank Webpay Plus | E — Pasarela |
| 6 | Gestionar inventario con stock, altas/bajas y alertas | F — Inventario |
| 7 | Coordinar la integración y compatibilidad entre módulos A–F | H — Orquestación |

### Objetivos Específicos (Eval 5)

Cada equipo de 3 estudiantes hereda el código base de Eval 4 y extiende con:

| Opción | Funcionalidad |
|--------|---------------|
| G — Admin/Dashboard | Reportes de ventas, gestión de usuarios, históricos, analytics |
| IA — Recomendaciones | Sistema de recomendación de productos basado en IA |
| Pasarela real | Integración productiva con Transbank (no mock) |
| UX avanzada | Mejoras de experiencia de usuario, animaciones, feedback visual |

---

## 2. Stack Tecnológico

| Capa | Tecnología | Versión |
|------|-----------|---------|
| Frontend | HTML5 + CSS3 + Bootstrap | 5.3.x |
| Frontend dinámico | JavaScript vanilla (fetch API, DOM) | ES6+ |
| Backend | PHP | 8.x |
| Base de datos | MySQL | 8.x |
| Pasarela de pagos | Transbank Webpay Plus (SDK PHP) | — |
| Control de versiones | Git + GitHub | — |
| Hosting | DirectAdmin (proyectoskc.cl) — tentativo | — |

> **Nota:** El stack puede ajustarse según disponibilidad del hosting. Alternativa: Flask + Python si la migración desde PHP se justifica.

---

## 3. Arquitectura General

```
┌─────────────────────────────────────────────┐
│                  FRONTEND                    │
│  HTML5 + CSS3 + Bootstrap 5.3 + JS Vanilla  │
│                                              │
│  [Catálogo] [Carrito] [Login] [Checkout]     │
│  [Admin/Dashboard] [Perfil]                  │
└─────────────────┬───────────────────────────┘
                  │ HTTP (fetch API)
                  ▼
┌─────────────────────────────────────────────┐
│               BACKEND (PHP 8)               │
│                                              │
│  REST API por módulo                        │
│  - /api/productos/*                         │
│  - /api/carrito/*                           │
│  - /api/auth/*                              │
│  - /api/checkout/*                          │
│  - /api/pago/*                              │
│  - /api/inventario/*                        │
│  - /api/admin/*                             │
└─────────────────┬───────────────────────────┘
                  │ PDO / MySQLi
                  ▼
┌─────────────────────────────────────────────┐
│              BASE DE DATOS                  │
│                  MySQL                      │
│                                              │
│  Tablas: productos, categorías, usuarios,    │
│  carrito, pedidos, detalle_pedido,           │
│  transbank_transacciones, inventario_mov,    │
│  roles_permisos                              │
└─────────────────────────────────────────────┘
```

### Estructura de carpetas

```
ecommerce/
├── public/                   # Raíz web (index.php)
│   ├── index.php            # Landing / catálogo
│   ├── login.php
│   ├── registro.php
│   ├── carrito.php
│   ├── checkout.php
│   ├── pago/
│   │   ├── iniciar.php      # Inicia transacción Webpay
│   │   └── retorno.php      # POST de retorno Transbank
│   ├── admin/
│   │   ├── dashboard.php
│   │   ├── productos.php
│   │   ├── usuarios.php
│   │   ├── pedidos.php
│   │   └── inventario.php
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   │   └── images/
│   └── .htaccess
├── src/                      # Lógica de negocio
│   ├── config/
│   │   ├── database.php     # Conexión PDO
│   │   └── transbank.php    # Config pasarela
│   ├── controllers/
│   ├── models/
│   ├── services/
│   └── middleware/
│       └── auth.php         # Verificación sesión/roles
├── tests/                    # Tests (si aplica)
├── docs/                     # Documentación
│   ├── api-contracts/        # Contratos entre módulos
│   │   ├── modulo-a-catalogo.yaml
│   │   ├── modulo-b-carrito.yaml
│   │   └── ... (por módulo)
│   └── db/
│       └── schema.sql        # Esquema completo
├── spec.md                   # Este archivo
├── plan.md                   # Plan de implementación
├── tasks.md                  # Tareas atómicas
└── README.md                 # Guía rápida
```

---

## 4. Contratos entre Módulos (API Contracts)

Cada equipo implementa su módulo contra contratos definidos. No se desvían de ellos sin coordinar con el equipo de orquestación (Módulo H).

### 4.1. Módulo A → Módulo B (Catálogo → Carrito)

| Ruta | Método | Request | Response |
|------|--------|---------|----------|
| `/api/productos/listar` | GET | `?categoria=X&buscar=Y&pagina=Z` | `{productos: [...], total, pagina}` |
| `/api/productos/detalle` | GET | `?id=123` | `{id, nombre, precio, stock, descripcion, imagen, categoria}` |

### 4.2. Módulo C → Módulo D (Autenticación → Checkout)

| Ruta | Método | Request | Response |
|------|--------|---------|----------|
| `/api/auth/usuario` | GET | Header: `Authorization: Bearer {token}` | `{id, nombre, email, direcciones: [...]}` |
| `/api/auth/verificar` | POST | `{token}` | `{valido: bool, usuario: {id, rol}}` |

### 4.3. Módulo B → Módulo D (Carrito → Checkout)

| Ruta | Método | Request | Response |
|------|--------|---------|----------|
| `/api/carrito/resumen` | GET | Header: `Authorization` | `{items: [...], subtotal, total, cantidad_items}` |
| `/api/carrito/validar` | POST | `{token}` | `{valido: bool, items_disponibles: [...], items_agotados: [...]}` |

### 4.4. Módulo D → Módulo E (Checkout → Pasarela)

| Ruta | Método | Request | Response |
|------|--------|---------|----------|
| `/api/pago/iniciar` | POST | `{pedido_id, monto, token}` | `{url_webpay, token_ws}` |
| `/api/pago/confirmar` | POST | `{token_ws, token}` | `{exitoso, pedido_id, codigo_autorizacion}` |

### 4.5. Módulo D → Módulo F (Checkout → Inventario)

| Ruta | Método | Request | Response |
|------|--------|---------|----------|
| `/api/inventario/descontar` | POST | `{items: [{producto_id, cantidad}], pedido_id}` | `{exitoso, items_procesados}` |
| `/api/inventario/verificar` | POST | `{items: [{producto_id, cantidad}]}` | `{disponible: bool, items_con_stock: [...], sin_stock: [...]}` |

### 4.6. Módulo F → Módulo A (Inventario → Catálogo)

| Ruta | Método | Request | Response |
|------|--------|---------|----------|
| `/api/inventario/stock` | GET | `?producto_id=123` | `{producto_id, stock_actual, stock_minimo}` |

---

## 5. Esquema de Base de Datos

### Tablas principales

```
categorias             productos              usuarios
├── id (PK)            ├── id (PK)            ├── id (PK)
├── nombre             ├── categoria_id (FK)  ├── nombre
├── slug               ├── nombre             ├── email (UNIQUE)
└── descripcion        ├── slug               ├── password_hash
                        ├── descripcion        ├── rol (cliente|admin)
                        ├── precio             ├── direccion
                        ├── stock              ├── telefono
                        ├── imagen             ├── creado_en
                        ├── activo             └── ultimo_login
                        ├── creado_en
                        └── actualizado_en

carrito                  pedidos                detalle_pedido
├── id (PK)              ├── id (PK)            ├── id (PK)
├── usuario_id (FK)      ├── usuario_id (FK)    ├── pedido_id (FK)
├── producto_id (FK)     ├── total              ├── producto_id (FK)
├── cantidad             ├── estado             ├── cantidad
├── sesion_id            ├── direccion_envio    ├── precio_unitario
└── agregado_en          ├── metodo_pago        └── subtotal
                          ├── token_ws
                          ├── codigo_auth
                          ├── creado_en
                          └── actualizado_en

transbank_transacciones   inventario_mov
├── id (PK)               ├── id (PK)
├── pedido_id (FK)        ├── producto_id (FK)
├── token_ws              ├── tipo (entrada|salida|ajuste)
├── monto                 ├── cantidad
├── estado                ├── referencia (pedido_id o nota)
├── codigo_autorizacion   ├── usuario_id (FK)
├── fecha_creacion        └── creado_en
└── fecha_actualizacion
```

---

## 6. Roles y Permisos

| Rol | Acceso |
|-----|--------|
| **Invitado** | Ver catálogo, ver detalle de productos |
| **Cliente** | Todo lo de invitado + agregar al carrito, checkout, ver historial de pedidos |
| **Admin** | Todo lo de cliente + CRUD productos, gestión usuarios, ver reportes, gestión inventario |

---

## 7. Flujo de una Compra Exitosa

```
1. Cliente navega catálogo (A)          → GET /api/productos/listar
2. Agrega producto al carrito (B)       → POST /api/carrito/agregar
3. Inicia sesión / se registra (C)      → POST /api/auth/login
4. Revisa carrito y procede (B→D)       → GET /api/carrito/resumen
5. Ingresa datos de envío (D)           → POST /api/checkout/direccion
6. Inicia pago Transbank (D→E)         → POST /api/pago/iniciar
7. Redirige a Webpay → paga → retorna   → Transbank → POST /api/pago/retorno
8. Confirma pago (E→D)                 → POST /api/pago/confirmar
9. Descuenta inventario (D→F)          → POST /api/inventario/descontar
10. Muestra resumen de compra (D)      → GET /api/pedido/{id}
```

---

## 8. Glosario para Estudiantes

| Término | Significado |
|---------|-------------|
| **API Contract** | Acuerdo explícito entre dos equipos sobre cómo se comunican sus módulos (qué ruta, qué parámetros, qué devuelve) |
| **Bus de eventos** | Sistema donde los mensajes fluyen entre componentes; aquí Git funciona como bus de eventos textual |
| **Mock** | Simulación de un componente real (ej: pasarela de pagos falsa) para poder desarrollar sin depender del servicio real |
| **Pasarela de pagos** | Servicio externo que procesa pagos con tarjeta de crédito/débito de forma segura |
| **Orquestación** | Coordinación entre múltiples módulos para que funcionen como un sistema integrado |
| **Spec-Driven Development** | Metodología donde primero se escribe la especificación (qué y por qué) y luego se implementa |

---

## 9. Criterios de Éxito (Eval 4)

- [ ] Todos los módulos A–F implementan los contratos definidos en `docs/api-contracts/`
- [ ] El flujo completo de compra funciona de extremo a extremo (catálogo → pago → confirmación)
- [ ] No hay dependencias cruzadas entre módulos que no estén especificadas en contratos
- [ ] La integración (Módulo H) se completa sin conflictos de merge mayores
- [ ] La base de datos se despliega con el esquema unificado

---

## 10. Pendiente de Decisión

- [ ] **Stack definitivo:** PHP 8 (actual) vs Flask/Python (alternativa) — confirmar con Cristian
- [ ] **Hosting:** DirectAdmin (proyectoskc.cl) — verificar disponibilidad para estudiantes
- [ ] **Mock de Transbank:** Usar SDK en modo integración (testing) de Transbank
- [ ] **Rúbrica detallada:** Definir puntajes para Eval 4 y Eval 5 (seguir formato TINF1113)
