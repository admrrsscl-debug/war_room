# PRES-001 — Presentaciones TINF1113 con Notebook LM + Google Slides

**Versión:** 1.0.0
**Autor:** Hermes 🏔️ (en representación del equipo War Room — Newen, Antu, Kimche, Hermes)
**Fecha:** 2026-05-27
**Estado:** BORRADOR
**Curso:** TINF1113 — Desarrollo y Diseño Web + IA (UCT)

---

## 1. ¿QUÉ y POR QUÉ?

### Problema

El curso TINF1113 requiere 5 presentaciones de calidad institucional para las semanas 12 a 15 (sesiones restantes del semestre). Cada presentación debe:

- Usar la **plantilla TECUCT institucional** (TECUCT 1 para sesiones impares, TECUCT 2 para sesiones pares).
- Contener **imágenes contextualizadas al contenido** de cada slide (0 Lorem Ipsum, 0 placeholders).
- Seguir el **formato probado de las semanas 4 a 11** (benchmark: semana 8).
- Incluir **código funcional, actividades prácticas y alineación con RA2/RA3**.
- Ser generada con un **flujo automatizado** que minimice el trabajo manual.

### Método validado por Cristian

Cristian validó el siguiente flujo como método principal para generar presentaciones:

1. **ChatGPT (o Wirin)** genera contenido estructurado de 12 diapositivas (título, cuerpo, subtítulos, imágenes sugeridas).
2. **Exportar a PDF** el contenido generado.
3. **Cargar el PDF en Notebook LM** con la instrucción: "Sigue rigurosamente el documento y genera 12 diapositivas."
4. **Notebook LM genera slides completas con imágenes contextualizadas** automáticamente.
5. **Extraer imágenes** de Notebook LM (manual o por script).
6. **Google Slides API** pega las imágenes en la plantilla TECUCT institucional.

### Flujo alternativo (automatizado)

Para sesiones donde el contenido ya existe (semanas 12 y 13, fuente teclab.uct.cl):

1. **Contenido desde teclab** (ya existe en docentia-docs/recursos/).
2. **Google Slides API** genera slides directamente con la plantilla TECUCT.
3. **Pollinations.ai** (integrado y probado) genera imágenes automatizadas si se requieren reemplazos.
4. **Revisión de calidad contra benchmark** (semana 8).

### Flujo completo

```
    ┌──────────────────────────────────────────────────────┐
    │               CONTENIDO EXISTENTE                     │
    │          (teclab.uct.cl / docentia-docs)              │
    │                    Semanas 12-13                      │
    └──────────┬───────────────────────────────────────────┘
               │
               ▼
    ┌──────────────────┐         ┌─────────────────────┐
    │  Google Slides   │         │  Pollinations.ai    │
    │  API + TECUCT    │◄────────│  (imágenes fallback) │
    │  Template        │         └─────────────────────┘
    └──────────┬───────┘
               │
               ▼
    ┌──────────────────────────────────────────────────────┐
    │               CONTENIDO NUEVO                         │
    │          (Semanas 14-15 — jQuery, IA, Ética)          │
    └──────────┬───────────────────────────────────────────┘
               │
               ▼
    ┌──────────────────┐         ┌─────────────────────┐
    │  ChatGPT / Wirin │         │  Notebook LM        │
    │  → Contenido     │────────►│  → Slides c/        │
    │  → PDF           │         │  imágenes generadas  │
    └──────────────────┘         └──────────┬──────────┘
                                            │
                                            ▼
                               ┌────────────────────────┐
                               │  Extraer imágenes      │
                               │  (manual o captura)    │
                               └──────────┬─────────────┘
                                          │
                                          ▼
                               ┌────────────────────────┐
                               │  Google Slides API     │
                               │  → Pegar en TECUCT     │
                               │  → Texto en shapes     │
                               └──────────┬─────────────┘
                                          │
                                          ▼
                               ┌────────────────────────┐
                               │  Revisión calidad      │
                               │  (Hermes)              │
                               └────────────────────────┘
```

---

## 2. Stack y Herramientas

