# DECISION-001 — Arquitectura del War Room

| Campo | Valor |
|-------|-------|
| **ID** | D-001 |
| **Fecha** | 2026-05-26 |
| **Participantes** | Newen 🚀, Hermes 🏛️, Antu ☀️, Cristian |
| **Estado** | Aprobada ✅ |

## Decisión

Se define la arquitectura base del War Room y del ecommerce académico con el siguiente stack:

| Componente | Elección | Justificación |
|------------|----------|---------------|
| Backend | **Flask** + HTMX | Más liviano que Django para MVP. Deploy más rápido en DirectAdmin. |
| Base de datos | **SQLite** (desarrollo) / **MySQL** (producción) | SQLite para prototipado local, MySQL para escalabilidad en producción. |
| Bus de mensajes | **Git como fuente de verdad** | Cada commit = un mensaje. Cada merge = un consenso. Sin dependencias externas. |
| Comunicación en tiempo real | **Polling cada 10-15s** (luego WebSocket si necesario) | Sin WebSockets en MVP. Mantenerlo simple. |
| Visor web | **Flask + HTMX** sobre el repositorio Git | Interfaz web como capa de presentación sobre el bus de eventos textual. |

## Convenciones acordadas

1. **Numeración de documentos:** `DECISION-001.md`, `DECISION-002.md`, etc., por día junto al debate correspondiente.
2. **Índice rápido en README del repo** con tabla de decisiones (ID, Fecha, Decisión, Participantes).
3. **Cron de monitoreo:** Cada 3 minutos (180s).
4. **Comandos de control:** `/stop war room` detiene cron; `/start war room` lo reactiva.

## Implicaciones

- La web app se construye como interfaz sobre Git, no como reemplazo.
- Especs de módulos ecommerce siguen formato Docentia: spec.md → plan.md → tasks.md.
- Cada equipo recibe API contracts antes de escribir código.
