---
task: measureImpact()
responsavel: "@analista-de-impacto"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: movement_context
    tipo: string
    origem: Session
    obrigatorio: true
  - campo: goals
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: impact_framework
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Pirámide de impacto definida con 5 niveles" 
  - "[ ] fórmula del índice de vitalidad definida con pesos" 
  - "[ ] Cadencia de presentación de informes establecido" 
---

# Task: Measure Impact

** ID de la lista:** MOVIMIENTO-005
**Version:** 1.0.0
**Command:** `*measure-impact`
**Agente:** Analista de Impacto (Analizador de Impacto)analista-de-impacto)
**Purpose:** Diseñar e implementar un marco de medición de impacto completo con métricas, tableros de control y puntuación de vitalidad

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `movement_context` Silencio Silencio Silencio Sí Silencio Causa, identidad y estrategia de crecimiento Silencioso
| `growth_data` | estrategista-de-ciclo TENED No TENIDO métricas de crecimiento y datos comunitarios existentes
| `goals` Silencio invocar usuario Silencio Silencio Qué impacto tiene el movimiento para lograr Silencio
| `timeframe` Silencio Usuario Silencio No Silencio Periodo de medición: mensual, trimestral, anual Silencio
| `existing_metrics` TENIDO Usuario TENIDO No TEN cualquier métrica ya siendo rastreada TENCIÓN

## Preconditions

- Identidad de movimiento definida (al mínimo, creencias básicas y audiencia)
- La estrategia de crecimiento existe o está en marcha
- Marcos de movimiento cargados (`data/movement-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Define Impact Pyramid

1. Mapear los 5 niveles de la pirámide de impacto:
   *Nivel 1 – Sensibilización* *La gente sabe que el movimiento existe
   *Nivel 2 - Participación** La gente interactúa con el movimiento
   *Nivel 3 -- Compromiso**: La gente se identifica como miembros
   *Nivel 4 - Promoción**: Los miembros reclutan a otros
   *Nivel 5 – Transformación*:* El cambio del mundo real ocurre
2. Para cada nivel, definir cómo es el "éxito" para este movimiento específico
3. Identificar el **current nivel** - ¿Dónde está el movimiento hoy
4. Conjunto **target nivel** para el próximo ciclo
5. Dependencias de mapas entre los niveles

### Fase 2: Establecer métricas por nivel

1. Para cada nivel de pirámide, definir:
   * Indicadores de envío* - señales predictivas
   ** Indicadores de retraso** - resultados confirmados
   - **Marcos cualitativos** - evidencia narrativa
2. Seleccione **3-5 métricas por nivel** (no más, para evitar la sobrecarga métrica)
3. Definir los métodos de medición para cada métrica
4. Establecer bases de referencia y metas
5. Crear el **metrics matriz** - nivel x método métrico x objetivo

### Phase 3: Measure Community Health

1. Diseñar el **Calizaje de Salud Comunitaria** con 6 dimensiones:
   ** Tasa de crecimiento** - nuevos miembros por período
   ** Tasa de actividad** - Porcentaje de nuevos miembros que participan en un plazo de 7 días
   ** Tasa de retención** - % todavía activa después 30/60/90 días
   ** Profundidad de la participación** - interacciones promedio por miembro activo
   - **La puntuación de la sensibilidad** - positive/negative/neutral ratio sentimental
   ** Tasa de promoción** - Porcentaje de miembros que reclutan a otros
2. Definir los métodos de reunión de datos para cada dimensión
3. Establecer rangos saludables para cada dimensión (green/yellow/red)
4. Diseño de la **weekly Pulsera de informe**
5. Diseño de la **monthly deep-dive** Plantilla de informe

### Fase 4: Calcular índice de vitality

1. Definir la fórmula ** Índice de la Vitalidad**:
   - Composite de peso de las 6 dimensiones de salud
   - Pesos predeterminados: Crecimiento (15%), Activación (20%), Retención (25%), Ingerencia (20%), Sentencia (10%), Promoción (10%)
   - Scale: 0-100
2. Conjunto **vitality umbrales**:
   - 80-100: Conducir - mantener y optimizar
   - 60-79: ajustes menores saludables necesarios
   - 40-59: En riesgo - intervención necesaria
   - 20-39: crítico - importante pivote necesario
   - 0-19: Failing - revisión existencial requerida
3. Crear el **reporting cadencia**:
   - Semanal: Pulso del índice de vitalidad + 3 indicadores principales
   - Mensual: Panel completo + análisis de tendencias + recomendaciones
   - Trimestralmente: Repaso de la pirámide de impacto + ajuste de estrategia
4. Definir **alert dispara** -- cuándo escalar para movement-chief

## Formato de salida

```yaml
impact_framework:
  movement: "{name}"
  current_pyramid_level: {1-5}
  target_pyramid_level: {1-5}
  metrics_per_level:
    awareness: ["{metric1}", "{metric2}", "{metric3}"]
    engagement: ["{metric1}", "{metric2}", "{metric3}"]
    commitment: ["{metric1}", "{metric2}", "{metric3}"]
    advocacy: ["{metric1}", "{metric2}", "{metric3}"]
    transformation: ["{metric1}", "{metric2}", "{metric3}"]
  community_health:
    growth_rate: {baseline: "", target: "", status: ""}
    activation_rate: {baseline: "", target: "", status: ""}
    retention_rate: {baseline: "", target: "", status: ""}
    engagement_depth: {baseline: "", target: "", status: ""}
    sentiment_score: {baseline: "", target: "", status: ""}
    advocacy_rate: {baseline: "", target: "", status: ""}
  vitality_index:
    current_score: {0-100}
    threshold: "{Conduciendo la vida sanaat-riskSilencios morales" 
    weights: {growth: 15, activation: 20, retention: 25, engagement: 20, sentiment: 10, advocacy: 10}
  reporting_cadence:
    weekly: "Pulso de vibración + indicadores de liderazgo" 
    monthly: "Full dashboard + tendencias + recomendaciones" 
    quarterly: "Repaso de la pirámide de impacto + ajuste de estrategia" 
  alert_triggers:
    - "{condición que desencadena escalada}" 
```

## Condiciones de veto

1. **Nunca defina más de 5 métricas por nivel de pirámide** - la sobrecarga métrica paraliza la acción
2. **Nunca saltar marcadores cualitativos** - los números por sí solos pierden la dimensión humana de los movimientos
3. **Nunca fijar objetivos sin bases de referencia** - los objetivos sin contexto son fantasías
4. **NUNCA informe Índice de Vitalidad sin contexto** - una puntuación sin tendencia y recomendaciones es ruidosa
5. **Nunca ignore los datos de sentimientos** - una comunidad creciente pero infeliz es una bomba de tiempo

## Criterios de finalización

- [ ] Pirámide de impacto definida con 5 niveles personalizados al movimiento
- Matriz de medición completa con 3-5 métricas por nivel
- [ ] Comunitario de salud Panel diseñado con 6 dimensiones
- [ ] fórmula del índice de vitalidad definida con pesos y umbrales
- [ ] Cadencia de presentación de informes establecida (semana, mensual, trimestral)
- [ ] Detonantes de alerta definidos para escalada
- [ ] Estado actual evaluado con mediciones de referencia
- [ ] La salida coincide con el esquema anterior
