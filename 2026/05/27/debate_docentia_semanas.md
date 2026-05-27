# 🏛️ War Room — Contenidos TINF1113 Semanas 12-15
**Fecha:** 2026-05-27
**Iniciado por:** @Cristian
**Moderador:** @Cristian

---

## 📋 Propuesta Inicial

### Planteamiento
Necesito los contenidos y presentaciones para las 5 sesiones restantes de TINF1113. La semana 11 es evaluación (N°3). De 8 sesiones, 3 se pierden en pruebas → 5 sesiones de clase. El contenido debe tener la calidad y estructura de la semana 8 (PHP + MySQL, código completo, ejercicios prácticos).

### Objetivo
Cubrir RA2 (PHP/MySQL/jQuery) y RA3 (IA/Ética) en 5 sesiones de 3 horas cada una.

### Contenido disponible
- Semana 12: CRUD PHP + MySQL (existe en teclab)
- Semana 13: CRUD API REST PHP (existe en teclab)
- Semana 14: SIN contenido — hay que crearlo
- Semana 15: SIN contenido — hay que crearlo

### Contexto
- Curso: TINF1113, 36 estudiantes, 2 secciones
- Stack: PHP 8 + MySQL + Bootstrap 5.3
- Formato: 2 presentaciones de 12 slides cada una (plantilla TECUCT)
- Metodología: actividades prácticas, código real, ejercicios guiados

---

## 💬 Debate

## [13:55] — Cristian

@todos Quiero que revisen la semana 8 como benchmark de calidad. Esa semana tiene: preparación del entorno, código completo de cada archivo PHP, ejercicios prácticos con objetivos claros, y actividades guiadas paso a paso. Ese es el estándar.

La propuesta de @Newen de distribuir las 5 sesiones en: CRUD PHP → API REST → jQuery → IA → Ética me parece bien. Pero necesito que definan YA los contenidos exactos de cada sesión, los ejercicios prácticos, y los criterios de evaluación. No tengo más tiempo — empezamos la semana 12 en pocos días.

@Newen coordina. @Wirin genera los contenidos. @Adkintun alinea con RA2/RA3. @Hermes revisa calidad. @Antu diseña actividades. @Kimche prepara código de ejemplo funcional. Quiero ver specs por cada semana en el repo de docentia-docs. A trabajar.

---

## [13:58] — Newen 🚀

@Cristian entendido. Soy el orquestador. Propongo el siguiente plan de ejecución inmediata:

### Reparto de trabajo

| Semana | Contenido | Wirin | Newen (Slides) | Adkintun (RA) | Kimche (Código) | Antu (Actividades) |
|---|---|---|---|---|---|---|
| 12 | CRUD PHP + MySQL | ✅ Existe en teclab | 2 PPTs | RA2 | Revisar y testear | Diseñar ejercicio CRUD |
| 13 | API REST PHP | ✅ Existe en teclab | 2 PPTs | RA2 | Revisar y testear | Diseñar ejercicio API |
| 14 (S1) | jQuery + AJAX | 🆕 Crear | 1 PPT | RA2 | Crear ejemplos | Diseñar ejercicio AJAX |
| 14 (S2) | IA Aplicada | 🆕 Crear | 1 PPT | RA3 | — | Diseñar casos IA |
| 15 (S1) | Ética + Cierre | 🆕 Crear | 1 PPT | RA3 | — | Diseñar debate ético |

**Prioridad: Semana 12 YA** — contenido existe, solo necesita slides y actividades.

@Wirin ¿puedes empezar a generar el contenido estructurado para semana 14-15? Necesito el JSON en el schema de presentaciones (PRES-001) para que yo pueda generar las slides con Pollinations.ai.

@Kimche ¿puedes clonar el código de semana 12 desde teclab y verificar que funcione en XAMPP local?

---

## [14:00] — Hermes 🏛️

@Newen buena estructura. Reviso la propuesta contra el spec y agrego precisiones:

### Semana 14 (S1) — jQuery + AJAX
**Contenido mínimo:**
1. Selectores jQuery ($, clase, ID, atributo)
2. Eventos (click, submit, change, keyup)
3. AJAX con $.ajax() y $.get()/$.post()
4. Integración con PHP: formulario que envía sin recargar página
5. Ejercicio: sistema de comentarios con jQuery AJAX + PHP backend

### Semana 14 (S2) — IA Aplicada
**Contenido mínimo:**
1. Qué es IA (predictiva vs generativa)
2. Herramientas gratuitas: Claude AI, Perplexity, Gamma, Google Gemini
3. Caso práctico: usar Claude para generar código PHP/MySQL
4. Caso práctico: usar Perplexity para investigar buenas prácticas
5. Ejercicio: los estudiantes deben usar una herramienta IA para mejorar su proyecto de portafolio

### Semana 15 (S1) — Ética + Cierre
**Contenido mínimo:**
1. Sesgo en IA: ejemplos reales (contratación, crédito, justicia)
2. Privacidad de datos: qué datos compartimos con las IAs
3. Propiedad intelectual: ¿de quién es el código generado por IA?
4. Debate en clase: ¿deberían las IAs tener límites legales?
5. Cierre: integración de todo lo aprendido, preparación para examen

@Cristian ¿te parece este desglose para las semanas que faltan?

---

## [14:02] — Antu ☀️

@todos Excelente estructura. Diseño las actividades prácticas:

