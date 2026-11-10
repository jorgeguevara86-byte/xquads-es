---
task: mapArchetype()
responsavel: "@archetype-consultant"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: brand_values
    tipo: list
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Perfil del arquetipo de marca" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Los 12 arquetipos evaluados y los 3 mejores puntuados" 
  - "[ ] Arquetipos primarios y secundarios seleccionados" 
  - "[ ] Ejemplos de aplicaciones proporcionados para más de 5 puntos de contacto" 
---

# Tarea: Mapa del arquetipo de marca

**ID de tarea:** MARCA-007
**Version:** 1.0.0
**Command:** `*map-archetype`
**Agente:** Consultor de Arquetipo (archetype-consultant)
**Propósito:** Identificar y aplicar el arquetipo junguiano de la marca para guiar la personalidad, los mensajes y la experiencia.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| marca | cadena | Mensaje de usuario | Sí | Nombre de la marca y descripción |
| audiencia | cadena | Mensaje de usuario | Sí | Público objetivo y sus aspiraciones |
| brand_values | lista | Mensaje de usuario | Sí | Valores y creencias fundamentales |
| industria | cadena | Mensaje de usuario | No | Contexto de la industria |
| competidores | lista | Mensaje de usuario | No | Competidores con sus arquetipos percibidos |
| current_perception | cadena | Mensaje de usuario | No | Cómo se percibe actualmente la marca |

---

## Preconditions

- Valores de marca articulados (incluso de manera informal)
- Comprensión de lo que aspira la audiencia

---

## Fases de Ejecución

### Fase 1: Análisis de Arquetipos
1. Evalúe la marca frente a los 12 arquetipos:
   - **Inocente:** Optimismo, sencillez, pureza (Dove, Coca-Cola)
   - **Explorador:** Libertad, descubrimiento, aventura (Jeep, Patagonia)
   - **Sabio:** Sabiduría, conocimiento, verdad (Google, BBC)
   - **Héroe:** Coraje, maestría, logros (Nike, FedEx)
   - **Outlaw:** Liberación, revolución, disrupción (Harley-Davidson, Virgin)
   - **Mago:** Transformación, visión, imaginación (Apple, Disney)
   - **Chico normal:** Pertenencia, autenticidad, conexión (IKEA, Target)
   - **Amante:** Intimidad, pasión, belleza (Chanel, Godiva)
   - **Jester:** Alegría, humor, vivir el momento (Old Spice, M&Ms)
   - **Cuidador:** Servicio, compasión, cariño (Johnson & Johnson, TOMS)
   - **Creador:** Innovación, self-expression, originalidad (LEGO, Adobe)
   - **Regente:** Control, autoridad, liderazgo (Mercedes, Rolex)
2. Califique los 3 arquetipos principales según su ajuste (1-10 en alineación de valores, resonancia de la audiencia, diferenciación competitiva)
3. Identificar el arquetipo primario y la influencia secundaria.
4. Validar frente a los arquetipos de la competencia para garantizar la diferenciación

### Fase 2: Guía de expresión de arquetipos
1. Defina cómo se manifiesta el arquetipo primario en la marca:
   - **Core Desire:** Lo que el arquetipo quiere fundamentalmente
   - **Objetivo:** Lo que el arquetipo intenta lograr
   - **Miedo:** Lo que el arquetipo evita
   - **Estrategia:** Cómo el arquetipo aborda los desafíos
   - **Regalo:** Lo que el arquetipo ofrece al mundo
   - **Sombra:** El lado oscuro a evitar (arquetipo llevado demasiado lejos)
2. Traducir el arquetipo en expresiones de marca:
   - Tono de voz: Cómo habla la marca
   - Estado de ánimo visual: cómo se ve y se siente la marca
   - Temas de historias: qué historias cuenta la marca
   - Relación con el cliente: Cómo la marca trata a los clientes
   - Temas de contenido: Qué temas cubre la marca

