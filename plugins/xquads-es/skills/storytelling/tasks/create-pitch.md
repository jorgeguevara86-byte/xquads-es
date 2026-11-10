---
task: createPitch()
responsavel: "@oren-klaff"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: pitch_subject
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: target_audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: pitch_narrative
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Audiencia perfilada con criterios de decisión mapeados" 
  - "[ ] Enfoque narrativo seleccionado y todos los golpes estructurados" 
  - "[ ] clara pregunta con la manipulación de la objeción preparado" 
---

# Task: Pitch Deck Narrative

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*create-pitch`
*Oren Klaff*oren-klaff) o Nancy Duarte (nancy-duarte)
**Purpose:** Crear una narrativa de lanzamiento convincente que capta la atención y conduce la acción.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `pitch_subject` Silencio Silencio Silencio Silencio Silencio Silencio
| `target_audience` Silenciosos inversores, clientes, socios, interna Silencio
| `desired_outcome` TENRI financiación, acuerdo, aprobación, buy-in Silencio , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
| `key_data_points` TENIDO TERMINADOR, tracción, finanzas TENIDO ANTERITORIO
| `time_limit` Silencio duración Pitch Silencio NO (predeterminado: 10 min) Silencio
| `existing_deck` Silencio diapositivas actuales o esquema Silencio NO Silencio

## Preconditions

1. Comprensión clara de lo que se está lanzando
2. Público objetivo identificado con sus decision-making context
3. Puntos clave de datos disponibles para apoyar la narrativa

## Fases de Ejecución

### Fase 1: Analyze Audience

1. Perfile el público —quienes son ellos, qué valoran, cuáles son sus miedos?
2. Identificar su marco actual - ¿Cómo ven el mundo ahora mismo?
3. Mapear sus criterios de decisión - ¿qué debe ser verdad para ellos decir que sí?
4. Determinar la dinámica del estado - ¿Está usted lanzando, abajo o lateralmente?
5. Determinar posibles objeciones y puntos de resistencia
6. Enfoque seleccionado: Klaff (control de marcos, tensión) o Duarte (esparquelina, transformación)

### Fase 2: Estructura Narrante

**Si se acerca Klaff (oren-klaff):**
1. **Configurar el marco** — Establezca su marco como el dominante (frazo de precio, plazo, marco de autoridad)
2. **Dile la historia** — Ganar con intriga, crear tensión, crear deseo
3. **Reveal the Intrigue** - La única visión o oportunidad que cambia todo
4. **Oferta del Premio** - Posición yourself/product como el premio, no el vendedor
5. **Nail the Hookpoint** — El momento en que se inclinen y quieran más
6. ** Obtener la decisión** - Conducir a un claro yes/no (no "dejenme pensar en ello")

**Si Duarte se acerca (nancy-duarte):**
1. **Lo que es** — Pinta la realidad actual (el mundo del público hoy)
2. **Lo que podría ser** - Revelar la posibilidad (el futuro mejor)
3. **Suplente** — Retrocede entre el dolor actual y la promesa futura (espacila)
4. ** Call to Action** — El paso específico para pasar de "lo que es" a "lo que podría ser"
5. **Nueva Bienaventuranza** — Pinta el futuro transformado vívidamente

### Fase 3: Construir la Tensión

1. Identificar la tensión central - la brecha entre el estado actual y la posibilidad
2. Amplificar la urgencia — ¿por qué debe ocurrir esto ahora? ¿Cuál es el costo de la inacción?
3. Capa en puntos de prueba — datos, testimonios, tracción que valida la narrativa
4. Crear picos emocionales — momentos de sorpresa, deleite o preocupación
5. Gestionar el pacing — rápido para la emoción, lento para la gravedad
6. Objeciones de mano preventivamente — teje respuestas a la narrativa

### Fase 4: Resolución de diseño

1. Hacer la pregunta cristal claro - exactamente lo que usted desea y por cuando
2. Simplificar la decisión — reduzca a una opción binaria
3. Crear los siguientes pasos: acciones inmediatas después del lanzamiento
4. Terminar con la resonancia — una imagen o una declaración de cierre memorable
5. Prepararse para Q beneficiarA — prever las 5 preguntas principales y preparar respuestas
6. Diseño de leave-behind — lo que queda con ellos después de salir de la habitación

## Formato de salida

```yaml
pitch_narrative:
  subject: "¿Qué está siendo lanzado?" 
  approach: "klaff_frame_control | duarte_sparkline"
  specialist: "oren-klaff | nancy-duarte"
  audience: "{Grupo de meta.]" 
  desired_outcome: "¿Qué es el éxito?" 
  duration: "{Tiempo estimado}" 
  narrative_beats:
    - beat: 1
      name: "{beat name}" 
      content: "¿Qué? say/show}" 
      emotional_target: "{sentimiento de la audiencia}" 
      duration: "{tiempo asignado}" 
  tension_points: ["{momentos de tensión clave}" ]
  proof_points: ["{datos y pruebas}" ]
  the_ask: "{pregunta específica}" 
  objection_handling:
    - objection: "{preocupación anticipada}" 
      response: "{Respuesta preventiva}" 
  closing_statement: "{Terminato memorable}" 
```

## Condiciones de veto

- **Nunca** lanzamiento sin entender primero al público
################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
- **Nunca** confía en datos solos sin narración emocional
- ** NUNCA** crear un lanzamiento más largo que el límite de tiempo permite
- **Nunca** dejar al público sin los próximos pasos claros

## Criterios de finalización

- Audiencia perfilada con criterios de decisión
- [ ] Enfoque narrativo seleccionado y justificado
- Todos los golpes estructurados con contenidos y objetivos emocionales
- Tensión construida con urgencia y puntos de prueba
- [ ] Pregunta clara con la ruta de decisión simplificada
- [ ] Manejo de objetos preparado
- [ ] Cerramiento memorable diseñado