| Herramienta | Propósito | Estado |
|-------------|-----------|--------|
| Google Slides API | Crear/modificar slides en plantilla TECUCT | ✅ Token OAuth activo |
| Notebook LM | Generar slides completas con imágenes contextualizadas | ✅ Método validado por Cristian |
| ChatGPT / Claude | Generar contenido estructurado → PDF | ✅ Disponible (Wirin) |
| Pollinations.ai | Generar imágenes automatizadas (fallback/alternativa) | ✅ Integración funcional, gratis, 4s por imagen |
| TECUCT 1 Template | Plantilla para sesiones impares (18 slides, fondo oscuro) | ✅ En Drive + docentia-docs |
| TECUCT 2 Template | Plantilla para sesiones pares (21 slides, fondo claro) | ✅ En Drive + docentia-docs |
| PlantillaPTT_TECUCT_1.pptx | Archivo PPTX fuente (sesiones impares) | ✅ En docentia-docs/recursos/ |
| PlantillaPTT_TECUCT_2.pptx | Archivo PPTX fuente (sesiones pares) | ✅ En docentia-docs/recursos/ |

---

## 3. Sesiones a generar

| Semana | Sesión | Contenido | Plantilla | Método | Responsable Slides | Responsable Contenido | Deadline |
|--------|--------|-----------|-----------|--------|-------------------|----------------------|----------|
| 12 | S1 | CRUD PHP + MySQL | TECUCT 1 (impar) | Google API + teclab | 🚀 Newen | ✅ Existe en teclab | ✅ Listo |
| 12 | S2 | CRUD PHP + MySQL (cont.) | TECUCT 2 (par) | Google API + teclab | 🚀 Newen | ✅ Existe en teclab | ✅ Listo |
| 13 | S1 | API REST PHP | TECUCT 1 (impar) | Google API + teclab | 🚀 Newen | ✅ Existe en teclab | HOY |
| 13 | S2 | API REST PHP (cont.) | TECUCT 2 (par) | Google API + teclab | 🚀 Newen | ✅ Existe en teclab | HOY |
| 14 | S1 | jQuery + AJAX | TECUCT 1 (impar) | ChatGPT/PDF → Notebook LM → Google API | 🚀 Newen | ☀️ Antu → ChatGPT → PDF | Jueves 28 (mañana) |
| 14 | S2 | IA Aplicada (RA3) | TECUCT 2 (par) | ChatGPT/PDF → Notebook LM → Google API | 🚀 Newen | ☀️ Antu → ChatGPT → PDF | Jueves 28 (tarde) |
| 15 | S1 | Ética + Cierre (RA3) | TECUCT 1 (impar) | ChatGPT/PDF → Notebook LM → Google API | 🚀 Newen | ☀️ Antu → ChatGPT → PDF | Viernes 29 |

---

## 4. Estándar de Calidad

### Checklist de revisión (basado en benchmark semana 8)

Cada presentación DEBE cumplir:

- [ ] **Plantilla TECUCT correcta** — TECUCT 1 para sesiones impares, TECUCT 2 para pares
- [ ] **12 slides máximo** (sin contar portada/cierre)
- [ ] **Imágenes contextuales** — al menos 1 imagen por slide principal (desde Notebook LM o Pollinations.ai)
- [ ] **Código funcional** con ejemplos verificables
- [ ] **Actividad práctica** con instrucciones claras (slides 11-12)
- [ ] **0 Lorem Ipsum, 0 placeholders, 0 errores de formato**
- [ ] **Alineación con RA2 o RA3** según corresponda
- [ ] **Alineación de textos verificada** dentro de las shapes de Google Slides
- [ ] **Contenido con significado** — conectado con la realidad del estudiante

### Criterios de rechazo

| Problema | Acción |
|----------|--------|
| Plantilla incorrecta | Reemplazar y regenerar |
| Más de 12 slides | Reducir a 12, fusionar contenido redundante |
| Imágenes faltantes o placeholder | Usar Pollinations.ai o Notebook LM para generar |
| Lorem Ipsum | Reemplazar inmediatamente |
| Texto desalineado en shapes | Ajustar posiciones en Google Slides API |

---

## 5. Distribución de trabajo

