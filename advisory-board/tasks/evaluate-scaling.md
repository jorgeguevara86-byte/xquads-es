---
task: evaluateScaling()
responsavel: "@board-chair"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: business_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: scaling_trigger
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: scaling_evaluation
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Preparación evaluada por los tres asesores (Hoffman, Thiel, Naval)" 
  - "[ ] Estrategia de escalamiento identificada con una justificación clara" 
  - "[] Veredicto Go/No-Go con libro de jugadas y criterios de eliminación" 
---

# Tarea: Análisis de decisiones de escala

**ID de tarea:** BOARD-004
**Version:** 1.0.0
**Command:** `*evaluate-scaling`
**Agente:** El presidente de la junta directiva se dirige a Reid Hoffman + Peter Thiel + Naval Ravikant
**Propósito:** Evaluar si y cómo escalar un negocio, producto o equipo.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `business_description` | Estado actual del negocio | SÍ |
| `scaling_trigger` | Por qué se está considerando ahora la ampliación | SÍ |
| `current_metrics` | Ingresos, usuarios, tasa de crecimiento, economía unitaria | PREFERIDO |
| `resources_available` | Capital, equipo, infraestructura | PREFERIDO |
| `market_context` | Tamaño del mercado, competencia, calendario | NO |
| `constraints` | Limitaciones, valores, non-negotiables | NO |

## Preconditions

1. La empresa tiene algún tipo de ajuste product-market (o cree que lo tiene)
2. El escalamiento se está considerando activamente como un movimiento estratégico
3. Métricas básicas o datos de tracción disponibles.

## Fases de Ejecución

### Fase 1: Evaluar la preparación

**Reid Hoffman — Preparación para escalar Blitz:**
1. ¿Existe un mercado grande y en crecimiento? (análisis TAM)
2. ¿Se ajusta product-market ? (retención, referencia, crecimiento orgánico)
3. ¿Hay efectos de red? (¿El producto mejora con más usuarios?)
4. ¿Tiene ventaja de distribución? (¿viral, integrado, pago escalable?)
5. ¿Existe alguna ventaja sobre el first-scaler ? (¿Dinámicawinner-take-most ?)
6. Califique la preparación para blitzscaling: NO LISTO / ACERCANDO / LISTO / VENCIDO

**Peter Thiel — Evaluación de monopolio:**
1. ¿Domina un mercado pequeño? (Deberías ser el número 1 o 2 en un nicho)
2. ¿Cuál es tu secreto? (¿Qué sabes tú que otros no saben?)
3. ¿Se puede lograr el monopolio en un espacio definido?
4. ¿Su tecnología es 10 veces mejor (no sólo de forma incremental)?
5. ¿Está creando tecnología propia, efectos de red, economías de escala o marca?
6. Potencial de monopolio tarifario: DÉBIL / MODERADO / FUERTE

**Ravikant naval — Análisis de apalancamiento:**
1. ¿Está aplicando apalancamiento? (Código, medios, capital, trabajo, en ese orden de preferencia)
2. ¿Tiene conocimientos específicos? (Algo que el mercado no puede replicar fácilmente)
3. ¿Está creando activos que generan ganancias mientras duerme?
4. ¿Es esta una oportunidad compuesta? (¿Cada unidad de esfuerzo se basa en la anterior?)
5. ¿Cuál es la estructura de rendición de cuentas? (¿Quién tiene piel en el juego?)
6. Posición de apalancamiento de tipos: BAJA / MEDIA / ALTA

### Fase 2: Identificar la estrategia de escalamiento

1. **Velocidad versus eficiencia**: ¿Debería priorizar la velocidad de crecimiento o la economía unitaria?
   - Hoffman: Velocidad cuando el mercado es winner-take-most
   - Thiel: Eficiencia a la hora de construir un monopolio en un nicho
   - Naval: Aproveche cuando puede escalar sin esfuerzo proporcional
2. **Horizontal versus vertical**: ¿Ampliar la amplitud (más mercados) o la profundidad (más valor)?
3. **Orgánico vs Inorgánico**: ¿Crecer internamente o a través de acquisition/partnership?
4. **Estrategia de capital**: ¿iniciar, aumentar el riesgo o crecimiento de revenue-fund ?
5. Mapee la secuencia de escalamiento: lo que debe ser cierto en cada etapa

