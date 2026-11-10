---
task: unblockCreative()
responsavel: "@keith-johnstone"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: block_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: project_context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: false

Saida:
  - campo: creative_unblock
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "Tipo de bloque diagnosticado con raíz emocional identificada" 
  - "[ ] Al menos 3 ejercicios prescritos y explicados" 
  - "[ ] Micro-goal set for immediate action" 
---

# Task: Creative Unblocking

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*unblock-creative`
Keith Johnstone (Ejecución)keith-johnstone)
**Purpose:** Diagnostique y supere los bloques creativos usando técnicas de improvisación y juegos de historias.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `block_description` ← El usuario describe su punto atorado Silencio Silencio
| `project_context` Silencio Lo que están trabajando en Silencio PreFERRED
| `what_theyve_tried` Silencio Anterior intentos de desbloquear Silencio NO TENIDO
| `deadline_pressure` Silencios Silencio Silencio Silencio Silencio Silencio
| `creative_history` ← Los éxitos y patrones pasados TENIDO NO TENIDO

## Preconditions

1. El usuario reconoce que están creativamente atascados
2. Existe algún contexto sobre el proyecto o el esfuerzo creativo
3. Voluntad de tratar enfoques no convencionales

## Fases de Ejecución

### Fase 1: Diagnostico Bloque

1. Identificar el tipo de bloque creativo:
   - **El miedo al fracaso** - El crítico interno es demasiado alto (más común)
   *Perfectionismo* – Refusing to produce anything less than perfect
   - *La ansiedad de los tatuajes* - El miedo a parecer tonto o incompetente.
   * Paralisis de la decisión** — Demasiadas opciones, no pueden comprometerse
   - **Afuera** - Extensión creativa de la sobre-trabaja
   - **Perdido hilo** - Empecé fuerte, perdió el hilo narrativo
   * Página negra** – No se puede encontrar ningún punto de partida
2. Evaluar la gravedad — ¿pueden producir algo, o es total congelación?
3. Identificar la raíz emocional - ¿qué sentimiento está conduciendo el bloque?
4. Busque patrones - ¿Ha ocurrido esto antes? ¿Qué lo rompió entonces?

# Fase 2: Ejercicios improvisados

1. ** "Sí, Y"** — Aceptar cada idea sin juicio y construir sobre ella
   - Escribe 10 ideas terribles.
   - El punto es volumen, no calidad - bajar la barra completamente
2. **Status Shift** — Cambiar la dinámica de poder en la historia
   - Haz débil al poderoso personaje, el débil carácter poderoso
   - A menudo una historia atascada es realmente una relación de estado atascado
3. ** Oferta ciega** — Comience con una acción y descubra el significado después de
   - Escribe la siguiente escena sin saber a dónde va
   - Deja que el subconsciente dirija; la mente consciente sigue
4. **Tilt** - Introducir un elemento inesperado que cambia todo
   - ¿Y si lo contrario fuera verdad?
   - ¿Qué pasaría si la peor cosa posible ocurriera ahora?
5. **Asociación Libre** — Escriba sin parar durante 10 minutos
   - Sin edición, sin juicio, sin espacio trasero
   - Sigue lo que venga, aunque parezca irrelevante.

## Fase 3: Juegos de historia

1. **La versión de borrado** — Escribe la versión más obvia y aburrida de la escena
   - Contraintuitivamente, esto a menudo revela lo que es la versión interesante
   - Retirar la presión de la originalidad
2. **Estacional de la vida** — Mi experiencia personal para el material
   - ¿Qué te pasó hoy?
   - Los detalles reales hacen que la ficción se sienta auténtica
3. **La peor versión** — Escribe deliberadamente la peor versión posible
   - Esto derrota al perfeccionismo haciendo "bad" el objetivo
   - A menudo produce material sorprendentemente útil
4. ** Entrevista de Carácter** - Deja que el personaje hable por sí mismo
   - Pregunta: ¿Qué quieres? ¿Qué tienes miedo? ¿Qué nunca harías?
   - El personaje suele conocer la historia mejor que el autor.
5. ** Caja de restricciones**: Agrega restricciones arbitrarias para forzar la creatividad
   - Escribe exactamente 100 palabras. No uses adjetivos. Sólo diálogo.
   - Limita paradójicamente la liberación

### Fase 4: Reframe &amp; Reconnect

1. Rechazar el bloque como información - ¿Cuál es la resistencia que intenta decirle?
2. Identificar lo que ES trabajando —construir de la fuerza, no de la debilidad
3. Reconectarse con el impulso original - ¿por qué este proyecto le excitaba inicialmente?
4. Establecer un micro-goal — no "acaba el capítulo" sino "escribir un párrafo"
5. Crear un ritual — una acción específica que señale "modo creador está comenzando"
6. Programar la próxima sesión creativa: el impulso requiere continuidad
7. Proporcionar una receta de desbloqueo personalizada basada en el tipo de bloque específico

## Formato de salida

```yaml
creative_unblock:
  specialist: "keith-johnstone"
  block_type: "{tipo diagnosticado}" 
  severity: "mid Ø moderada Silencio severo" 
  emotional_root: "{comprensión de sentimiento}" 
  diagnosis: "¿Por qué está pasando el bloque y qué señaliza?"
  exercises_prescribed:
    - exercise: "{name}"
      instructions: "{Paso a paso}" 
      purpose: "¿Por qué esto ayuda a este bloque específico?" 
      time_required: "{duration}"
  reframe: "¿Cómo ver el bloque de forma diferente?"
  micro_goal: "{acción pequeña inmediata}" 
  ongoing_practice: "{habita para evitar la recurrencia}" 
```

## Condiciones de veto

- *Nunca* *dile a alguien que "sólo se apodere" – los bloques tienen causas emocionales
- ** NUNCA** criticar el trabajo existente del usuario durante una sesión de desbloqueo
- **Nunca** añadir presión - plazos y estacas empeoran los bloques
* ** NUNCA** prescribir un enfoque único — siempre ofrecer múltiples ejercicios para elegir
- ###############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################

## Criterios de finalización

Tipo de bloque diagnosticado con raíz emocional identificada
Al menos 3 ejercicios prescritos, adaptados al bloque específico
- Cada ejercicio explicado con instrucciones claras y propósito
- [ ] Bloqueo reorganizado como información en lugar de falla
- [ ] Micro-goal set for immediate action
- [ ] Práctica continua recomendada para prevenir la recurrencia
