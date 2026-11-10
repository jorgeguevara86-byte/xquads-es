---
task: getFounderCounsel()
responsavel: "@board-chair"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: crossroads_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: founder_context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: founder_counsel
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Se entregaron las tres perspectivas de asesores (Sivers, Chouinard, Naval)" 
  - "[] Verificación contraria completada con minimización de arrepentimiento" 
  - "[] Marco de decisión ofrecido con mensaje de registro en diario" 
---

# Tarea: Abogado fundador de Crossroads

**ID de tarea:** BOARD-005
**Version:** 1.0.0
**Command:** `*get-founder-counsel`
**Agente:** El presidente de la junta directiva se dirige a Derek Sivers + Yvon Chouinard + Naval Ravikant
**Propósito:** Proporcionar sabiduría y perspectiva a los fundadores en los puntos críticos de decisión life/business .

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `crossroads_description` | La decisión o el dilema | SÍ |
| `founder_context` | Etapa, valores, situación personal | SÍ |
| `options_considered` | Caminos que se pesan | PREFERIDO |
| `fears_and_hopes` | A qué temen y qué quieren | PREFERIDO |
| `constraints` | No negociables, compromisos | NO |

## Preconditions

1. El fundador se enfrenta a una auténtica encrucijada (no es una decisión trivial)
2. Se encuentra disponible el contexto sobre la situación y valores del fundador.
3. Apertura a perspectivas no convencionales o contrarias

## Fases de Ejecución

### Fase 1: Encuadre la Encrucijada (board-chair)

1. Aclare la decisión en términos precisos: ¿qué se debe decidir exactamente?
2. Identificar el tipo de cruce:
   - **Iniciar vs Permanecer** — Deje la seguridad para el emprendimiento
   - **Crecer versus mantenerse pequeño**: ampliar o mantener un negocio de estilo de vida
   - **Vender vs Mantener** — Oferta de salida sobre la mesa
   - **Pivotar vs Persistir**: la ruta actual no funciona
   - **Solo vs Partner** — Ve solo o trae a co-founders/investors
   - **Burnout Crossroads** — Sigue adelante o da un paso atrás por motivos de salud
3. Mapee el panorama emocional: ¿qué miedos y esperanzas están impulsando la decisión?
4. Identifique suposiciones ocultas: ¿qué se da por sentado?
5. Ruta a los tres asesores founder-philosopher 

### Fase 2: Múltiples perspectivas

**Derek Sivers — Simplicidad contraria:**
1. Aplique la prueba "Diablos, sí o no". ¿Esta opción le hace decir "¡Diablos, sí!"?
2. Verifique el pensamiento convencional: ¿está haciendo esto porque "todo el mundo dice que debería hacerlo"?
3. Aplique el principio de "lo contrario también es cierto": ¿qué pasa si el camino opuesto es el correcto?
4. Evalúe la simplicidad: ¿qué opción es más sencilla? La complejidad suele ser una señal de advertencia
5. Considere el escenario "feliz de equivocarse": ¿en qué opción estaría más feliz de equivocarse?
6. Pregunta clave: "¿Qué harías si supieras que nadie te juzgará?"

**Yvon Chouinard — Sabiduría impulsada por la misión:**
1. ¿Esto se alinea con tus valores más profundos? (No son tus valores declarados, tus valores REALES)
2. ¿Cuál es el impacto ambiental y social de cada camino?
3. Aplique la lente de los 100 años: ¿de qué decisión estará orgulloso a muy largo plazo?
4. ¿Se trata de crecimiento o de calidad? (Chouinard siempre eligió la calidad)
5. ¿Puedes "dejar que mi gente vaya a surfear"? ¿Este camino permite una vida plena y equilibrada?
6. Pregunta clave: "¿Qué necesita el planeta (y tu comunidad) que hagas?"

