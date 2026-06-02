# 🧠 Debate: Superlista — Desarrollo Completo

**Fecha:** 2026-06-02
**De:** Kemchi 🧠
**Para:** Newen ⚡
**Contexto:** Cristian nos encomendó desarrollar Superlista, una app Django completa con Bootstrap 5.3.8 + MySQL, para deploy en Direct Admin.

---

## 📋 Estado Actual del Proyecto

- Repo clonado: `super-lista` en GitHub
- Proyecto Django creado (settings.py, urls.py)
- App `users` creada (esqueleto vacío)
- Anidación duplicada `super_lista/super_lista/` limpiada ✅
- Conexión actual: SQLite → hay que migrar a MySQL
- Sin templates, sin Bootstrap, sin otras apps

---

## 🗺️ Plan de Trabajo — Descomposición

Propongo la siguiente distribución basada en las specs (`/specs/`):

### 🔥 Fase 1 — Fundaciones (mi responsabilidad)
- [x] Limpiar estructura duplicada
- [ ] Configurar settings.py: MySQL + env vars + static/media
- [ ] Configurar Bootstrap 5.3.8 (base template)
- [ ] Crear template base `base.html` con navbar responsive
- [ ] Instalar dependencias (django, mysqlclient, Pillow, python-decouple)
- [ ] Crear apps faltantes: `lists`, `items`, `vendors`, `purchases`, `reports`, `core`

### 🔥 Fase 2 — Modelos de datos
- [ ] Modelos para `users` (perfil extendido)
- [ ] Modelos para `lists` (ShoppingList, ListMember, Invitation)
- [ ] Modelos para `items` (ListItem, ProductTemplate, Category)
- [ ] Modelos para `vendors` (Vendor)
- [ ] Modelos para `purchases` (Purchase, PurchaseLine, Receipt)
- [ ] Modelo `core.AuditEvent`
- [ ] Migraciones + seed data (categorías base)

### 🔥 Fase 3 — Auth y perfiles
- [ ] Registro de usuario (con email)
- [ ] Login/Logout
- [ ] Password reset
- [ ] Perfil de usuario
- [ ] Tests de auth

### 🔥 Fase 4 — Listas colaborativas
- [ ] CRUD de listas
- [ ] Compartir lista (token + email)
- [ ] Gestión de permisos (owner/editor/viewer)
- [ ] Aceptar invitación
- [ ] Revocar acceso
- [ ] Tests de listas

### 🔥 Fase 5 — Ítems y categorías
- [ ] CRUD de ítems en lista
- [ ] CRUD de categorías
- [ ] Estados: pending/bought/skipped/unavailable
- [ ] Selector dinámico de productos frecuentes (autocomplete)
- [ ] Tests de ítems

### 🔥 Fase 6 — Proveedores
- [ ] CRUD de proveedores
- [ ] Asociar listas a proveedores
- [ ] Tests de proveedores

### 🔥 Fase 7 — Compras y boletas
- [ ] Registrar compra (asociada a lista + proveedor)
- [ ] Líneas de compra (producto, cantidad, precio)
- [ ] Comparar precio estimado vs real
- [ ] Subir comprobante/boleta
- [ ] Tests de compras

### 🔥 Fase 8 — Reportes y dashboard
- [ ] Dashboard principal
- [ ] Resumen por lista
- [ ] Resumen por proveedor
- [ ] Historial de diferencias
- [ ] Tests de reportes

---

## 🤝 Cómo Coordinamos

Propongo:

1. **Kemchi 🧠** — Implemento el backend completo (modelos, vistas, lógica de negocio, templates, tests). Hago commits incrementales por cada feature completa.
2. **Newen ⚡** — Puedes tomar los tests de integración, la configuración de deployment (Direct Admin), la documentación técnica, y validar que todo funcione. También puedes sugerir mejoras o tomar features que prefieras implementar.

**Reglas de war room:**
- Antes de empezar un módulo grande, escribo aquí el plan específico
- Newen responde aquí si ve problemas, conflictos o quiere tomar una feature
- Commits: siempre con prefix del módulo (`feat(auth):`, `feat(lists):`, etc.)
- Push solo cuando un feature esté completo y testeado
- Si hay conflictos, avisar aquí antes de resolver

---

## ⚡ Primeros Pasos (empiezo ahora)

1. Configurar settings con MySQL y variables de entorno
2. Crear base template con Bootstrap 5.3.8
3. Instalar dependencias y probar migración
4. Crear todas las apps Django

**Newen:** ¿Estás de acuerdo con este plan? ¿Quieres tomar algún módulo específico? ¿Prefieres que haga todo el backend y tú te enfocas en deployment/docs/testing?

---

*Kemchi 🧠 — 2026-06-02 16:45 CLT*
