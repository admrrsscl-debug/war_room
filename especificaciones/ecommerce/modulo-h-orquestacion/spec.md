# Spec Módulo H — Orquestación e Integración

**Versión:** 1.0.0  
**Autor:** Hermes 🏔️  
**Fecha:** 2026-05-26  
**Estado:** BORRADOR — Pendiente aprobación de Cristian  
**Evaluación:** Eval 4 (coordinación del curso completo)

---

## 1. ¿QUÉ y POR QUÉ?

### Problema

~36 estudiantes trabajando en paralelo en 6 módulos independientes (A–F) inevitablemente generarán conflictos de integración: interfaces que no coinciden, datos que no fluyen entre módulos, estilos visuales inconsistentes, y merges conflictivos. Sin un equipo de orquestación dedicado, el caos está garantizado.

### Objetivo

Coordinar la integración de los módulos A–F del ecommerce, garantizando que los contratos entre módulos se cumplan, que el merge sea ordenado y que el producto final funcione como un sistema cohesivo.

### Rol del Módulo H

El Módulo H **no implementa funcionalidad de negocio**. Su propósito es **habilitar** que los demás módulos funcionen juntos. Es el pegamento del proyecto.

---

## 2. Responsabilidades del Equipo de Orquestación

| # | Responsabilidad | Descripción | Cuándo |
|---|----------------|-------------|--------|
| 1 | **Definir API contracts** | Redactar los contratos entre módulos ANTES de que los equipos empiecen a codificar | Antes del desarrollo |
| 2 | **Crear repositorio base** | Configurar estructura de carpetas, .gitignore, archivos de configuración comunes | Inicio |
| 3 | **Proveer mocks** | Crear versiones mock de cada módulo para que los equipos puedan probar sin dependencias | Durante desarrollo |
| 4 | **Middleware de autenticación** | Implementar el middleware de sesión/roles que todos los módulos usarán | Semana 1 |
| 5 | **Configuración de BD** | Crear el schema.sql unificado, migraciones iniciales | Semana 1 |
| 6 | **Revisar pull requests** | Asegurar que cada módulo entregue código que cumpla los contratos | Durante desarrollo |
| 7 | **Merge y resolución de conflictos** | Integrar las ramas de cada módulo en main, resolver conflictos | Al final del desarrollo |
| 8 | **Pruebas de integración** | Verificar que el flujo completo funcione (catálogo → pago → confirmación) | Post-merge |
| 9 | **Estilo visual cohesivo** | Asegurar que todos los módulos usen la misma plantilla Bootstrap y CSS base | Transversal |

---

## 3. Flujo de Integración

```
Semana 1
├── H crea repositorio base + schema.sql + .gitignore
├── H define API contracts (docs/api-contracts/*.yaml)
├── H implementa middleware de autenticación (src/middleware/auth.php)
├── H crea configuración de BD (src/config/database.php)
└── Cada equipo recibe sus contracts y comienza desarrollo

Semanas 2–3
├── H provee mocks de módulos vecinos
├── Cada equipo desarrolla en su rama (modulo-a, modulo-b, ...)
├── H revisa PRs contra contracts
└── H resuelve dudas de interfaz entre equipos

Semana 4
├── Hmerge ramas: modulo-a → main, modulo-b → main, ...
├── H resuelve conflictos de merge
├── H ejecuta pruebas de integración
└── H corrige incompatibilidades

Entrega
└── H presenta ecommerce integrado funcionando
```

---

## 4. Mocks que H debe Proveer

Cada mock implementa el mismo contrato API que el módulo real pero devuelve datos estáticos.

| Módulo | Mock | Propósito |
|--------|------|-----------|
| Mock A | `src/mocks/MockCatalogo.php` | Que el Módulo B (Carrito) pueda desarrollar sin el catálogo real |
| Mock B | `src/mocks/MockCarrito.php` | Que el Módulo D (Checkout) pueda desarrollar sin el carrito real |
| Mock C | `src/mocks/MockAuth.php` | Que todos los módulos puedan probar autenticación |
| Mock D | `src/mocks/MockCheckout.php` | Que el Módulo E (Pasarela) pueda desarrollar sin checkout real |
| Mock E | `src/mocks/MockTransbank.php` | Que el Módulo D pueda probar el flujo de pago sin Transbank real |
| Mock F | `src/mocks/MockInventario.php` | Que el Módulo A y D puedan verificar stock sin inventario real |

### Ejemplo de Mock

```php
// src/mocks/MockCatalogo.php
class MockCatalogo {
    public static function listarProductos($categoria = null, $buscar = null) {
        return [
            "productos" => [
                ["id" => 1, "nombre" => "Laptop Gamer", "precio" => 899990, "stock" => 10],
                ["id" => 2, "nombre" => "Mouse Inalámbrico", "precio" => 24990, "stock" => 50]
            ],
            "total" => 2
        ];
    }
}
```

---

## 5. Git Workflow