**Ravikant naval — Sabiduría de los primeros principios:**
1. Aplique conocimientos específicos: ¿para qué está especialmente capacitado?
2. Evalúe el apalancamiento: ¿qué camino crea el mayor apalancamiento (código > medios > capital > mano de obra)?
3. Comprueba si estás jugando juegos de estatus: ¿estás persiguiendo estatus o creando riqueza?
4. Aplique la "prueba 40-year-old ": ¿qué camino conduce a la libertad y la paz a los 40, 50, 60?
5. Considere la posibilidad de capitalizar: ¿qué opción se compone mejor durante décadas?
6. Pregunta clave: "¿Qué camino te convierte en la versión más interesante y realizada de ti mismo?"

### Fase 3: Verificación contraria

1. Para cada camino, encuentre el argumento más fuerte EN CONTRA
2. Identificar qué miedos son legítimos y cuáles son ego-driven
3. Busque "esposas de oro": ¿la comodidad se hace pasar por sabiduría?
4. Aplica el "marco de minimización del arrepentimiento": a los 80 años, ¿qué elección te arrepentirás de NO haber tomado?
5. Prueba de reversibilidad: ¿es esta una puerta one-way o two-way ? (Las puertas de dos vías necesitan menos deliberación)
6. Pregunte: "¿Qué le aconsejarías a tu mejor amigo que hiciera en esta situación?"

### Fase 4: Marco de decisión

1. Sintetizar las tres perspectivas en una imagen coherente
2. Identifique la tensión central: ¿cuál es la verdadera compensación?
3. Presentar la decisión no como right/wrong sino como different-life-paths
4. Ofrecer un marco de decisión:
   - Si values-driven → apóyate en la lente de Chouinard
   - Si freedom-driven → apóyate en la lente de Naval
   - Si happiness-driven → apóyate en la lente de Sivers
5. Sugerir un pequeño experimento antes de comprometerse (si es posible)
6. Proporcionar un mensaje de diario para que el fundador lo procese antes de decidir
7. Recuerde: La decisión en sí importa menos que el compromiso de hacerla funcionar

## Formato de salida

```yaml
founder_counsel:
  advisors: [derek-sivers, yvon-chouinard, naval-ravikant]
  crossroads: "{description}"
  type: "{tipo de cruce}" 
  perspectives:
    sivers:
      hell_yeah_test: "{result}"
      contrarian_view: "{¿y si ocurre lo contrario?}" 
      key_insight: "{sabiduría central}" 
    chouinard:
      values_alignment: "{assessment}"
      long_term_lens: "{perspectiva de 100 años}" 
      key_insight: "{sabiduría central}" 
    naval:
      leverage_analysis: "{qué camino tiene más influencia}" 
      specific_knowledge: "{¿Para qué eres especialmente adecuado?}" 
      key_insight: "{sabiduría central}" 
  contrarian_check:
    strongest_argument_against: "{para cada ruta}" 
    regret_minimization: "{a los 80, ¿de qué te arrepentirías?}" 
    reversibility: "one-way | two-way"
  synthesis:
    core_tension: "{la verdadera compensación}" 
    framework: "{recomendación de lentes de decisión}" 
    experiment: "{pequeña prueba antes de comprometerse}" 
    journaling_prompt: "{para reflexión personal}" 
  closing_wisdom: "{Un mensaje personal sintetizado del foro}"
```

## Condiciones de veto

- **NUNCA** tome la decisión por el fundador: proporcione sabiduría, no directivas
- **NUNCA** descarte las preocupaciones emocionales como irracionales: los sentimientos son datos
- **NUNCA** avance hacia el éxito convencional si el fundador valora una vida no convencional
- **NUNCA** apresure la decisión: las encrucijadas merecen deliberación
- **NUNCA** ignore al ser humano detrás del negocio: la salud, las relaciones y la alegría son importantes

## Criterios de finalización

- [ ] Cruce claramente enmarcado con tipo identificado
- [ ] Las tres perspectivas de los asesores presentadas a través de sus lentes únicos
- [] Verificación contraria completada para cada ruta
- [ ] Se evalúa la minimización y reversibilidad del arrepentimiento
- [ ] Tensión central identificada y nombrada
- [ ] Se ofrece marco de decisión (no una directiva)
- [ ] Mensaje de diario o experimento sugerido para reflexión
