---
task: seekInvestmentCounsel()
responsavel: "@board-chair"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: opportunity_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: financial_data
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: false

Saida:
  - campo: investment_counsel
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Los tres análisis (Dalio, Munger, Thiel) completados" 
  - "[ ] Recomendación clara con términos o condiciones" 
  - "[ ] Criterios de eliminación y marco de seguimiento definidos" 
---

# Tarea: Sesión del Comité de Inversiones

**ID de tarea:** BOARD-002
**Version:** 1.0.0
**Command:** `*seek-investment-counsel`
**Agente:** El presidente de la junta directiva se dirige a Ray Dalio + Charlie Munger + Peter Thiel
**Propósito:** Evaluar una inversión o una decisión financiera importante a través de múltiples lentes analíticos.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `opportunity_description` | Mensaje de usuario | SÍ |
| `financial_data` | Ingresos, costes, proyecciones | PREFERIDO |
| `investment_amount` | Capital requerido | PREFERIDO |
| `market_context` | Industria, competencia, sincronización | PREFERIDO |
| `risk_appetite` | Conservador, moderado, agresivo | NO |
| `time_horizon` | Corto plazo, medio, long-term | NO |

## Preconditions

1. Se describe oportunidad de inversión o decisión financiera
2. Al menos un contexto financiero básico está disponible
3. Se comprenden las limitaciones y los valores de quien toma decisiones

## Fases de Ejecución

### Fase 1: Oportunidad presente (board-chair)

1. Enmarque la oportunidad en términos claros: ¿qué se está considerando?
2. Resumir los datos financieros y las proyecciones disponibles.
3. Identificar la decisión: invest/pass, monto, plazos, oportunidad
4. Mapear riesgos conocidos y desconocidos
5. Ruta al comité de inversiones: Dalio, Munger, Thiel

### Fase 2: Análisis de Riesgos

**Ray Dalio — Análisis basado en principios:**
1. Aplique una transparencia radical: ¿cuáles son las verdades incómodas?
2. Supuestos de las pruebas de resistencia: ¿qué pasa si las proyecciones están equivocadas en un 50%?
3. Evaluar el riesgo sistemático: ¿está esto correlacionado con factores macro?
4. Aplicar dolor + reflexión = progreso: ¿qué enseña la experiencia pasada?
5. Calcular el valor esperado: resultados de probability-weighted 
6. Verificar: ¿Se alinea esto con los principios de inversión establecidos?

**Charlie Munger — Análisis de modelos mentales:**
1. Aplicar inversión: ¿qué haría que esto fallara? Trabajar al revés desde el desastre
2. Verifique si hay sesgos cognitivos: sesgo de confirmación, FOMO, costos hundidos, anclaje
3. Evalúe el círculo de competencia: ¿realmente comprende este dominio?
4. Aplicar el efecto Lollapalooza: ¿se combinan múltiples fuerzas (a favor o en contra)?
5. Compruebe el foso: ¿cuál es la ventaja competitiva duradera?
6. Aplique la "prueba del periódico". ¿Estaría orgulloso de esta decisión en la portada?

**Peter Thiel — Análisis cero a uno:**
1. ¿Es esta una oportunidad 0-to-1 (crear algo nuevo) o 1-to-n (copiar)?
2. ¿Cuál es el secreto? ¿Qué crees que la mayoría de la gente no cree?
3. ¿Puede esto convertirse en un monopolio en un mercado pequeño antes de expandirse?
4. Aplique un optimismo definido: ¿existe un plan específico, no solo una esperanza?
5. Evalúe la ley de potencia: ¿podría ser un rendimiento de 100x o es incremental?
6. Verifique la ventaja del último en moverse: ¿será esta la solución definitiva?

### Fase 3: Aplicación de Modelos Mentales

1. Compile los tres análisis uno al lado del otro.
2. Identifique dónde coinciden los tres (señalhigh-confidence )
3. Identificar dónde no están de acuerdo (requiere un análisis más profundo)
4. Aplique el pensamiento second-order : ¿qué sucede DESPUÉS del primer movimiento?
5. Calcule la asimetría: ¿las ventajas son mucho mayores que las desventajas?
6. Ejecute el pre-mortem . Imagínese que falló, ¿cuál fue la causa?

### Fase 4: Recomendación

1. Sintetizar en una recomendación clara invest/pass/conditional 
2. Si invierte: términos, monto y condiciones recomendados
3. Si se aprueba: ¿qué habría que cambiar para reconsiderar?
4. Si es condicional: hitos específicos o información necesaria
5. Definir criterios de eliminación: qué desencadena la salida de la inversión
6. Proporcionar un marco de seguimiento: qué métricas seguir

## Formato de salida

```yaml
investment_counsel:
  opportunity: "{description}"
  committee: [ray-dalio, charlie-munger, peter-thiel]
  analyses:
    dalio:
      principles_assessment: "{analysis}"
      expected_value: "{calculation}"
      stress_test: "{peor caso}" 
      verdict: "INVERTIR | PASAR | CONDICIONAL" 
    munger:
      mental_models_applied: ["{modelos utilizados}" ]
      inversion_result: "{escenarios de falla}" 
      bias_check: ["{sesgos identificados}" ]
      verdict: "INVERTIR | PASAR | CONDICIONAL" 
    thiel:
      zero_to_one: "{¿Esto está creando algo nuevo?}" 
      monopoly_potential: "{assessment}"
      power_law_fit: "{¿podría ser esto un 100x?}" 
      verdict: "INVERTIR | PASAR | CONDICIONAL" 
  synthesis:
    agreement: ["{convergence}"]
    disagreement: ["{divergence}"]
    asymmetry: "{alcistas versus desventajas}" 
  recommendation:
    verdict: "INVERTIR | PASAR | CONDICIONAL" 
    terms: "{si invierte}" 
    conditions: "{si es condicional}" 
    kill_criteria: ["{activadores de salida}" ]
    monitoring: ["{métricas clave}" ]
```

## Condiciones de veto

- **NUNCA** recomiendo invertir sin supuestos de stress-testing 
- **NUNCA** omita el ejercicio de inversión; considere siempre cómo podría fallar
- **NUNCA** ignore los sesgos cognitivos en el análisis
- **NUNCA** lo recomiendo basándose únicamente en FOMO o prueba social
: **NUNCA** presente una recomendación sin definir criterios de eliminación

## Criterios de finalización

- [ ] Oportunidad enmarcada con datos financieros disponibles
- [] Análisis principles-based de Dalio completado con prueba de estrés
- [ ] Modelos mentales de Munger aplicados con inversión y verificación de sesgos
- [ ] Análisis de Thiel zero-to-one completado con evaluación de monopolio
- [ ] Análisis sintetizados con acuerdo y desacuerdo mapeados
- [ ] Recomendación clara con términos o condiciones
- [ ] Criterios de eliminación y marco de seguimiento definidos
