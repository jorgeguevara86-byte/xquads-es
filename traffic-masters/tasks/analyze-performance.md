---
task: analyzePerformance()
responsavel: "@performance-analyst"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: metrics
    tipo: object
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: performanceAnalysis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] métricas básicas calculadas y presentadas" 
  - "[ ] 80/20 análisis realizados" 
  - "[ ] Plan de acción de 7 días creado" 
---

# Task: Analyze Performance

** ID de la lista:** TRAFFIC-006
**Version:** 1.0.0
**Command:** `*analyze-performance`
**Agente:** Analista de Desempeño (Analizador de Desempeño)performance-analyst)
**Purpose:** Análisis de resultados profundos de campañas publicitarias data-driven recomendaciones.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencio, plataforma, Silencio, insinuación de usuario Silencio, vida, vida, vida, vida, vida, vida
TENCIÓN TERRITORIO TENIDO objeto TENIDO Usuario prompt TENIS TERRITORIO DE LA Campaña: gasto, impresiones, clics, conversiones, ingresos TENIDO
| time_period Silencio Silencio Silencio Silencio Usuario prompt Silencio Silencioso ventana Análisis (7d, 14d, 30d, 90d) Silencio
| comparison_period Silencio Silencio Silencio Silencio Usuario prompt Silencio No Silencio Período anterior para el análisis de tendencias Silencio
Silenciosidad incompleto Silenciosidad intuitiva No Silencio Solicitado desglose: campaña, ad-set, ad, audiencia, colocación ←
| business_context TENTER SON TENIDO ANTERIOR NO TENIDO Estacionalidad, promociones o factores externos TEN

---

## Preconditions

- Mínimo 7 días de datos para un análisis significativo
- Seguimiento de conversiones verificados y precisos
- Al menos un negocio claro definido por KPI (CPA, ROAS, CPL)

---

## Fases de Ejecución

### Fase 1: Computación métrica
1. Calcule las métricas centrales de datos brutos:
   - CPC (Cost Per Click) = Paso / Clic
   - CTR (Tasa de clics) = Clics / impresiones
   - CVR (tasa de conversión) = Conversiones / Clics
   - CPA (Cost Per Acquisition) = Gasto / Conversiones
   - ROAS (Regreso al Paso de Anuncio) = Ingreso / Gasto
   - CPM (Cost Per 1000 Impresiones) = (Spend / Impresiones) x 1000
   - Frecuencia = Impresiones / Alcance
2. Cálculo period-over-period cambios si se dispone de datos de comparación
3. Determinar cambios estadísticamente significativos frente a la diferencia normal
4. anomalías de la bandera (puntos o gotas endobladas)

### Fase 2: Desintegración de rendimiento
1. Descomponer el rendimiento por la dimensión solicitada:
   - Por Campaña: ¿Qué campañas impulsan el mayor valor?
   - Por Ad Set: ¿Qué audiencias convierte mejor?
   - ¿Qué creativos realizan?
   - Por Lugar: ¿Dónde funciona mejor el anuncio?
   - Por Day/Hour: ¿Cuándo es el rendimiento más fuerte?
2. Aplicar el 80/20 análisis: ¿qué 20% de los elementos impulsan el 80% de los resultados?
3. Identificar el 20% inferior arrastrando el rendimiento
4. Calcular el impacto de la eliminación de los infravalores

## Fase 3: Análisis de tendencias
1. Coloque las métricas clave durante el período de análisis:
   - tendencia de la CPA: estable, creciente o declinante?
   - ROAS: ¿mejoramiento o degradante?
   - Tendencia CTR: ¿Señal de fatiga creativa?
   - Tendencia: ¿extracto de la audiencia?
2. Identificar puntos de inflexión — ¿cuándo cambió el rendimiento?
3. Correlaciona los cambios con eventos conocidos (lanzamientos creativos, cambios presupuestarios, factores externos)
4. Proyecto de futuro: ¿dónde irán estas tendencias en los próximos 14-30 días?

### Fase 4: Insights Actionable
1. Resumir los 3 resultados más importantes
2. Para cada conclusión, proporcione:
   - ¿Qué pasó?data-backed observación)
   - Por qué importa (incidencia empresarial)
   - Qué hacer al respecto (acción específica)
3. Priorizar las medidas mediante los efectos previstos
4. Crear un plan de acción de 7 días
5. Defina qué monitorear para el próximo período de análisis

---

## Formato de salida

```markdown
## Performance Analysis: {Platform/Campaign}

**Period:** {dates}
**Total Spend:** ${X}
**Total Revenue:** ${X}
**ROAS:** {X}:1
**CPA:** ${X}
**Trend:** {improving / stable / declining}

---

### Key Metrics Summary

| Metric | Current | Previous | Change | Status |
|--------|---------|----------|--------|--------|
| Spend | ${X} | ${X} | {+/-X%} | {OK/Watch/Alert} |
| Revenue | ${X} | ${X} | {+/-X%} | {OK/Watch/Alert} |
| ROAS | {X}:1 | {X}:1 | {+/-X%} | {OK/Watch/Alert} |
| CPA | ${X} | ${X} | {+/-X%} | {OK/Watch/Alert} |
| CTR | {X}% | {X}% | {+/-X%} | {OK/Watch/Alert} |
| CVR | {X}% | {X}% | {+/-X%} | {OK/Watch/Alert} |

### 80/20 Analysis
**Top 20% drivers:** {list with metrics}
**Bottom 20% drags:** {list with metrics}
**Impact of cutting bottom 20%:** +${X} saved, ROAS improves to {X}:1

### Trend Analysis
{Trend descriptions with inflection points and projections}

### Top 3 Insights

#### Insight 1: {Title}
**What:** {observation}
**Why it matters:** {impact}
**Action:** {recommendation}

#### Insight 2-3: ...

### 7-Day Action Plan
| Day | Action | Expected Impact |
|-----|--------|----------------|

### Monitor Next Period
| Metric | Watch For | Threshold |
|--------|-----------|-----------|
```

---

## Condiciones de veto

- Nunca se analizan menos de 7 días de datos: ventanas cortas son ruido, no señal
- NUNCA presentan métricas sin contexto (marcas, tendencias o períodos de comparación)
- NUNCA sacar conclusiones de datos estadísticamente insignificantes (grupos de anuncios de volumen bajo)
- Nunca proporcionar información sin recomendaciones específicas y factibles
- NUNCA ignorar factores externos (temporalidad, promociones, eventos de mercado)

---

## Criterios de finalización

- [ ] métricas básicas calculadas y presentadas
- [ ] Período...over-period comparación completada (si se dispone de datos)
- [ ] 80/20 análisis realizados
Análisis de tendencias con puntos de inflexión
- [ ] Top 3 ideas con data-backed Observaciones
- [ ] Plan de acción de 7 días creado
- [ ] Marco de vigilancia para el próximo período definido