### Fase 3: Evaluación de riesgos

1. **Riesgos de escalamiento prematuro**: escalar antes de que product-market encaje es el asesino número uno de las startups
2. **Riesgo de ejecución**: ¿puede su equipo manejar una complejidad 10 veces mayor?
3. **Riesgo cultural**: ¿El rápido crecimiento destruirá su cultura? (Fase de "extinción de incendios" de Hoffman)
4. **Riesgo financiero**: ¿Cuál es la tasa de consumo durante el escalado? ¿Pista?
5. **Riesgo de mercado**: ¿Es el momento adecuado? ¿Podría cerrarse la ventana?
6. **Riesgo competitivo**: ¿La ampliación provocará represalias por parte de los titulares?
7. Aplique la prueba de optimismo definitivo de Thiel: ¿tiene un plan específico, no sólo una esperanza?

### Fase 4: Recomendación Go/No-Go 

1. Sintetizar la preparación, la estrategia y las evaluaciones de riesgos
2. Dar un veredicto claro:
   - **GO — Escalar ahora** — El momento del mercado, la preparación y los recursos se alinean
   - **CONDITIONAL GO**: escale después de que se cumplan condiciones específicas (enumérelas)
   - **NO-GO - No listo** - Especifique qué debe cambiar antes de reconsiderar
   - **PIVOT**: escalar el enfoque actual es incorrecto; redirigir primero
3. Si GO: Defina el manual de escalamiento (primeros 90 días, 6 meses, 12 meses)
4. Definir métricas de éxito y puntos de control en cada etapa.
5. Establezca criterios de eliminación: qué le haría dejar de escalar y reevaluar

## Formato de salida

```yaml
scaling_evaluation:
  advisors: [reid-hoffman, peter-thiel, naval-ravikant]
  readiness:
    hoffman_blitzscaling: "NO_LISTO | ACERCANDO | LISTO | VENCIDO" 
    thiel_monopoly: "DÉBIL | MODERADO | FUERTE" 
    naval_leverage: "BAJO | MEDIANO | ALTA" 
  strategy:
    approach: "velocidad | eficiencia | apalancamiento" 
    direction: "horizontales | vertical" 
    growth_type: "orgánico | inorgánico | híbrido" 
    capital_strategy: "arranque | emprendimiento | revenue-funded" 
  risks:
    premature_scaling: "{assessment}"
    execution: "{assessment}"
    culture: "{assessment}"
    financial: "{assessment}"
    market: "{assessment}"
    competitive: "{assessment}"
  verdict: "IR | CONDICIONAL_GO | NO_GO | PIVOTE" 
  conditions: ["{si es condicional}" ]
  playbook:
    days_90: ["{primeras acciones}" ]
    months_6: ["{medium-term actions}"]
    months_12: ["{long-term actions}"]
  success_metrics: ["{qué medir}" ]
  kill_criteria: ["{cuándo parar}" ]
```

## Condiciones de veto

- **NUNCA** recomendamos realizar un escalado sin evidencia de ajuste del product-market 
- **NUNCA** ignore la economía unitaria: el crecimiento sin márgenes es simplemente un fracaso costoso
- **NUNCA** recomiendo blitzscaling cuando no hay ventaja first-scaler 
- **NUNCA** omita la evaluación de riesgos: el exceso de confianza mata a más empresas que la competencia
- **NUNCA** recomiendo escalar si entra en conflicto con los valores fundamentales del fundador (pregunte primero)

## Criterios de finalización

- [ ] Se evaluó la preparación para Blitzscaling (Hoffman)
- [ ] Potencial de monopolio evaluado (Thiel)
- [ ] Posición de apalancamiento analizada (Naval)
- [ ] Estrategia de escalamiento identificada con una justificación clara
- [ ] Evaluación de riesgos completada en todas las dimensiones
- [] Borrar veredicto Go/No-Go con razonamiento
- [] Playbook definido con métricas y criterios de eliminación
