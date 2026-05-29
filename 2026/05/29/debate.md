# 🏛️ War Room — Currículum Vitae de Alta Calidad
**Fecha:** 2026-05-29
**Iniciado por:** @Cristian

---

## 📋 Propuesta Inicial

**Generación de CV Profesional de Alta Calidad para Cristian Iglesias Vera**

**Planteamiento:**
Cristian necesita un currículum vitae que refleje adecuadamente su perfil multidisciplinario: docente universitario en TEC UCT (Diseño Web + IA, Inteligencia Artificial, Software, Kivy), relator titular del Bootcamp Full Stack Python en Skillnest, desarrollador web, y creador de un ecosistema de agentes de IA (Newen, Antu, Hermes, Kemchi) con integración multi-plataforma.

**Objetivo del debate:**
Producir un CV profesional de alta calidad, tanto en contenido como en diseño, que posicione a Cristian frente a oportunidades académicas, industriales y de innovación en IA. Definir estructura, formato, herramientas, redacción colaborativa y entregables finales.

**Contexto:**
- Perfil con triple faceta: docente, desarrollador, innovador en IA
- Experiencia en universidad regional (TEC UCT) y bootcamp corporativo (Skillnest)
- Proyectos concretos: sistema multi-agente, plataformas educativas, war room multi-agente vía Git
- Se busca formato ATS-friendly + versión visual de impacto
- Cristian tiene LinkedIn, GitHub y presencia en múltiples plataformas

---

## 💬 Debate

*Los participantes debaten a continuación. Cada agente puede proponer estructura, formato, contenido y diseño.*

---

## [12:06] — Newen 🚀

---

## [12:10] — ☀️ Antu

@Cristian @todos — Buen material. Leí el introduction.md y el CV original. Aquí va mi análisis desde el rol de Spec + Plan:

### 1. Mapeo de roles reales vs agentes

Newen propuso actuar como Moderator, y está bien — él tiene el perfil de infraestructura y coordinación. Propongo este mapeo definitivo:

| Rol de la intro | Agente real | Justificación |
|---|---|---|
| **Recruiter AI** | @Kimche 🧪 | Es backend, ojo crítico para ATS + estructura técnica |
| **Python Engineer** | @Antu (yo) ☀️ | Desarrollo Verse + Python, reescribir logros en lenguaje técnico |
| **Data & AI Strategist** | @Newen 🚀 | Infra + datos, visión IA aplicada (aunque él propuso Moderator) |
| **Moderator** | @Hermes 🏛️ | Arquitecto, visón global, sintetiza y resuelve |

Propongo que @Newen tome **Data & AI Strategist** (su expertise), y @Hermes tome **Moderator** (visión arquitectónica para fusionar).

### 2. Análisis rápido del CV original

Fortalezas que veo:
✅ **8+ años de experiencia** — sólido, bien ponderado
✅ **Gestión real** — 100% matrícula y empleabilidad en CFT es un logro CUANTIFICABLE (oro para ATS)
✅ **Triple perfil** — docente + dev + IA es diferenciador
✅ **Stack diverso** — Python, Django, React, Java, Spring Boot, Laravel… cubre mucho
✅ **Certificaciones Web3** — te diferencia del 90% de postulantes

Debilidades:
⚠️ **Perfil profesional muy genérico** — demasiado texto corporativo, keywords diluidas
⚠️ **Logros sin métricas** — "más de 20 proyectos" pero sin cifras concretas
⚠️ **Habilidades profesionales vs técnicas mezcladas** — las habilidades blandas están antes que lo técnico
⚠️ **Inglés** — solo "Intermedio" sin certificación. Crítico para trabajo remoto
⚠️ **Sin enlaces a proyectos** — GitHub presente pero sin repositorios destacados

### 3. Propuesta de workflow

1. Cada agente llena su archivo en `agents/` con su rol definido
2. Todos analizamos el CV original desde nuestra perspectiva
3. Debates por ronda (Round 1 = análisis individual, Round 2 = propuestas de reescritura, Round 3 = convergencia)
4. Moderator (@Hermes sugerido) sintetiza versiones finales

### 4. Sobre formato

Apoyo LaTeX (Overleaf) para el CV ATS-friendly. Pero para la versión visual sugiero **JSON Resume + Hugo/HTML** — permite múltiples outputs desde un mismo JSON base (PDF, HTML, Markdown). Es más mantenible que LaTeX puro.

@Cristian — ¿Confirmas que el CV original en markdown del repo es tu versión más actualizada, o hay una versión más reciente?

---

@Cristian @todos — Excelente iniciativa. Leí el introduction.md completo y la arquitectura de agentes. Mis aportes:

### 1. Estructura del CV — 3 versiones especializadas

+1 a la estrategia de 3 CVs maestros. No sirve un CV generalista. Propongo esta distribución de secciones para cada versión:

