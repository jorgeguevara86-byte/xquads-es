---
task: manageBudget()
responsavel: "@fiscal"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: total_budget
    tipo: number
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: campaign_data
    tipo: object
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: budgetOptimization
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Asignación actual mapeada con ROAS marginal" 
  - "[ ] 3 escenarios presupuestarios modelados con proyecciones" 
  - "[ ] Plan de reasignación gradual durante 1-2 semanas" 
---

# Task: Gestion Budget

** ID de la lista:** TRAFFIC-007
**Version:** 1.0.0
**Command:** `*manage-budget`
**Agente:** Impuestos (fiscales)
**Purpose:** Optimize budget allocation across campaigns, platforms, and funnel stages.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| total_budget Silencio número Silencio Usuario prompt Silencio Sí Silencio Total mensual ad budget Silencio
Silencio plataformas Silenciosos lista Silenciosos de usuario incitados Sí Silencio Plataformas activas con la asignación actual Silencio
| campaign_data Silencioso objeto Silencioso de usuario incitar a su usuario Sí Silencioso de la campaña (hablando, CPA, ROAS, conversiones) TEN
| revenue_target Silencio número Silencio Usuario prompt Silencio No Silencio Objetivos de ingresos mensuales Silencio
| max_cpa Silencio número Silencio Usuario prompt Silencio No Silencio Maximum acceptable CPA Silencio
| min_roas Silencio número Silencio Usuario prompt Silencio No Silencio mínima aceptable ROAS Silencio
| growth_mode TEN enum TENIDO Usuario prompt TEN No TEN mantener, crecer, agresivo — defaults to grow TEN

---

## Preconditions

- Al menos 30 días de datos sobre el desempeño de la campaña
- Múltiples campañas o plataformas para asignar entre
- Objetivos claros de la KPI definidos

---

## Fases de Ejecución

### Phase 1: Current Allocation Analysis
1. Distribución de los gastos corrientes de mapa:
   - Por plataforma
   - Por campaña
   - En estadio de embudo (FTA, MOF, BOF)
2. Calcular el ROAS marginal por campaña (el retorno del último dólar gastado)
3. Identificar los rendimientos que disminuyen, ¿dónde está el gasto más no producir más?
4. Calcular el gasto desperdiciado (campañas por debajo del umbral mínimo de ROAS)
5. Evaluar la utilización del presupuesto (¿están las campañas gastando sus presupuestos completos?)

### Fase 2: Optimización de la modelación
1. Efectivamente todas las campañas:
   - CPA-ranked (lowest CPA first)
   - ROAS (la más alta ROAS primero)
   - Rancho de volumen (la mayoría de conversiones primero)
2. Aplicar el principio de optimización de cartera:
   - Asignar incrementalmente a la highest-returning campaña
   - Hasta que el regreso marginal de esa campaña sea igual a la siguiente mejor opción
   - Continuar hasta que se asignen todos los presupuestos o se alcancen umbrales mínimos
3. Modelo 3 hipótesis presupuestarias:
   - Conservador: Mantener ROAS, maximizar el beneficio
   - Crecimiento: Aceptar 10-20% de aumento de CPA para volumen
   - Agresivo: Aceptar 30-50% de aumento de CPA para la escala máxima
4. Cálculo de los resultados previstos para cada escenario

## Fase 3: Plan de Realización
1. Definir el cambio presupuestario:
   - De: Campañas que pierden presupuesto (con análisis de impacto)
   - A: Campañas que ganan presupuesto (con beneficio proyectado)
2. Fase de la reasignación durante 1-2 semanas (no de la noche a la mañana):
   - Semana 1: 50% del turno (monitor para la perturbación)
   - Semana 2: Permaneciendo el 50% (si Semana 1 estable)
3. Establecer corresponsales para la transición:
   - Cambio de presupuesto diario por campaña
   - umbrales de vigilancia del CPA durante la transición
   - Rollback dispara si el rendimiento se degrada
4. Cuenta para las fases de aprendizaje de plataformas durante los cambios presupuestarios

### Fase 4: Marco de Gestión en curso
1. Definir la cadencia del examen del presupuesto:
   - Diario: Revisar el pacto de la pasada (en el plan de la pista vs?)
   - Semanal: examen de la ejecución y ajustes menores
   - Mensual: Revisión completa de la reasignación
2. Establecer reglas automatizadas cuando sea posible:
   - Pausa ad set si CPA supera X por 3 días consecutivos
   - Aumentar el presupuesto 15% si el CPA se encuentra por debajo de la meta durante 7 días consecutivos
   - Alerta si el gasto diario se desvía más del 20% del plan
3. Crear la plantilla de informe del presupuesto mensual
4. Planifique el presupuesto del próximo trimestre basado en las tendencias de rendimiento

---

## Formato de salida

```markdown
## Budget Optimization: {Business/Account}

**Total Budget:** ${X}/month
**Current ROAS:** {X}:1
**Target ROAS:** {X}:1
**Growth Mode:** {mode}

---

### Current Allocation

| Campaign/Platform | Monthly Spend | CPA | ROAS | Marginal ROAS | Status |
|-------------------|--------------|-----|------|---------------|--------|

**Wasted Spend:** ${X}/month on underperformers
**Underutilized:** ${X}/month budget not being spent

### Scenario Modeling

| Scenario | Budget | Projected CPA | Projected ROAS | Projected Revenue |
|----------|--------|--------------|----------------|------------------|
| Conservative | ${X} | ${X} | {X}:1 | ${X} |
| Growth | ${X} | ${X} | {X}:1 | ${X} |
| Aggressive | ${X} | ${X} | {X}:1 | ${X} |

### Recommended Reallocation

| Campaign | Current | New | Change | Rationale |
|----------|---------|-----|--------|-----------|

### Transition Plan
| Week | Action | Monitor |
|------|--------|---------|

### Automated Rules
| Rule | Trigger | Action |
|------|---------|--------|

### Monthly Review Template
{Template for ongoing budget management}
```

---

## Condiciones de veto

- Nunca reasignar el 100% del presupuesto en un solo día - fases de aprendizaje requieren cambios graduales
- Nunca cortó una campaña rentable a cero sin confirmación - reducir primero, monitor, luego decidir
- Nunca asignar basado en los ingresos por sí solos - considerar el margen de ganancia (ROAS vs CPA)
- NUNCA ignora los impactos de la fase de aprendizaje de plataformas al cambiar el presupuesto
- Nunca establecer reglas automatizadas sin kill-switch umbrales

---

## Criterios de finalización

- [ ] La asignación actual mapeada con ROAS marginal
- [ ] Gasto desperdiciado y subutilizado identificado
- 3 escenarios presupuestarios modelados con proyecciones
- Plan de reasignación gradual durante 1-2 semanas
- [ ] Guardias y disparadores de revolvimiento definidos
- [ ] Reglas automatizadas configuradas
- [ ] Cadencia y plantilla de revisión mensual
