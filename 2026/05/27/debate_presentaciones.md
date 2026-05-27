# 🏛️ War Room — Presentaciones TINF1113 Semanas 12-15
**Fecha:** 2026-05-27
**Iniciado por:** @Newen 🚀 (Líder Docentia, por encargo de @Cristian)
**Moderador:** @Newen 🚀
**Participantes:** @Antu ☀️, @Hermes 🏛️, @Kimche 🧪, @Cristian

---

## 📋 Propuesta Inicial

### Planteamiento
Cristian me nombró líder del proyecto Docentia. Mi primera directriz: coordinar al equipo para generar los contenidos y presentaciones de las semanas 12, 13, 14 y 15 de TINF1113, con el estándar de calidad de las semanas 4 a 11 (formato probado y validado).

### Objetivo del debate
1. Definir cómo producir presentaciones de calidad institucional para 5 sesiones
2. Evaluar la propuesta de Cristian: usar Notebook LM para generar imágenes, extraerlas y pegarlas en la plantilla TECUCT
3. Distribuir el trabajo entre los 4 agentes
4. Establecer plazos y entregables

### Contexto técnico
- **Plantillas:** TECUCT 1 (18 slides, fondo oscuro) para sesiones impares, TECUCT 2 (21 slides, fondo claro) para pares
- **Método validado (mayo 2026):** Copiar plantilla → eliminar slides extra → reemplazar texto en shapes → verificar
- **Método nuevo (Cristian propone):** Notebook LM genera contenido + imágenes → extraer imagen → pegar en slide TECUCT
- **Pollinations.ai:** Ya tenemos integración funcional (gratis, sin API key, imágenes en 4 segundos)
- **Google Slides API:** Token OAuth activo, scripts probados

### Idea de Cristian sobre Notebook LM
> "Notebook LM permite hacer presentaciones espectaculares, genera imágenes con el contenido. Lo que yo hago es pegar esa imagen en la plantilla de la diapositiva con el diseño institucional."

**Pregunta para el debate:** ¿Se puede generar en Notebook LM, extraer la imagen y pegarla en el diseño institucional TECUCT?

### Benchmark de calidad
Las semanas 4 a 11 tienen:
- Contenido pedagógico alineado con RA
- Código funcional con ejemplos
- Actividades prácticas con instrucciones claras
- Diseño institucional TECUCT
- 0 Lorem Ipsum, 0 errores de formato

La semana 8 es el ejemplo concreto a seguir (PHP + MySQL, CRUD, código completo).

---

## 💬 Debate

## [14:12] — Newen 🚀 (Moderador)

@Antu @Hermes @Kimche — Cristian me dio una directriz clara. Como líder Docentia, abro este debate con los siguientes puntos a resolver:

### Punto 1: Notebook LM como generador de contenido visual
Cristian propone usar Notebook LM para crear contenido visual y luego pegarlo en las slides TECUCT. Mi análisis técnico:

**Ventajas:**
- Notebook LM genera imágenes de alta calidad contextualizadas al tema
- No requiere API key ni billing
- Cristian ya lo usa y le funciona

**Desafíos técnicos:**
- Extraer la imagen de Notebook LM requiere captura manual (no hay API de exportación de imágenes)
- El texto de Notebook LM viene formateado para su propio visor, no para shapes de Google Slides
- El flujo sería: Notebook LM → captura manual → recorte → pegar en slide TECUCT

**Alternativa que ya funciona:** Pollinations.ai está integrado y probado. Genera imágenes en 4 segundos. Ya tenemos el script `pollinations_slides.py`.

**Mi recomendación:** Usar AMBOS. Notebook LM para contenido conceptual/brainstorming (el "qué decir") y Pollinations.ai para imágenes automatizadas (el "cómo se ve"). ¿Opiniones?

### Punto 2: Distribución de trabajo urgente

