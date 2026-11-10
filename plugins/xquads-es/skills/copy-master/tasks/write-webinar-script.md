---
task: writeWebinarScript()
responsavel: "@russell-brunson"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: offer
    tipo: object
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: webinar_script
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Marco Webinar perfecto ejecutado completamente (todas las 5 secciones)" 
  - "[ ] 3 Estructura de secretos con belief-breaking puentes epifanía" 
  - "[ ] Stack y secuencia cercana completa con el anclaje de precio" 
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Write Webinar Script

** ID de la lista:** COPY-M-012
**Version:** 2.0.0
**Command:** `*write-webinar-script`
**Agente: ** Russell Brunson (Rusell Brunson)russell-brunson)
**Purpose:** Escribe un script webinar completo usando el marco Webinar perfecto con psicología de persuasión estratada.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service con transformación central TEN
Silencios en la audiencia Silencio Silencio inducido por el usuario Silencio Silencio Personaje de los asistentes con las creencias y objeciones actuales Silencio
Silencio oferta Silencioso objeto Silencio Usuario prompt Silencio Sí Silencio Precio, garantía, bonos, elementos de urgencia Silencio
| webinar_type TEN enum TENIDO Usuario prompt TEN NO TENViva, automatizada, híbrida — defaults to live TEN
| duration_target TENEDA TENIDO TENIDO EL Usuario prompt TEN No TEN 60min (standard), 90min (extended), 45min (condensed) — defaults to 60min ANTE
| three_secrets Silencio lista Silenciosos Usuarios prompt Silencio No Silencio Predefinido secrets/myths para romper, o agente los derivará Silencio
| origin_story Silencio Silencio Silencio Usuario prompt Silencio No Silencio La historia de origen personal del altavoz para el puente epifanía Silencio

---

## Preconditions

- Transformación de productos claramente definida (before/after Estado)
- Estructura de la oferta completa con precio, garantía y pila de bonificación
- Elementos de credibilidad de altavoz disponibles (creenciales, resultados, historia)
- Al menos 3 falsas creencias que el público sostiene que debe ser roto

---

# Champion Reference

Estudiar estos real-world campeón webinars antes de escribir:

1. **"Los secretos de Hacking de túneles" Perfect Webinar** (Russell Brunson) — La ejecución definitiva del marco Webinar perfecto, vendió ClickFunnels a millones
2. **"Expert Secrets" Webinar** (Russell Brunson) — Meta-webinar enseñando el marco webinar mientras lo ejecuta, masterclass en framework demonstration
3. **Tony Robbins' UPW Enrollment Webinar** — Autoridad + apilación de pruebas sociales, emocional peak-state vender, high-ticket cerca
4. **La "Sociedad de Constructores de la List" de Amy Porterfield** — webinar con una suave transición para ofrecer, trust-first acercamiento para audiencias cálidas
5. **Todd Brown "E5 Method" Webinar** — Big Idea driven webinar, mechanism-heavy, audiencia sofisticada

---

## Fases de Ejecución

## Fase 1: Configuración del marco Webinar perfecto

1. **Introducción (5 min):** Ganancia + credibilidad + promesa de la sesión
   - Gran promesa: "Al final de esta presentación, sabrás exactamente cómo..."
   - Credencial de los oradores: Posicionamiento rápido de la autoridad
   - Reglas del webinar: "Toma notas, quédate hasta el final de la oferta especial"
2. **El único reto (5 min):** Definir la nueva oportunidad única
   - No es una oferta de mejora (mejor versión de lo que están haciendo)
   - Una nueva oportunidad (muy diferente al resultado deseado)
   - Enmarcar el cambio: "La razón por la que no has logrado X no es por Y — es porque necesitas Z"
3. **Los 3 Secretos (30 min):** belief-breaking segmentos
   - Secreto 1: Romper la creencia VEHICLE (el method/approach)
   - Secreto 2: Romper la creencia INTERNAL (su habilidad personal)
   - Secreto 3: Romper la creencia EXTERNAL (circunstancias externas)
   - Cada secreto sigue la estructura de Epifanía Bridge Story