| Rol | Agente | Responsabilidades |
|-----|--------|-------------------|
| **Generación Slides** | 🚀 Newen | Ejecutar scripts Python con Google Slides API, crear/modificar slides con plantilla TECUCT, pegar imágenes |
| **Contenido (semanas 12-13)** | 🚀 Newen | Contenido ya existe en teclab.uct.cl, solo aplicar formateo |
| **Contenido (semanas 14-15)** | ☀️ Antu + 🧪 Kimche | Antu genera PDF estructurado (12 slides) vía ChatGPT. Kimche prepara código jQuery/AJAX funcional para integrar |
| **Código ejemplo** | 🧪 Kimche | Preparar y testear código funcional de jQuery + AJAX, API REST, y ejemplos de IA |
| **Revisión calidad** | 🏔️ Hermes | Verificar contra checklist, 0 Lorem Ipsum, alineación RA, formato correcto |
| **Imágenes alternativas** | 🚀 Newen | Pollinations.ai si Notebook LM no genera alguna imagen específica |
| **Aprobación final** | 🧑‍🏫 Cristian | Validar contenido y formato antes de usar en clases |

---

## 6. Contenido mínimo por sesión

### Semana 14 S1 — jQuery + AJAX

1. Selectores jQuery ($, clase, ID, atributo)
2. Eventos (click, submit, change, keyup)
3. AJAX con $.ajax() y $.get()/$.post()
4. Integración con PHP: formulario que envía sin recargar página
5. **Ejercicio:** Sistema de comentarios con jQuery AJAX + PHP backend

### Semana 14 S2 — IA Aplicada (RA3 intro)

1. ¿Qué es IA? Predictiva vs Generativa
2. Herramientas gratuitas: Claude AI, Perplexity, Gamma, Google Gemini
3. Caso práctico: usar Claude para generar código PHP/MySQL
4. Caso práctico: usar Perplexity para investigar buenas prácticas
5. **Ejercicio:** Usar una herramienta IA para mejorar el proyecto de portafolio

### Semana 15 S1 — Ética + Cierre (RA3)

1. Sesgo en IA: ejemplos reales (contratación, crédito, justicia)
2. Privacidad de datos: qué datos compartimos con las IAs
3. Propiedad intelectual: ¿de quién es el código generado por IA?
4. **Debate en clase:** ¿deberían las IAs tener límites legales?
5. Cierre: integración de todo lo aprendido, preparación para examen

---

## 7. Dependencias y prerrequisitos

| Dependencia | ¿Resuelta? | Notas |
|-------------|-----------|-------|
| Token OAuth Google Slides API | ✅ Sí | Cuenta adm.rrss.cl@gmail.com |
| Plantillas TECUCT en Drive | ✅ Sí | TECUCT 1 (impar), TECUCT 2 (par) |
| Scripts Python Google Slides | ✅ Sí | Probados en sesiones previas |
| Pollinations.ai | ✅ Sí | Integración funcional, gratis, sin API key |
| Contenido teclab (semanas 12-13) | ✅ Sí | En docentia-docs |
| Contenido nuevo (semanas 14-15) | ❌ Por crear | Antu genera PDF, Kimche código jQuery |
| Notebook LM | ✅ Sí | Acceso disponible para Cristian y Newen |

---

## 8. Criterios de éxito

| Criterio | Medición |
|----------|----------|
| Presentaciones generadas | 7 presentaciones (semanas 12-15, 5 sesiones) |
| Calidad de imágenes | 0 placeholders, 0 Lorem Ipsum, imágenes contextuales por slide |
| Formato TECUCT | Plantilla correcta para cada sesión (par/impar) |
| Código funcional | Cada snippet verificado por Kimche antes de incluir |
| Deadline | Viernes 29 de mayo — todas las presentaciones listas |
| Aprobación de Cristian | Validación final antes de usar en clases |

---

## 9. Pendientes de decisión

| Ítem | Estado | Pendiente de |
|------|--------|--------------|
| Flujo Notebook LM como método principal | ✅ Aprobado por Cristian | — |
| Extracción de imágenes de Notebook LM | ⚠️ En discusión | ¿Captura manual o script automatizado? Discutir con Newen |
| Pollinations.ai como fallback | ✅ Aprobado | — |
| Stack para código de ejemplo | ✅ PHP 8 + Bootstrap 5.3 | Stack del curso TINF1113 |
| Distribución de trabajo entre agentes | ✅ Acordado | Ver sección 5 |

---

## 10. Historial de versiones

| Versión | Fecha | Cambios | Autor |
|---------|-------|---------|-------|
| 1.0.0 | 2026-05-27 | Creación inicial con flujo Notebook LM + Google Slides API | 🏔️ Hermes |

---

*Especificación generada siguiendo la metodología Docentia: Discovery → Delivery con Spec-Driven Development. Basada en debate del War Room (2026-05-27), instrucciones de Cristian y análisis técnico de Newen, Antu, Hermes y Kimche.*
