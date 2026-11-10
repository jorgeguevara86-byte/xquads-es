---
task: conveneBoard()
responsavel: "@board-chair"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: strategic_question
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: board_meeting
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] 3-5 asesores relevantes consultados con sus marcos" 
  - "[ ] La síntesis identifica acuerdos, desacuerdos y tensiones." 
  - "[ ] Recomendación unificada con opiniones disidentes incluidas" 
---

# Tarea: Reunión de Junta Completa

**ID de tarea:** BOARD-001
**Version:** 1.0.0
**Command:** `*convene-board`
**Agente:** Presidente de la junta directiva (board-chair)
**Propósito:** Convocar una sesión completa del consejo asesor sobre una cuestión estratégica, sintetizando múltiples perspectivas de los asesores.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `strategic_question` | Mensaje de usuario | SÍ |
| `context` | Situación empresarial, datos, limitaciones | SÍ |
| `advisors_requested` | Asesores específicos a incluir | NO (predeterminado: 3-5 más relevantes) |
| `decision_urgency` | Cronograma para la decisión | NO |
| `previous_decisions` | Decisiones pasadas relacionadas | NO |

## Preconditions

1. La pregunta estratégica está claramente formulada.
2. Se proporciona contexto suficiente para que los asesores formen opiniones significativas
3. Al menos 3 asesores son relevantes para el dominio de la pregunta.

## Fases de Ejecución

### Fase 1: Formular la pregunta (board-chair)

1. Replantear la cuestión estratégica en términos precisos.
2. Identificar el tipo de decisión: inversión, escalamiento, cultura, contratación, producto, pivote, salida
3. Mapear las dimensiones de decisión: financiera, operativa, cultural, estratégica, ética
4. Determinar qué 3-5 asesores son más relevantes según los dominios de experiencia
5. Defina las limitaciones: tiempo, recursos, apetito de riesgo, valores.
6. Encuadre la pregunta para cada asesor en su lenguaje y marco.
7. Establecer la agenda: orden de consulta basado en el flujo lógico

### Fase 2: Recopilar perspectivas (dirigida a 3-5 asesores)

Para cada asesor seleccionado, solicite su perspectiva:

1. **Ray Dalio**: análisis basado en principios, evaluación sistemática de riesgos, lente de transparencia radical
2. **Charlie Munger** — Aplicación de modelos mentales, pensamiento inverso, qué podría salir mal
3. **Peter Thiel** — Pensamiento cero-to-one , perspectiva contraria, potencial de monopolio
4. **Reid Hoffman** — Efectos de red, lente de escala blitz, estrategia de alianza
5. **Naval Ravikant** — Análisis de apalancamiento, aplicación de conocimientos específicos, pensamiento long-term 
6. **Simon Sinek** — Alineación de objetivos, perspectiva de juego infinita, por qué detrás de la decisión
7. **Brene Brown** — Evaluación del coraje, vulnerabilidad en el liderazgo, implicaciones para la confianza
8. **Patrick Lencioni**: impacto en la salud del equipo, riesgos de disfunción organizacional
9. **Derek Sivers** — Simplicidad contraria, prueba de "sí o no", lente minimalista
10. **Yvon Chouinard** — Alineación de la misión, impacto de environmental/ethical , sostenibilidad de long-term 

Cada asesor proporciona:
- Su análisis a través de su marco específico
- Riesgos clave que ven
- Su recomendación
- Nivel de confianza (high/medium/low)

### Fase 3: Sintetizar Perspectivas (board-chair)

1. Identificar áreas de acuerdo: ¿dónde convergen los asesores?
2. Identifique áreas de desacuerdo: ¿dónde divergen y por qué?
3. Mapee las tensiones: ¿qué desacuerdos representan compensaciones genuinas versus diferentes suposiciones?
4. Ponderar las perspectivas por relevancia: ¿qué experiencia es más importante para ESTA pregunta?
5. Identifique los puntos ciegos: ¿qué es lo que ningún asesor ha abordado?
6. Busque el "y": ¿se pueden conciliar puntos de vista aparentemente opuestos?

### Fase 4: Presentar recomendación unificada (board-chair)

1. Indique claramente la recomendación sintetizada.
2. Explique el razonamiento: qué perspectivas de los asesores lo influyeron más y por qué.
3. Reconocer las opiniones disidentes: qué argumentos sólidos existen en contra de la recomendación
4. Definir el perfil de riesgo: qué podría salir mal y estrategias de mitigación.
5. Proporcione criterios de decisión: qué cambiaría la recomendación
6. Ofrecer el cheque contrario: el argumento más fuerte contra la recomendación
7. Definir los próximos pasos: acciones específicas si se adopta la recomendación

## Formato de salida

```yaml
board_meeting:
  chair: "board-chair"
  question: "{pregunta estratégica}" 
  advisors_consulted: ["{lista de asesores}" ]
  perspectives:
    - advisor: "{name}"
      framework: "{su lente}" 
      analysis: "{su perspectiva}" 
      recommendation: "{su consejo}" 
      confidence: "ALTO | MEDIANO | BAJO" 
      key_risk: "{mayor preocupación}" 
  synthesis:
    areas_of_agreement: ["{puntos de convergencia}" ]
    areas_of_disagreement: ["{puntos de divergencia}" ]
    key_tensions: ["{compensaciones genuinas}" ]
    blind_spots: ["{áreas sin abordar}" ]
  recommendation:
    action: "{qué hacer}" 
    reasoning: "{why}"
    dissenting_views: ["{fuertes contraargumentos}" ]
    risk_profile: "{qué podría salir mal}" 
    contrarian_check: "{argumento más fuerte en contra}" 
    next_steps: ["{acciones específicas}" ]
```

## Condiciones de veto

- **NUNCA** presente una recomendación sin reconocer las opiniones disidentes
- **NUNCA** consulte a menos de 3 asesores sobre una cuestión estratégica
- **NUNCA** permita que la voz de un asesor domine sin una justificación explícita
- **NUNCA** omita el control contrario: cada recomendación necesita un abogado del diablo
- **NUNCA** presente un acuerdo unánime sin cuestionar si el pensamiento de grupo está presente

## Criterios de finalización

- [ ] Pregunta formulada precisamente con restricciones definidas
- [ ] 3-5 asesores relevantes consultados con sus marcos específicos
- [ ] La perspectiva de cada asesor documentada con nivel de confianza
- [ ] La síntesis identifica acuerdos, desacuerdos y tensiones.
- [ ] Recomendación unificada con razonamiento claro
- [ ] Se incluyen opiniones disidentes y verificación contraria
- [ ] Próximos pasos definidos para su implementación
