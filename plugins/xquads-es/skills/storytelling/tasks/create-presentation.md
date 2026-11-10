---
task: createPresentation()
responsavel: "@nancy-duarte"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: presentation_topic
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: presentation
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Audiencia perfilada con creencias actuales y resistencia mapeado" 
  - "[ ] Estructura de chispalina creada con contrastes alternantes" 
  - "[ ] Momento estrella diseñado y llamada a la acción definida" 
---

# Task: Presentation Narrative Arc

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*create-presentation`
# Nancy Duarte #nancy-duarte)
**Purpose:** Diseñar una narrativa de presentación usando la metodología Sparkline (Lo que es / Lo que podría ser).

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `presentation_topic` Silencio Silencio Silencio Silencio Silencio Silencio
| `audience` Silencio Quién asistirá a la vida
| `desired_action` ← Qué público debe hacer después de Silencio
| `key_data` tención soporte de hechos, métricas, investigación TENIDO ANTERITORIO
| `duration` Silencio tiempo disponible Silencio NO (predeterminado: 20 min) Silencio
| `existing_content` Silencios actuales diapositivas o notas Silencio NO Silencio

## Preconditions

1. El mensaje temático y clave se define
2. La audiencia se identifica con su contexto y preocupaciones
3. Acción deseada del público después de la presentación es clara

## Fases de Ejecución

### Fase 1: Análisis de audiencia

1. Perfil del público — función, nivel de conocimiento, preocupaciones, motivaciones
2. Identificar su creencia actual - ¿Qué creen que es verdad ahora?
3. Mapear su resistencia — ¿qué los haría rechazar su mensaje?
4. Defina la brecha — la distancia entre su creencia actual y su creencia deseada
5. Determinar el viaje emocional - ¿dónde comienzan y dónde deben terminar?
6. Identificar la única llave que se lleva — si recuerdan sólo una cosa, ¿qué es?

## Fase 2: Estructura de la Esparcilínea

1. ** Apertura (Lo que es)** — Describe la realidad actual de manera viva
   - Poner al público en experiencia compartida
   - Reconocer el dolor o la limitación que sienten
   - Usar una historia relatable o una estadística llamativa
2. **Primero Contraste (Lo que podría ser)** — Revelar la posibilidad
   - Pintar el futuro mejor en términos concretos
   - Crear deseo - hacer que quieran este futuro
3. **Retroceder y Forth** — Suplente entre el dolor actual y la promesa futura
   - Cada rezadera levanta las apuestas
   - Capa de evidencia: datos, historias, ejemplos, analogías
   - Construir el impulso - cada ronda es más convincente
4. **El Momento de la Estrella** — Un momento memorable que el público nunca olvidará
   - Una demostración dramática, sorprendente estadística o poderosa historia
   - Este es el pico emocional de la presentación
5. ** Call to Action** — El paso específico para pasar de "lo que es" a "lo que podría ser"
   - Hazlo concreto, alcanzable e inmediato
   - Conectarlo a los valores y motivaciones del público

## Fase 3: Qué-es / qué-podría-ser Contenido

1. Para cada sección "Lo que es":
   - Use ejemplos concretos y específicos del dolor actual
   - Datos de referencia que validan el problema
   - Mantenlo honesto - no exagerar, pero no suavizar
2. Para cada sección "Lo que podría ser":
   - Usar imágenes vívidas del futuro transformado
   - Mostrar pruebas de que el futuro es alcanzable (estudios de casos, precedentes)
   - Conectar emocionalmente - mostrar impacto humano
3. Transiciones de diseño: cada movimiento debe fluir naturalmente
4. Planificar soporte visual - qué slides/visuals ¿Amplificar cada momento?
5. Datos y historia de equilibrio - ni domina, ambos refuerzan

### Fase 4: Nueva felicidad

1. Pintar la "Nueva Bienaventuranza" — el mundo después de que el público actúe
2. Hacerlo específico y tangible — no promesas abstractas
3. Conéctate a la apertura - cierra el bucle narrativo
4. Terminar con una imagen final resonante o declaración
5. Diseñar el eco — la frase o la idea que se queda con ellos durante días
6. Prepararse para Q PulA — prever las preguntas principales y preparar respuestas concisas

## Formato de salida

```yaml
presentation:
  topic: "{Tema de la presentación}" 
  specialist: "nancy-duarte"
  methodology: "Sparkline"
  audience: "{Grupo de meta.]" 
  desired_action: "¿Qué público debería hacer?" 
  duration: "{time}"
  key_takeaway: "- ¿Qué?" 
  sparkline:
    - section: "Apertura - Lo que es" 
      content: "{realidad actual}" 
      visual_support: "{ concepto deslizante}" 
      duration: "{time}"
    - section: "Contraste 1 - Lo que podría ser" 
      content: "{La posibilidad}" 
      visual_support: "{ concepto deslizante}" 
      duration: "{time}"
    # ... additional toggles
    - section: "Star Moment" 
      content: "{CTOQUE MEMORIAL}" 
      visual_support: "{ visual dramática}" 
      duration: "{time}"
    - section: "Llamado a la acción" 
      content: "{pregunta específica}" 
      duration: "{time}"
    - section: "Nueva Bienaventuranza" 
      content: "{En adelante traducido}" 
      duration: "{time}"
  star_moment: "{descripción del momento memorable}" 
  closing_statement: "{Resonante final}" 
  qa_prep:
    - question: "{Cuestión anticipada}" 
      answer: "{repuesta preparada}" 
```

## Condiciones de veto

* * * NUNCA* *Empieza con una agenda aburrida* – abierta con historia o datos llamativos
- *Nunca* *presente todo lo que es* seguido por todo lo que podría ser* – alternarlos
################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
- **Nunca** termina sin una clara llamada a la acción - los públicos necesitan saber qué hacer después
- ** NUNCA** dejar que los datos sustituyan la historia — los datos demuestran, la historia persuade; use ambos

## Criterios de finalización

- Audiencia perfilada con creencias y resistencias actuales mapeadas
- Estructura de chispa con contrastes alternantes
- [ ] Momento estrella diseñado para el máximo impacto
Cada sección tiene conceptos de contenido y soporte visual
- [ ] La llamada a la acción es concreta y alcanzable
- Nueva Bienaventuranza pinta un futuro transformado
- [ ] El tiempo encaja dentro de la duración asignada
