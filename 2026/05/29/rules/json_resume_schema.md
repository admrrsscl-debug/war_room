# JSON Resume Schema — Fuente única de datos para los 3 CVs

Este schema sigue el estándar [JSON Resume](https://jsonresume.org/schema) para mantener compatibilidad con generadores existentes.

## Estructura base

```json
{
  "$schema": "https://raw.githubusercontent.com/jsonresume/resume-schema/v1.0.0/schema.json",
  "basics": {
    "name": "Cristian Iglesias Vera",
    "label": "Python Backend Developer | AI Education Specialist | Tech Lead",
    "email": "ciglesiasvera@gmail.com",
    "phone": "(+56) 9 4110 2467",
    "location": {
      "address": "Temuco",
      "region": "Araucanía",
      "countryCode": "CL"
    },
    "profiles": [
      { "network": "GitHub", "url": "https://github.com/ciglesiasvera" },
      { "network": "LinkedIn", "url": "linkedin.com/in/cristian-iglesias-vera-23a067219/" }
    ]
  },
  "work": [
    {
      "name": "SkillNest (ex Coding Dojo)",
      "position": "Relator Titular Bootcamp Full Stack Python",
      "startDate": "2025-05",
      "endDate": "actualidad",
      "highlights": [
        "Formación intensiva en Python/Django a estudiantes de todo Chile"
      ]
    },
    {
      "name": "TEC UCT — Universidad Católica de Temuco",
      "position": "Docente Desarrollo Web + IA",
      "startDate": "2024-08",
      "endDate": "actualidad",
      "highlights": [
        "Docencia en Desarrollo y Diseño de Software, Desarrollo Web + IA, Desarrollo Móvil"
      ]
    },
    {
      "name": "CFT Estatal de la Araucanía",
      "position": "Docente | Relator",
      "startDate": "2024-04",
      "endDate": "2025-07",
      "highlights": [
        "Matemáticas, Liderazgo, Proyectos de Innovación, Marketing Digital"
      ]
    },
    {
      "name": "Skylabs SpA",
      "position": "Fundador | Líder de Equipo | Full Stack Developer",
      "startDate": "2016-01",
      "endDate": "actualidad",
      "highlights": [
        "20+ proyectos digitales para turismo, comercio y educación",
        "Coordinación de equipos multidisciplinarios con metodologías ágiles"
      ]
    },
    {
      "name": "CFT Teodoro Wickel — UFRO",
      "position": "Coordinador de Carrera TNS Informática",
      "startDate": "2018-02",
      "endDate": "2022-01",
      "highlights": [
        "100% matrícula y empleabilidad durante la gestión",
        "Implementación de Bootcamps UX/UI y Vue.js",
        "Convenios con NTT Data, Anaconda Web, Instituto Claret"
      ]
    }
  ],
  "education": [
    {
      "institution": "CFT Teodoro Wickel — UFRO",
      "area": "Producción de Software",
      "studyType": "Técnico de Nivel Superior",
      "startDate": "2014",
      "endDate": "2016"
    }
  ],
  "certificates": [
    { "name": "Desarrollador Full Stack Python (Django)", "issuer": "Talento Digital", "date": "2024-11" },
    { "name": "Introducción al Análisis de Datos con Python", "issuer": "Desafío Latam", "date": "2024-05" },
    { "name": "Web3 Certified Developer Azle — TypeScript", "issuer": "ICP Hub LATAM", "date": "2023-11" },
    { "name": "NEAR Certified Developer NCD — Rust + React", "issuer": "NEAR Hispano", "date": "2022-11" }
  ],
  "skills": [
    { "name": "Backend", "keywords": ["Python", "Django", "DRF", "FastAPI", "PHP", "Laravel", "Java", "Spring Boot"] },
    { "name": "Frontend", "keywords": ["HTML5", "CSS3", "JavaScript", "TypeScript", "React"] },
    { "name": "Bases de Datos", "keywords": ["PostgreSQL", "MySQL", "SQL"] },
    { "name": "DevOps", "keywords": ["Docker", "Git", "CI/CD", "Linux"] },
    { "name": "IA / Datos", "keywords": ["LLMs", "Agentes IA", "Automatización", "Pandas", "Prompt Engineering"] },
    { "name": "Herramientas", "keywords": ["VS Code", "IntelliJ", "GitHub", "Jira", "Figma", "Notion"] }
  ],
  "languages": [
    { "language": "Español", "fluency": "Nativo" },
    { "language": "Inglés", "fluency": "Intermedio" }
  ],
  "projects": [
    {
      "name": "Sistema Multi-Agente Docentia",
      "description": "Ecosistema de 4 agentes IA autónomos (Newen, Antu, Hermes, Kimche)",
      "highlights": ["Integración Telegram + Discord + Git", "Debate multi-agente vía War Room"],
      "url": "https://github.com/admrrsscl-debug/war_room"
    }
  ]
}
```

## Uso en el pipeline

1. Este JSON es la **fuente única de verdad** para los 3 CVs
2. Cada CV filtra/selecciona las secciones relevantes según el target
3. El pipeline de @Newen toma este JSON como input
4. Compatible con generadores JSON Resume existentes