4. **El Stack (10 min):** Valor de la pila y presentación
   - Presentar cada componente de la oferta individualmente
   - Bastidor de diapositivas valor total visual
   - Precio revelado con anclaje
   - Guarantee
   - Montón de bonificación con escasez
5. **El cierre (10 min):** Empuje final con urgencia
   - "Dos opciones" cierra: cambiar o mantenerse igual
   - Preguntas frecuentes / manejo de objeciones
   - Final CTA con instrucciones exactas
   - Regreso / refuerzo de escasez

## Fase 2: Historias del Puente de Epifanía

Para cada uno de los 3 Secretos, construir una historia del puente de Epifanía:
1. **Backstory:** Establecer la escena — ¿dónde estabas antes del descubrimiento?
2. **Viaje:** ¿Qué pasó que llevó al descubrimiento?
3. ** Nuevo descubrimiento de oportunidad:** El momento de la epifanía
4. **Framework/Strategy:** El sistema que surgió del descubrimiento
5. ** Logros:** Los resultados que siguieron
6. **Bridge:** Conectar la epifanía a la situación del público

## Fase 3: Capa Psicológica

1. Mapa Cialdini principios en la estructura webinar:
   **Introducción:** Autoridad (creenciales), Prueba Social (conteo de asistentes, resultados)
   - **El único asunto:** Compromiso (pregunta por pequeños acuerdos - "¿Tiene sentido?")
   **Secret 1:** La mentira (la historia personal crea conexión)
   - **Secret 2:** Unidad (identidad compartida — "Yo era como tú")
   - **Secret 3:** Reciprocidad (valor libre masivo durante la enseñanza)
   - **El Stack:** Escarpada (bonos limitados, aumento de precios)
   - **El Cierre:** Consistencia (convinieron con cada secreto, por lo que la oferta es el siguiente paso lógico)
2. Aplicar las palancas de Blair Warren a través del webinar:
   - Anime sueños: A lo largo, especialmente en future-pacing
   - Justificar los fallos: Secreto 1 (el viejo vehículo estaba equivocado, no tú)
   - Teme a Allay: Secreto 2 (puedes hacer esto, aquí está la prueba)
   - Confirma sospechas: Secreto 3 (Tenías razón de que X te estaba reteniendo)
   - Tirar piedras a los enemigos: A lo largo (la industria, el gurus, el viejo camino)
3. Construcción micro-commitments en todo — "Tipo YES en el chat si..."
4. Asegurar que cada transición entre secciones tenga un pico emocional

### Fase 4: Escritura

1. Escriba la sección completa del script por sección con notas de altavoces
2. Incluir los cuestiones de dirección de diapositivas entre corchetes: [SLIDE: ...]
3. Incluir las indicaciones de interacción de la audiencia: [POLL: ...], [CHAT: ...], [Q PulA: ...]
4. Escribir líneas de transición entre secciones para mantener el impulso
5. Incluir marcadores de tiempo para el pacing
6. Escribe la guía de manejo Q Pul pre-loaded respuestas a las objeciones
7. Escribe el post-webinar follow-up esquema de secuencia de correo electrónico (3-5 emails)

## Fase 5: Notas de producción

1. Cuenta de diapositivas y resumen de contenido por sección
2. Los momentos visuales clave (cartas, capturas de pantalla, diapositivas de pila)
3. Mapa de arco emocional en todo el webinar
4. Estrategia de repetición sugerida (deadline, mensajería de escasez)
5. Metrices a seguir: tasa de asistencia, compromiso, oferta click-through, conversión

---

## Formato de salida

