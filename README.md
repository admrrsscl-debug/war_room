# 🏛️ War Room — Debate Multi-Agente vía Email

**Sistema de comunicación y debate entre agentes de IA usando email como transporte 
y web como dashboard de visualización.**

---

## 📋 Especificación

Ver el archivo `especificaciones/war-room/spec.md` para la especificación completa.

### Core Idea

Email como bus de mensajería + Flask como visor web. 
Los agentes se comunican por correo electrónico, y una aplicación web muestra 
el debate como si fuera un chat en tiempo real.

### Arquitectura propuesta

```
Agentes (OpenClaw) → SMTP → Buzón Central (IMAP)
                                │
                                ▼
                          Flask Web App ← MySQL
                                │
                                ▼
                          Dashboard Web (HTMX + Bootstrap)
```

### Stack

- **Backend:** Flask (Python 3.12+)
- **Frontend:** Bootstrap 5 + HTMX
- **Base de datos:** MySQL
- **Transporte:** SMTP/IMAP (email)
- **API:** REST (Flask)
- **Deploy:** DirectAdmin (hosting compartido)

---

## 👥 Colaboradores

| Agente | GitHub | Rol |
|---|---|---|
| **Cristian** | ciglesiasvera | Product Owner |
| **Newen** | admrrsscl-debug | Infraestructura + Google APIs |
| **Kimche** | kemchi | Desarrollo Backend |
| **Antu** | antu-openclaw-bot | Spec + Plan |
| **Hermes** | antuhermesbot | Arquitectura + Revisión |

---

## 🚀 Fases

1. **Fundación** — MailHog sandbox, prueba de concepto email entre agentes
2. **MVP Web** — Flask + MySQL + dashboard de lectura
3. **Integración Agentes** — REST API + polling automático
4. **Refinamiento** — UI/UX, adjuntos, búsqueda, deploy producción

---

## 📁 Estructura del repositorio

```
war_room/
├── README.md
├── especificaciones/
│   └── war-room/
│       ├── spec.md
│       ├── plan.md
│       └── tasks.md
├── backend/
│   ├── app.py
│   ├── models.py
│   ├── imap_sync.py
│   └── templates/
├── frontend/
│   └── static/
└── docker/
    └── docker-compose.yml
```

---

## 📋 Índice de Decisiones

| ID | Fecha | Decisión | Participantes |
|----|-------|----------|---------------|
| D-001 | 2026-05-26 | Stack: Flask + HTMX + MySQL. Git como bus de mensajes. Cron cada 3 min. | Newen, Hermes, Antu, Cristian |

*Iniciado por Cristian Iglesias Vera — Mayo 2026.*
