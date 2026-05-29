# Reglas ATS para el CV de Cristian Iglesias

## Principios generales
1. **Una página máximo** para CV #1 y #2. CV #3 (Tech Lead) puede llegar a 2 páginas.
2. **Formato:** Markdown con frontmatter YAML → LaTeX → PDF (pipeline @Newen)
3. **Sin imágenes, tablas complejas, columnas múltiples** — los parsers ATS los ignoran
4. **Fuente:** Estándar (Times New Roman, Arial, Calibri) tamaño 10-12pt
5. **Márgenes:** 1 pulgada estándar

## Palabras clave obligatorias por versión

### CV #1 — Python Backend Developer
Python, Django, REST APIs, PostgreSQL, Docker, Git, CI/CD,
Microservicios, Testing, SQL, Linux, FastAPI, Flask, DRF

### CV #2 — Data Analyst / AI Applied
Python, Pandas, Análisis de Datos, IA, Machine Learning, LLMs,
Automatización, Visualización, Agentes IA, Prompt Engineering

### CV #3 — Tech Lead / EdTech AI
Liderazgo Técnico, Coordinación, Docencia IA, Bootcamp,
Innovación Curricular, Mentoría, Gestión de Equipos, EdTech

## Estructura ATS-friendly
```
[ENCABEZADO] Nombre | Email | Teléfono | LinkedIn | GitHub
[PERFIL] 3 líneas máximo con keywords upfront
[EXPERIENCIA] Formato: Puesto | Empresa | Fechas (bullet points de logros)
[HABILIDADES TÉCNICAS] Lista plana separada por pipes
[EDUCACIÓN] Título | Institución | Año
[CERTIFICACIONES] Solo las relevantes
```

## Lo que mata el score ATS
❌ PDF con imágenes incrustadas
❌ Tablas con formato complejo
❌ Columnas múltiples
❌ Encabezados y pies de página con información
❌ Fuentes no estándar
❌ Caracteres especiales no UTF-8
❌ Enlaces sin texto descriptivo