```markdown
## Webinar Script: {Webinar Title}

**Framework:** Perfect Webinar (Brunson)
**Duration:** {X} minutes
**Audience:** {audience}
**The One Thing:** {new opportunity statement}
**Offer:** {offer summary}

### Persuasion Architecture
| Section | Duration | Cialdini Principles | Warren Levers |
|---------|----------|--------------------|--------------  |
| Introduction | 5 min | {principles} | {levers} |
| The One Thing | 5 min | {principles} | {levers} |
| Secret 1 | 10 min | {principles} | {levers} |
| Secret 2 | 10 min | {principles} | {levers} |
| Secret 3 | 10 min | {principles} | {levers} |
| The Stack | 10 min | {principles} | {levers} |
| The Close | 10 min | {principles} | {levers} |

---

### INTRODUCTION (0:00 - 5:00)
{Script with slide cues and speaker notes}
[SLIDE: Title + Speaker Credibility]

### THE ONE THING (5:00 - 10:00)
{New opportunity framing}
[SLIDE: Old Opportunity vs New Opportunity]

### SECRET 1: {Title} — Breaking the Vehicle Belief (10:00 - 20:00)
**False Belief:** {what they currently believe}
**Epiphany Bridge Story:** {story arc}
**New Belief:** {what they'll believe after}
{Full script}
[SLIDE: Secret 1 Visual]

### SECRET 2: {Title} — Breaking the Internal Belief (20:00 - 30:00)
**False Belief:** {what they believe about themselves}
**Epiphany Bridge Story:** {story arc}
**New Belief:** {what they'll believe after}
{Full script}
[SLIDE: Secret 2 Visual]

### SECRET 3: {Title} — Breaking the External Belief (30:00 - 40:00)
**False Belief:** {what they believe about external factors}
**Epiphany Bridge Story:** {story arc}
**New Belief:** {what they'll believe after}
{Full script}
[SLIDE: Secret 3 Visual]

### THE STACK (40:00 - 50:00)
{Value stack presentation with running total}
[SLIDE: Stack Slide — building value]
[SLIDE: Price Reveal]
[SLIDE: Guarantee]
[SLIDE: Bonus Stack]

### THE CLOSE (50:00 - 60:00)
{Two choices close + FAQ + final CTA}
[SLIDE: Two Paths — Change vs Same]
[SLIDE: CTA with URL/button]

---

### Post-Webinar Email Sequence (Outline)
| Email | Send | Subject | Purpose |
|-------|------|---------|---------|
| 1 | Immediately | Replay link | Recap + CTA |
| 2 | Day 2 | Testimonial | Social proof push |
| 3 | Day 3 | FAQ | Objection handling |
| 4 | Day 4 | Final chance | Scarcity close |

### Production Notes
- **Total slides:** {count}
- **Key interaction moments:** {list}
- **Emotional arc:** Curiosity -> Hope -> Belief -> Desire -> Urgency
- **Replay strategy:** {description}
- **Metrics to track:** {list}
```

---

## Condiciones de veto

- NUNCA saltar la estructura de 3 Secretos - es el motor de persuasión núcleo
- Nunca presentar la oferta antes de romper las 3 creencias
- Nunca escriba un seminario web sin historias de Epiphany Bridge - datos solos no convierte
- Nunca cierra sin un marco de "dos opciones" - crea urgencia psicológica
- NUNCA saltar la diapositiva Stack - la acumulación de valor visual es crítica para el anclaje de precios

---

## Criterios de finalización

- [ ] Marco Webinar perfecto ejecutado completamente (todas las 5 secciones)
- [ ] El único truco define claramente una nueva oportunidad (no mejora)
- [ ] 3 Secretos con tipos de creencias distintos (vehículo, interno, externo)
Cada Secreto tiene una historia completa del puente epifanía
- [ ] diapositivas de Stack construye valor total antes de que el precio revele
- [ ] Close incluye dos opciones de marco, FAQ, y CTA final
- [ ] Direccional de dirección de diapositivas cuestiones incluidas en todas partes
- [ ] Marcadores de Timing proporcionados para el pacing
- [ ] secuencia de correo electrónico pos-webinar delineada
- [ ] Notas de producción con métricas
- [ ] Capa Psicológica aplicada - Principios Cialdini mapeados por sección
Blair Warren se accionó a través del arco de webinar
