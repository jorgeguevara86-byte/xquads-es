---
task: analyzeStory()
responsavel: "@shawn-coyne"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: story_text
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: intended_genre
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: false

Saida:
  - campo: story_analysis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Genre identificado con el valor básico y escenas obligatorias" 
  - "[ ] Todas las escenas mapeadas con puntos de giro y cambios de valor" 
  - "[ ] Problemas diagnosticados y priorizados con recetas" 
---

# Task: Story Analysis (Story Grid)

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*analyze-story`
*Agente* *Shawn Coyne (*)shawn-coyne)
**Purpose:** Analizar una historia usando la metodología Story Grid para diagnosticar problemas estructurales y emocionales.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `story_text` TENIDO El usuario proporciona borrador, contorno o descripción TENIDO TENIDO
| `intended_genre` Silencio vocacional vocablo viv 
| `target_audience` Silencio descripción de usuario Silencio
| `specific_concerns` Silencio Lo que el autor piensa es incorrecto TENIDO NO TENIDO
| `story_format` TEN NOVIA, guión, cuento corto, episodio TENIDO NO TENIDO

## Preconditions

1. Existe material de historia (proyecto completo, borrador parcial o esquema detallado)
2. Contenido suficiente para identificar convenciones de género y patrones estructurales
3. Información sobre el marco de Story Grid es accesible

## Fases de Ejecución

### Phase 1: identify Genre

1. Determinar el género de contenido — Acción, horror, amor, rendimiento, sociedad, condición, visión del mundo
2. Identificar el sub-genre - cada género tiene convenciones específicas
3. Mapear el valor básico en juego:
   - Action: Life/Death
   - Horror: Life/Damnation
   - Love: Love/Hate
   - Performance: Respect/Shame
   - Society: Power/Impotence
   - Status: Success/Failure
   - Worldview: Meaning/Meaninglessness
4. Listar las escenas obligatorias para este género (lo que debe suceder)
5. Listar las convenciones para este género (lo que espera el público)
6. Verificar: ¿El género destinado al autor coincide con lo que la historia realmente entrega?

### Fase 2: Escenas de mapa

1. Romper la historia en escenas (unidades de acción con un cambio de valor)
2. Para cada escena, identifique:
   - **Punto de inicio** - ¿Qué cambios hay dentro de la escena?
   - ** Cambio de valor** - ¿Qué valor se mueve de positivo a negativo o viceversa?
   - ** Cambio de la polaridad** - por ejemplo, Vida (+) a la Inconsciencia (-)
   **Tipo de evento de la historia** - Punto de inflexión activo o revelador
3. Crear la hoja de cálculo de la historia de la Grid — scene-by-scene análisis
4. Mapear el arco de valor global - ¿Se mueve de negativo a positivo (prescriptivo) o positivo a negativo (caucionario)?
5. Identificar los cinco mandamientos clave por escena: Incitar al Incident, Complicación Progresiva, Crisis, Climax, Resolución

### Fase 3: Evaluar los puntos de giro

1. **Empieza el gancho** - ¿El incidente incitante engancha al lector? ¿Es el primer punto de inflexión convincente?
2. **Middle Build** — ¿Las complicaciones se intensifican progresivamente? ¿Hay un cambio de punto medio? ¿Las apuestas suben continuamente?
3. **Ending Payoff** — ¿El climax es satisfactorio? ¿La resolución cumple la promesa de la historia? ¿Se gana la transformación?
4. Evaluar la crisis global — es el dilema del protagonista un verdadero best-bad-choice o irreconcilable-goods?
5. Compruebe las escenas obligatorias — son todas genre-required escenas presentes y funcionales?
6. Consultar convenciones — ¿la historia entrega lo que espera el público de género?

### Fase 4: Diagnostique Issues

1. Identificar las brechas estructurales — los latidos perdidos, la escalada saltada, los giros sin entonar
2. Identificar fallos de género — escenas obligatorias perdidas, convenciones rotas
3. Identificar fallas emocionales — cambios de valor que no aterrizan, puntos de giro planos
4. Identificar problemas de pacificación: media saliente, final precipitado, apertura lenta
5. Priorizar cuestiones: Critical (story does not work without fixing)  Confes Mayor (significantly weakens)  Confes Menor (polish-level)
6. Proporcionar recetas específicas: qué cambiar, añadir, eliminar o reestructurar
7. Masters de género de referencia - ejemplos de cómo las historias similares solucionan estos problemas

## Formato de salida

```yaml
story_analysis:
  analyst: "shawn-coyne"
  methodology: "Historia Grid" 
  genre:
    content_genre: "{genre}"
    sub_genre: "{sub-genre}"
    core_value: "{valor en juego}" 
    obligatory_scenes_present: ["{escenas encontradas}" ]
    obligatory_scenes_missing: ["{escenas desaparecidas}" ]
    conventions_met: ["{convenciones encontradas}" ]
    conventions_violated: ["{convenciones rotas}" ]
  scene_map:
    total_scenes: 0
    value_arc: "prescriptivo TENGA" 
    key_scenes:
      - scene: "{nombre de escena}" 
        turning_point: "¿Qué cambia?" 
        value_shift: "{de → a}" 
        commandments: "{5 mandamientos evaluación}" 
  structure_assessment:
    beginning_hook: "{assessment}"
    middle_build: "{assessment}"
    ending_payoff: "{assessment}"
    global_crisis: "{assessment}"
  diagnosis:
    critical_issues: ["{Debe arreglarlo}" ]
    major_issues: ["{debería arreglarlo}" ]
    minor_issues: ["{nice to fix}" ]
  prescriptions: ["{recomendaciones específicas}" ]
```

## Condiciones de veto

- **NUNCA** analiza sin identificar primero el género - género determina las expectativas
* * * NUNCA* proporciona comentarios vagos como "necesita más tensión" — ser específico y prescriptivo
- ###############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
- ** NUNCA** juzgar una historia por un marco que no coincide con su género
- **Nunca** olvidar que cada escena debe tener un cambio de valor - escenas sin cambio no son escenas

## Criterios de finalización

Genre identificada con el valor básico y escenas obligatorias
- [ ] Todas las escenas mapeadas con puntos de giro y cambios de valor
- Cinco mandamientos evaluados para escenas clave
- [ ] Inicio de gancho, construcción media y finalización de pago evaluado
- [ ] Problemas estructurales, de género, emocionales y de pacificación diagnosticados
Cuestiones prioritarias (Critical  Confes Mayor √° menor)
- [ ] Requisitos específicos para cada cuestión