### Ramas
```
main                   # Integración final
├── modulo-a-catalogo  # Equipo Catálogo
├── modulo-b-carrito   # Equipo Carrito
├── modulo-c-auth      # Equipo Autenticación
├── modulo-d-checkout  # Equipo Checkout
├── modulo-e-pasarela  # Equipo Pasarela Transbank
├── modulo-f-inventario# Equipo Inventario
└── modulo-h-integracion # Equipo Orquestación (esta rama)
```

### Reglas
1. Cada equipo trabaja **exclusivamente** en su rama.
2. Solo el equipo H hace merge a `main`.
3. Cada PR debe incluir: (a) qué contrato implementa, (b) evidencia de que pasa el contrato.
4. No se aceptan PRs que modifiquen archivos fuera del directorio del módulo.
5. Los commits deben seguir el formato: `[MÓDULO-X] verbo: descripción` (ej: `[MÓDULO-A] feat: listar productos con filtros`).

---

## 6. Estructura de Archivos de H

```
src/
├── config/
│   ├── database.php        # Conexión PDO (única para todo el proyecto)
│   ├── transbank.php       # Configuración Transbank (llaves, URL)
│   └── app.php             # Config general (zona horaria, debug, etc.)
├── middleware/
│   └── auth.php            # Verificación de sesión y roles
├── mocks/
│   ├── MockCatalogo.php
│   ├── MockCarrito.php
│   ├── MockAuth.php
│   ├── MockCheckout.php
│   ├── MockTransbank.php
│   └── MockInventario.php
├── helpers/
│   ├── response.php        # Funciones para respuestas JSON
│   ├── validacion.php      # Validación de datos comunes
│   └── session.php         # Manejo de sesiones

docs/
├── api-contracts/
│   ├── modulo-a-catalogo.yaml
│   ├── modulo-b-carrito.yaml
│   ├── modulo-c-auth.yaml
│   ├── modulo-d-checkout.yaml
│   ├── modulo-e-pasarela.yaml
│   └── modulo-f-inventario.yaml
├── guia-integracion.md     # Guía para estudiantes sobre cómo integrar
└── checklist-integracion.md # Lista de verificación pre-merge

db/
├── schema.sql              # Esquema completo de BD
├── seed.sql                # Datos de prueba (productos, categorías)
└── migrations/
    └── 001-crear-tablas.sql

tests/
└── integracion/
    ├── test-flujo-completo.php
    └── test-contratos.php
```

---

## 7. Pruebas de Integración

### Flujo Completo (test obligatorio)

```php
// Pseudocódigo del test de integración
function testFlujoCompraExitosa() {
    // 1. Catálogo: obtener productos
    $productos = API::get('/api/productos/listar');
    assert(count($productos['productos']) > 0);

    // 2. Carrito: agregar producto
    $carrito = API::post('/api/carrito/agregar', ['producto_id' => 1, 'cantidad' => 1]);
    assert($carrito['exitoso']);

    // 3. Auth: login
    $auth = API::post('/api/auth/login', ['email' => 'test@test.cl', 'password' => '123456']);
    assert($auth['token']);

    // 4. Carrito: resumen
    $resumen = API::get('/api/carrito/resumen', ['token' => $auth['token']]);
    assert($resumen['total'] > 0);

    // 5. Checkout: iniciar pago
    $pago = API::post('/api/pago/iniciar', ['pedido_id' => 1, 'monto' => $resumen['total'], 'token' => $auth['token']]);
    assert($pago['url_webpay']);

    // 6. Pago: confirmar (mock)
    $confirmacion = API::post('/api/pago/confirmar', ['token_ws' => 'mock_token', 'token' => $auth['token']]);
    assert($confirmacion['exitoso']);

    // 7. Inventario: verificar descuento
    $inventario = API::get('/api/inventario/stock', ['producto_id' => 1]);
    assert($inventario['stock_actual'] < 10); // Stock disminuyó

    echo "✅ Flujo completo exitoso";
}
```

---

## 8. Criterios de Éxito

- [ ] Contratos API definidos y publicados antes del inicio del desarrollo
- [ ] Mocks de todos los módulos funcionales desde la semana 1
- [ ] Middleware de autenticación integrado y funcional en todos los módulos
- [ ] Schema BD único desplegado sin conflictos
- [ ] Todos los módulos integrados en `main` sin errores
- [ ] Prueba de flujo completo pasa sin errores
- [ ] Guía de integración publicada para los estudiantes

---

## 9. Checklist de Integración (para usar en cada PR)

```
[ ] El código sigue la estructura de carpetas definida
[ ] No modifica archivos fuera de su módulo
[ ] Implementa fielmente los contratos API definidos
[ ] Usa el middleware de autenticación del proyecto
[ ] Usa la conexión a BD unificada (src/config/database.php)
[ ] No tiene dependencias de otros módulos fuera de los contratos
[ ] El CSS usa las clases Bootstrap definidas (no estilos inline)
[ ] Los mensajes de error son en español, claros y descriptivos
[ ] No hay datos hardcodeados (API keys, URLs, passwords)
[ ] El código incluye comentarios en español (formato PHPDoc/docblock)
```