### Fase 3: Mensajería a través de la lente del arquetipo
1. Escribe archetype-aligned mensaje:
   - Lema: Captura la esencia del arquetipo
   - Promesa de marca: enmarcada a través de los valores del arquetipo
   - Mensajes clave: 3-5 mensajes que encarnan el arquetipo
   - Voz en las redes sociales: cómo aparece el arquetipo en el contenido diario
2. Crea la estrategia de contenido archetype-based :
   - Temas de contenido que resuenan con el arquetipo
   - Estructuras de la historia que se alinean (viaje del héroe, descubrimiento, transformación)
   - Desencadenantes emocionales para aprovechar
   - Desencadenantes emocionales a evitar
3. Proporcionar diferenciación arquetípica de la competencia:
   - Donde los competidores ocupan arquetipos similares
   - Cómo expresar un mismo arquetipo de manera diferente
   - Donde el arquetipo secundario crea singularidad

### Fase 4: Ejemplos de aplicación
1. Escribe de 3 a 5 ejemplos del arquetipo en acción:
   - Título de la página de inicio
   - Línea de asunto del correo electrónico
   - Publicación en redes sociales
   - Respuesta de atención al cliente
   - Mensaje de error o página 404
2. Proporcione "¿qué haría {archetype} ?" marco de decisión
3. Cree la hoja de referencia del arquetipo para el equipo:
   - Al tomar decisiones de marca, pregunte: "¿Un {archetype} say/do sería esto?"
   - Referencia rápida sobre lo que se debe y no se debe hacer

---

## Formato de salida

```markdown
## Brand Archetype: {Brand Name}

**Primary Archetype:** {archetype}
**Secondary Influence:** {archetype}
**Archetype Blend:** {X}% {primary} + {Y}% {secondary}

---

### Archetype Scorecard

| Archetype | Values Fit | Audience Fit | Differentiation | Total |
|-----------|-----------|-------------|-----------------|-------|
| {top 1} | X/10 | X/10 | X/10 | XX/30 |
| {top 2} | X/10 | X/10 | X/10 | XX/30 |
| {top 3} | X/10 | X/10 | X/10 | XX/30 |

### Archetype Profile

| Element | Definition |
|---------|-----------|
| Core Desire | {desire} |
| Goal | {goal} |
| Fear | {fear} |
| Strategy | {strategy} |
| Gift | {gift} |
| Shadow | {what to avoid} |

### Brand Expression Guide

| Dimension | Direction | Example |
|-----------|----------|---------|
| Tone of Voice | {description} | {example phrase} |
| Visual Mood | {description} | {reference} |
| Story Themes | {themes} | {example} |
| Customer Relationship | {style} | {example} |

### Archetype-Aligned Messaging
- **Tagline:** {tagline}
- **Promise:** {brand promise}
- **Key Messages:** {3-5 messages}

### Application Examples
| Touchpoint | Example |
|-----------|---------|
| Homepage headline | {copy} |
| Email subject | {copy} |
| Social post | {copy} |
| Support response | {copy} |

### Team Cheat Sheet
**Always ask:** "Would a {archetype} say/do this?"
**Do:** {list}
**Don't:** {list}
```

---

## Condiciones de veto

- NUNCA asigne un arquetipo sin evaluar los 12: el sesgo lleva a escribir mal
- NUNCA ignores el lado oscuro: cada arquetipo tiene una versión oscura que debes evitar.
- NUNCA asigne el mismo arquetipo que el competidor dominante sin una estrategia de diferenciación
- NUNCA recomiendes más de 2 influencias de arquetipos: las marcas con más de 3 arquetipos se sienten confundidas
- NUNCA omita los ejemplos de aplicación: la teoría de arquetipos abstractos no se puede utilizar sin una demostración concreta

---

## Criterios de finalización

- [ ] Los 12 arquetipos evaluados
- [ ] Top 3 anotados con justificación
- [ ] Arquetipos primarios y secundarios seleccionados
- [ ] Guía de expresión de arquetipos completada
- [ ] Mensajes escritos a través de una lente de arquetipo
- [ ] Ejemplos de aplicaciones proporcionados para más de 5 puntos de contacto
- [ ] Hoja de trucos del equipo creada
- [ ] Lado oscuro documentado como barandilla