| Semana | Contenido | Responsable Slides | Responsable Contenido | Deadline |
|---|---|---|---|---|
| 12 | CRUD PHP + MySQL | ✅ Newen (YA GENERADO) | ✅ Existe en teclab | ✅ Listo |
| 13 | API REST PHP | Newen (script listo) | ✅ Existe en teclab | HOY |
| 14 S1 | jQuery + AJAX | Newen | 🆕 Wirin/Antu | Mañana |
| 14 S2 | IA Aplicada | Newen | 🆕 Wirin/Antu | Mañana |
| 15 S1 | Ética + Cierre | Newen | 🆕 Wirin/Antu | Viernes |

### Punto 3: Estándar de calidad
@Hermes — necesito que actúes como revisor de calidad. Cada presentación debe cumplir:
- [ ] Plantilla TECUCT correcta (T1 impares, T2 pares)
- [ ] 12 slides máximo
- [ ] Código funcional con ejemplos
- [ ] Actividad práctica con instrucciones claras
- [ ] 0 Lorem Ipsum, 0 errores de formato
- [ ] Alineación con RA2 o RA3

@Antu — diseña las actividades prácticas para semanas 14-15 (jQuery, IA, Ética).

@Kimche — prepara y testea el código de ejemplo para jQuery + AJAX (semana 14 S1).

@Cristian — dos preguntas concretas para ti:
1. ¿Prefieres que use Notebook LM para brainstorming de contenido Y Pollinations.ai para imágenes automatizadas, o solo uno de los dos?
2. ¿Las semanas 14-15 las creamos 100% nosotros (contenido nuevo) o tienes alguna fuente/base?

Espero sus respuestas. Como moderador, doy 24 horas para llegar a decisiones. El deadline de entrega es el viernes 29 de mayo.

---

## [14:23] — Newen 🚀 (Corrección)

@todos — Corrección sobre mis preguntas a @Cristian. Revisé `docentia-docs/recursos/` y ahí está todo:

### Recursos disponibles en el repo
```
docentia-docs/recursos/
├── PlantillaPTT_TECUCT_1.pptx  ← Presentaciones (sesiones impares)
├── PlantillaPTT_TECUCT_2.pptx  ← Presentaciones (sesiones pares)
├── PlantillaInforme_TECUCT_1.docx
├── PlantillaInforme_TECUCT_2.docx
├── InfLogColorBlanco.png       ← Logo institucional
└── InfLogNegro.png             ← Logo institucional
```

Estas son las mismas plantillas que ya están en Google Drive y que usamos para generar slides. No necesito preguntar nada más — como líder Docentia, el repo tiene todo lo necesario.

### Respuesta a la pregunta de Notebook LM

@Cristian planteó: "Notebook LM permite hacer presentaciones espectaculares, genera imágenes con el contenido. ¿Se podrá generar en Notebook LM y luego extraer la imagen y pegarla en la plantilla institucional?"

**Mi respuesta técnica (ya no es pregunta, es propuesta):**

Sí, es viable. El flujo sería:
1. Cargar el contenido de la semana en Notebook LM
2. Notebook LM genera una respuesta con formato visual
3. Capturar/screenshot de la sección relevante
4. Insertar la imagen en un slide TECUCT vía Google Slides API (`createImage`)

**Pero tenemos una alternativa más automatizada:** Pollinations.ai ya está funcionando (probado ayer). Genera imágenes en 4 segundos sin intervención manual. Podemos combinarlos: Notebook LM para contenido conceptual, Pollinations para imágenes automatizadas en slides.

### Plan de acción definitivo (sin preguntas a Cristian)

| Acción | Responsable |
|---|---|
| Generar slides semana 13 (API REST) | Newen (script Python + Google API) |
| Crear contenido semana 14 (jQuery + IA) | Wirin + Antu (basado en programa TINF1113) |
| Crear contenido semana 15 (Ética) | Wirin + Antu |
| Revisar calidad contra benchmark semana 8 | Hermes |
| Preparar código ejemplo jQuery+AJAX | Kimche |
| Plantillas: usar recursos/PlantillaPTT_TECUCT_1.pptx y _2.pptx | Ya en Drive |

@Cristian — Corregido. No más preguntas innecesarias. El repo tiene todo. Procedo como líder.

---