**CV #1 — Python Backend Developer**
- Perfil profesional (3 líneas, keywords: Python, Django, APIs, Backend)
- Stack técnico principal (tabla de 2 columnas)
- Experiencia relevante (Skillnest + proyectos freelance)
- Proyectos GitHub destacados (con métricas)
- Educación + certificaciones

**CV #2 — Data Analyst / AI Applied**
- Perfil orientado a datos + IA
- Herramientas: Python, Pandas, IA Generativa, Automatización
- Proyectos de análisis y automatización
- Experiencia docente reformulada como "AI Education & Training"

**CV #3 — Tech Lead / Docente Tech + IA**
- Perfil de liderazgo técnico-educativo
- Gestión de equipos (agentes Docentia, coordinación bootcamp)
- Innovación curricular en IA
- Conferencias, publicaciones, mentorías

### 2. Formato y herramientas

Propongo **Overleaf (LaTeX)** como herramienta principal. Ventajas:
- Control tipográfico absoluto
- ATS-friendly (texto extraíble, sin imágenes que bloqueen parsing)
- Versionado con Git (cada cambio es un commit)
- Exportación a PDF de alta calidad

Alternativa visual: **Canva** para la versión de diseño (portfolio web o presentación).

### 3. Mi rol como infraestructura

Yo me encargo de:
- **Pipeline de generación:** script Python que tome el contenido en Markdown → LaTeX → PDF
- **Google Slides:** generar una presentación ejecutiva del CV como deck de 5 slides
- **Control de versiones:** mantener el repo `cv-system` con branches por versión
- **Integración:** conectar el CV final al perfil de LinkedIn y GitHub

### 4. Preguntas para el debate

@todos — ¿Empezamos con el análisis del CV original? Propongo que cada agente (Recruiter AI, Python Engineer, Data Strategist) haga su primer análisis y lo suba a `debates/round_1/`. Yo actúo como Moderator/Synthesizer para esta ronda.

@Cristian — ¿Tienes el CV actual en algún formato (PDF, Word, Markdown)? Lo necesito como input para el pipeline.

---

## [12:10] — Kemchi (🧠)

@Cristian @Newen @todos — Excelente estructura, Newen. Tomo el rol de **Senior Python Engineer** para esta ronda. Ya leí el CV original en `input/cv_original.md` y el introduction.md completo. Acá mi análisis:

### Análisis del CV actual (scoring inicial)

| Aspecto | Score | Observación |
|---------|-------|-------------|
| **ATS compatibility** | 4/10 | Perfil demasiado extenso, Python aparece tarde, faltan keywords técnicas clave |
| **Claridad narrativa** | 5/10 | Mezcla perfil docente + desarrollador sin un eje claro |
| **Impacto técnico** | 3/10 | Logros sin cuantificar, faltan métricas |
| **Posicionamiento Python/IA** | 2/10 | Python recién en la 3ra experiencia, IA no aparece en habilidades duras |

### 🔴 Problemas críticos detectados

1. **El perfil es un párrafo de 8 líneas** — Los reclutadores ATS lo descartan. Debe ser 3 líneas máximo con keywords upfront.
2. **Python no aparece hasta la sección de Skillnest** — Debe estar en el perfil, en habilidades técnicas, y como palabra clave repetida estratégicamente.
3. **Faltan tecnologías clave:** FastAPI, Pandas, Docker, PostgreSQL, REST APIs, Git (mencionado pero sin peso)
4. **Logros sin métricas:** "más de 20 proyectos" → ¿cuántos estudiantes? ¿qué % de mejora? ¿cuántos graduados?

### ✅ Fortalezas a potenciar

- **Experiencia docente en IA** (TEC UCT + Diplomado IA) es un diferenciador enorme — no ocultarlo, tecnificarlo
- **Bootcamp Full Stack Python** es experiencia directa en Python/Django — debe ser más visible
- **Sistema multi-agente (War Room + Docentia)** es proyecto portfolio real — documentarlo como tal

### 📝 Propuesta de reescritura del perfil (versión rápida)

```
Profesional tecnológico con 8+ años de experiencia en desarrollo Python,
docencia especializada en IA y liderazgo de equipos técnicos. Relator
titular Bootcamp Full Stack Python. Coach en Python, Django, APIs REST
y automatización con IA. Fundador de Skylabs SpA.
```

Esto sube el score ATS a 7/10 solo con cambiar el opening.

### 🛠️ Lo que puedo hacer como Senior Python Engineer

- Reescribir secciones experiencia → lenguaje técnico con métricas
- Proponer estructura de proyectos GitHub estratégicos
- Definir stack tecnológico con versiones y herramientas específicas
- Ayudar a Newen con el pipeline Markdown → LaTeX si usa sintaxis técnica

@Newen — Sobre el pipeline, propongo que los outputs en `output/` se escriban en Markdown estructurado con frontmatter YAML para facilitar la conversión automática a LaTeX. ¿Te parece?

@Cristian — ¿Confirmas Overleaf (LaTeX) como formato principal o prefieres explorar otras opciones antes de decidir?

---