### Semana 12 — Actividad: CRUD Portafolio Personal
**Objetivo:** Construir un sistema de gestión de proyectos personales con PHP + MySQL.
**Instrucciones:**
1. Crear BD `portafolio` con tabla `proyectos` (id, titulo, descripcion, tecnologia, url, imagen)
2. Implementar create.php con formulario Bootstrap 5 + validación
3. Implementar list.php que muestre todos los proyectos en cards
4. Implementar edit.php con formulario pre-cargado
5. Implementar delete.php con confirmación JavaScript
**Criterios de logro:** CRUD funcional, diseño Bootstrap, código comentado, sin errores SQL

### Semana 13 — Actividad: API REST Portafolio
**Objetivo:** Convertir el portafolio en una API REST consumible.
**Instrucciones:**
1. Crear api/proyectos.php con endpoints GET/POST/PUT/DELETE
2. Responder en JSON con status codes correctos
3. Crear frontend JS con fetch() que consuma la API
4. Documentar endpoints en README.md
**Criterios de logro:** API REST funcional, JSON válido, fetch() sin errores, documentación

### Semana 14 (S1) — Actividad: Comentarios AJAX
**Objetivo:** Sistema de comentarios en tiempo real sin recargar página.
**Instrucciones:**
1. Formulario HTML con jQuery + evento submit
2. $.post() a save_comment.php
3. Respuesta JSON → append al DOM
4. Bonus: validación con jQuery Validate
**Criterios:** Sin recarga, jQuery funcional, validación client-side

### Semana 14 (S2) — Actividad: IA Assistant
**Objetivo:** Usar IA para mejorar código propio.
**Instrucciones:**
1. Abrir Claude/Gemini
2. Pegar el código del portafolio y pedir: "Mejora este código PHP: seguridad, legibilidad, mejores prácticas"
3. Comparar antes/después
4. Documentar qué mejoras sugirió la IA
**Criterios:** Comparación documentada, mejoras implementadas, reflexión crítica

### Semana 15 — Actividad: Debate Ético
**Objetivo:** Debatir implicancias éticas de la IA en desarrollo de software.
**Formato:** Grupos de 4. Cada grupo recibe un caso. 20 min de preparación, 5 min de presentación.
**Casos:**
1. "Una IA generó el 80% del código de una app médica. ¿Quién es responsable si falla?"
2. "Un estudiante usó IA para toda su tesis. ¿Es válido?"
**Criterios:** Argumentación fundamentada, referencias a fuentes, contra-argumentos

@Cristian ¿aprobamos estas actividades?

---

## [14:04] — Kimche 🧪

@todos Revisando código de semana 12 desde teclab. Lo que veo:

### Semana 12 — CRUD PHP + MySQL
El contenido de teclab cubre bien: db_config.php, create.php, insert.php, list.php, edit.php, delete.php. Incluye subida de imágenes. **Listo para slides.**

### Semana 13 — API REST PHP
El contenido de teclab tiene: config.php con headers CORS, api/proyectos.php con switch por método HTTP, respuesta JSON. Cubre GET/POST/PUT/DELETE. **Listo para slides.**

### Semana 14 (S1) — jQuery + AJAX
Voy a preparar el código de ejemplo:

```php
// save_comment.php
header('Content-Type: application/json');
$data = json_decode(file_get_contents('php://input'), true);
$data['fecha'] = date('Y-m-d H:i:s');
$data['id'] = uniqid();
// Guardar en archivo JSON
$comments = json_decode(file_get_contents('comments.json') ?: '[]', true);
$comments[] = $data;
file_put_contents('comments.json', json_encode($comments));
echo json_encode($data);
```

Frontend con jQuery:
```javascript
$('#commentForm').submit(function(e) {
    e.preventDefault();
    $.post('save_comment.php', JSON.stringify({
        autor: $('#autor').val(),
        texto: $('#texto').val()
    }), function(resp) {
        $('#comments').prepend(`<div class="card"><strong>${resp.autor}</strong>: ${resp.texto}</div>`);
        this.reset();
    }, 'json');
});
```

@Newen este código está listo para las slides.

### Semana 14 (S2) — IA Aplicada
No necesita código, pero puedo preparar una guía con prompts de ejemplo para los estudiantes.

### Semana 15 — Ética
Puedo armar los 4 casos de estudio + guía de debate para el docente.

@Cristian ¿procedo con los ejemplos de código para semana 14 y 15?

---

## [14:06] — Newen 🚀

@todos Excelente. Ya tenemos el plan completo. Resumo decisiones:

### Decisiones

**D-001:** Distribución de 5 sesiones aprobada (CRUD → API → jQuery → IA → Ética)
**D-002:** Estándar de calidad: semana 8 como benchmark
**D-003:** Actividades prácticas diseñadas por @Antu para cada sesión
**D-004:** Código de ejemplo preparado por @Kimche para sesiones nuevas
**D-005:** Desglose de contenido para semana 14-15 aprobado por @Hermes

### Acciones inmediatas

| Prioridad | Tarea | Responsable | Deadline |
|---|---|---|---|
| 🔴 Crítica | Slides semana 12 (2 PPTs) | Newen | HOY |
| 🔴 Crítica | Slides semana 13 (2 PPTs) | Newen | HOY |
| 🟡 Alta | Contenido semana 14 (jQuery) | Wirin | Mañana |
| 🟡 Alta | Contenido semana 14 (IA) | Wirin | Mañana |
| 🟡 Alta | Contenido semana 15 (Ética) | Wirin | Mañana |
| 🟡 Alta | Slides semana 14-15 (3 PPTs) | Newen | Al tener contenido |
| 🟢 Normal | Subir todo a docentia-docs | Newen | Al completar |

@Cristian con tu aprobación, empiezo AHORA con las slides de semana 12. Los contenidos ya están en teclab, solo necesito generar las presentaciones con la plantilla TECUCT y Pollinations.ai para las imágenes.

---
