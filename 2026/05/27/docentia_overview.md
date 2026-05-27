# Docentia — Overview para el Equipo War Room

**Por:** Newen 🚀 — Líder Docentia  
**Para:** Hermes, Antu, Kimche, Cristian  
**Fecha:** 2026-05-27

---

## ¿Qué es Docentia?

Docentia es una plataforma de IA aplicada a la educación superior. Su misión es **democratizar el acceso a la inteligencia artificial en la docencia universitaria**, proporcionando a los profesores un equipo de agentes especializados que asisten en todas las áreas de la labor docente.

El proyecto nace de Cristian Iglesias Vera, docente de la Universidad Católica de Temuco (UCT), y se alinea con la metodología **Discovery → Delivery** de Javier Garzas y **Spec-Driven Development** (github/spec-kit + obra/superpowers).

---

## Equipo de Agentes Docentia

| Agente | Especialidad | Skill principal |
|---|---|---|
| **Newen 🚀** | Líder / Orquestador | Coordinación, Google APIs, infraestructura |
| **Adkintun 👁️** | Diseño Curricular | `adkintun-curricular` — analizar programas, planificar |
| **Ayekan 🧠** | Psicología Educativa | `ayekan-psicologia` — NEE, inclusión, CERETI |
| **Kümeelkan ✅** | Evaluación | `kumeelkan-evaluacion` — rúbricas, feedback, notas |
| **Kintun 📊** | Administrativo | `kintun-administrativo` — listas, asistencia, actas |
| **Pewma 💬** | Apoyo Estudiantil | `pewma-apoyo` — atención 24/7 a estudiantes |
| **Wirin 🎨** | Contenidos | `wirin-contenidos` — guías, ejercicios, presentaciones |
| **Kallfü 📈** | Datos | `kallfu-analisis` — dashboards, tendencias, riesgo |

Todos los agentes comparten la skill `docentia-docs-access` para leer el repositorio de materiales.

---

## Repositorio Principal

🔗 **https://github.com/ciglesiasvera/docentia-docs**

```
docentia-docs/
├── curso/              ← Programa TINF1113, reglamentos, syllabus
├── contenidos/semanas/ ← Contenido por semana (semana_3 a semana_13)
├── seccion_1/          ← 18 estudiantes, rúbrica, ajustes razonables
├── seccion_2/          ← 17 estudiantes, rúbrica, ajustes CERETI
├── evaluaciones/       ← Notas, informes, replanificación
├── guias/              ← Guías de laboratorio
├── cereti/             ← Documentación CERETI
└── reglamentos/        ← Reglamentos UCT
```

---

## Curso Activo: TINF1113

**Desarrollo y Diseño Web + IA**  
**Carrera:** Técnico Universitario en Informática (2° año)  
**Estudiantes:** ~36 en 2 secciones  
**Horas:** 3 presenciales + 3 mixtas + 4 autónomas (semanal)

### Resultados de Aprendizaje

| RA | Descripción | Estado |
|---|---|---|
| **RA1** | Diseño web con HTML/CSS/JS | ✅ Cubierto (semanas 1-7) |
| **RA2** | Desarrollo PHP + MySQL + AJAX | 🔄 En curso (semanas 8-13) |
| **RA3** | IA aplicada + ética profesional | ⬜ Pendiente (semanas 14-15) |

---

## Metodología de Trabajo

### Spec-Driven Development (adaptado a docencia)

```
1. SPECIFY  → spec.md (QUÉ: problema, criterios de aceptación)
2. PLAN     → plan.md (CÓMO: stack, estructura, validación)
3. TASKS    → tasks.md (desglose atómico por agente)
4. IMPLEMENT → Agente especializado ejecuta
5. REVIEW   → Newen revisa contra spec
```

### Reglas de evaluación

- Solo evaluar lo que está EXPLÍCITAMENTE en la rúbrica
- Aplicar ajustes CERETI ANTES de evaluar
- Misma rúbrica para todos en una sección
- localStorage NO penaliza (no está en la rúbrica)
- Cada nota debe ser defendible con evidencia

---

## Tarea Actual: Semanas 12-15

**Contexto:** 5 sesiones restantes para cubrir RA2 (PHP+MySQL+jQuery) + RA3 (IA+Ética).  
**Debate activo:** `2026/05/27/debate_docentia_tinf1113.md`

**Reparto propuesto:**

| Agente | Responsabilidad |
|---|---|
| **Newen** | Slides (Google API) + coordinación |
| **Wirin** | Contenido didáctico por sesión |
| **Adkintun** | Alineación curricular (RA2/RA3) |
| **Hermes** | Revisión de calidad + spec |
| **Antu** | Actividades prácticas + evaluación |
| **Kimche** | Scripts PHP/MySQL de ejemplo |

---

*Docentia — Democratizando IA en educación superior. https://docentia.skylabs.cl*
