# Spec Módulo G — Admin / Dashboard

**Versión:** 1.0.0  
**Autor:** Hermes 🏔️  
**Fecha:** 2026-05-26  
**Estado:** BORRADOR — Pendiente aprobación de Cristian  
**Evaluación:** Eval 5 (equipos de 3 estudiantes)

---

## 1. ¿QUÉ y POR QUÉ?

### Problema

Los administradores del ecommerce (dueños de la tienda) necesitan visibilidad sobre el estado del negocio: ventas, usuarios, stock de productos y comportamiento de la tienda. Sin un panel de administración, no es posible tomar decisiones informadas.

### Objetivo

Construir un panel de administración (dashboard) que permita a usuarios con rol **admin** gestionar productos, visualizar reportes de ventas, administrar usuarios y monitorear el inventario.

---

## 2. Funcionalidades

| # | Funcionalidad | Descripción | Prioridad |
|---|--------------|-------------|-----------|
| 1 | **Dashboard principal** | Tarjetas resumen: ventas del día, total usuarios, productos activos, órdenes pendientes | Alta |
| 2 | **CRUD productos** | Listar, crear, editar, eliminar productos con imagen, precio, stock y categoría | Alta |
| 3 | **Gestión de pedidos** | Ver historial de pedidos, cambiar estado (pendiente, pagado, enviado, entregado, cancelado) | Alta |
| 4 | **Gestión de usuarios** | Listar usuarios, cambiar roles, deshabilitar cuentas | Alta |
| 5 | **Reporte de ventas** | Gráfico de ventas por día/semana/mes, totales, productos más vendidos | Media |
| 6 | **Alertas de stock** | Listar productos con stock bajo (menor al mínimo definido) | Media |
| 7 | **Exportar reportes** | Descargar reportes en CSV/PDF | Baja |

---

## 3. Stack

| Capa | Tecnología |
|------|-----------|
| Frontend | HTML5 + CSS3 + Bootstrap 5.3 + JS Vanilla |
| Gráficos | Chart.js (CDN) |
| Backend | PHP 8 (REST API) |
| Base de datos | MySQL (misma BD del ecommerce) |
| Autenticación | Middleware de verificación de rol admin (reutiliza Módulo C) |

---

## 4. Contratos API (Módulo G)

### 4.1. Dashboard

```
GET /api/admin/dashboard
Headers: Authorization: Bearer {token_admin}
Response:
{
  "resumen": {
    "ventas_hoy": 450000,
    "ventas_semana": 2100000,
    "ventas_mes": 8500000,
    "total_usuarios": 120,
    "productos_activos": 45,
    "pedidos_pendientes": 8
  },
  "ventas_recientes": [
    {"fecha": "2026-05-25", "monto": 85000, "cantidad": 3}
  ]
}
```

### 4.2. Productos (CRUD)

```
GET    /api/admin/productos?pagina=1&limite=20
POST   /api/admin/productos        {nombre, precio, stock, categoria_id, descripcion, imagen}
PUT    /api/admin/productos/{id}   {nombre, precio, stock, categoria_id, descripcion, imagen}
DELETE /api/admin/productos/{id}
```

### 4.3. Pedidos

```
GET    /api/admin/pedidos?estado=pagado&pagina=1
GET    /api/admin/pedidos/{id}
PUT    /api/admin/pedidos/{id}/estado  {estado: "enviado"}
```

### 4.4. Usuarios

```
GET    /api/admin/usuarios?pagina=1
GET    /api/admin/usuarios/{id}
PUT    /api/admin/usuarios/{id}/rol   {rol: "admin"|"cliente"}
PUT    /api/admin/usuarios/{id}/estado {activo: true|false}
```

### 4.5. Reportes

```
GET /api/admin/reportes/ventas?desde=2026-01-01&hasta=2026-05-26&agrupacion=dia
Response: {datos: [{fecha, total, cantidad_pedidos}], total_periodo: 15000000}

GET /api/admin/reportes/productos-mas-vendidos?limite=10
Response: {productos: [{id, nombre, cantidad_vendida, total_generado}]}
```

### 4.6. Alertas de stock

```
GET /api/admin/alertas-stock
Response: {alertas: [{producto_id, nombre, stock_actual, stock_minimo}]}
```

---

## 5. Estructura de Archivos

```
public/admin/
├── dashboard.php          # Panel principal con resumen y gráficos
├── productos.php          # CRUD de productos
├── pedidos.php            # Gestión de pedidos
├── usuarios.php           # Gestión de usuarios
├── reportes.php           # Reportes de ventas
├── alertas-stock.php      # Alertas de inventario
└── assets/
    ├── css/
    │   └── admin.css
    └── js/
        ├── dashboard.js
        ├── productos.js
        └── reportes.js

src/controllers/
├── AdminController.php    # Lógica del dashboard
├── ProductoAdminController.php
├── PedidoAdminController.php
├── UsuarioAdminController.php
└── ReporteController.php
```

---

## 6. Dependencias

| Módulo | Dependencia de | Qué necesita |
|--------|---------------|--------------|
| G (Admin) | C (Autenticación) | Middleware de verificación de rol admin |
| G (Admin) | A (Catálogo) | Modelo de productos y categorías |
| G (Admin) | F (Inventario) | Datos de stock y movimientos |
| G (Admin) | D (Checkout/Pedidos) | Datos de pedidos y detalle |

---

## 7. Criterios de Éxito

- [ ] Usuario admin puede ver dashboard con indicadores actualizados
- [ ] CRUD completo de productos funcional
- [ ] Gestión de pedidos: listar, filtrar por estado, cambiar estado
- [ ] Gestión de usuarios: listar, cambiar rol, deshabilitar
- [ ] Reporte de ventas con gráfico (Chart.js)
- [ ] Alertas de stock bajo visibles en dashboard
- [ ] Middleware de autenticación verifica rol admin en cada ruta

---

## 8. Consideraciones de UX

- Navegación lateral con secciones claras (Dashboard, Productos, Pedidos, Usuarios, Reportes)
- Confirmación antes de eliminar productos o deshabilitar usuarios
- Feedback visual inmediato (toast/alert) después de cada acción CRUD
- Paginación en listas con más de 20 registros
- Gráficos responsivos (Chart.js con opciones responsive)
