---
task: analyzeData()
responsavel: "@avinash-kaushik"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: business
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: channels
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: analytics_framework
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] DMMM aplicado con objetivos, metas, KPIs, objetivos" 
  - "[ ] OMTM identificado" 
  - "[ ] Panel de mando diseñado con la fila de Acciones" 
---

# Task: Analyze Data

** ID de usuario**
**Version:** 1.0.0
**Command:** `*analyze-data`
*Agent:* Avinash Kaushik (Avenash Kaushik)avinash-kaushik)
**Purpose:** Diseño de marcos de análisis y paneles usando el Modelo de Marketing y Medición Digital (DMMM)

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `business` Silencio invocar a su usuario Silencio Silencioso descripción de su negocio y objetivos
| `channels` Silencio Insinuación del usuario Silencio Sí Silencio Canales digitales activos (web, social, email, etc.) Silencio
| `current_tracking` TENIDO Usuario TENIDO No TENIDO Herramientas de análisis existentes y lo que se rastrea hoy TENIDO
| `audience_segments` ← Usuario Silencio No Silencio Populares segmentos de audiencia
| `stage` TENIDO Usuario TENIDO No TENIDO Etapa de Negocios: pre-launch, crecimiento, madura Silencio

## Preconditions

- Objetivos empresariales definidos (incluso a alto nivel)
- Al menos un canal digital activo
- Marcos de medición cargados (`data/metrics-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Definir las preguntas de los negocios

1. Identificar las preguntas de negocios críticas **3-5** respondidas por los interesados
2. Mapa de cada pregunta a una etapa **Ver-Think-Do-Care**:
   **Ver:** Mayor audiencia calificada
   - **Piensa:** Audiencia con alguna intención comercial
   - **Do:** Audiencia con fuerte intención comercial
   - **Care:** Clientes existentes (2+ transacciones)
3. Priorizar las cuestiones mediante el impacto en las decisiones empresariales
4. Identificar **what las decisiones cambiarán** basándose en las respuestas
5. Rechazar preguntas de vanidad - si la respuesta no cambiará una decisión, no importa

### Fase 2: Select Metrics (DMMM)

1. Para cada pregunta de negocio, aplique el modelo **Medición Digital**:
   *Objetivo de la empresa* - lo que queremos lograr
   - Objetivo** - Meta mensurable específica
   **KPI** - métrica que indica el progreso hacia la meta
   *Ergete* -- umbral numérico para el éxito
   **Segmento** - a qué público se aplica esto
2. Aplicar el **¿Qué?"* prueba a cada métrica - si no puedes decir qué acción tomarías, eliminarlo
3. Limitar a **10-15 KPIs totales** en todos los objetivos (Kaushik's 10/90 regla)
4. Asegurar una mezcla de **acquisition, comportamiento y resultado** métricas
5. Definir el **one métrica que más importa** (OMTM) para este período

### Fase 3: Dibujo de diseño

1. Estructurar el tablero usando el marco **Ver-Think-Do-Care**
2. Para cada etapa, mostrar:
   **Primary KPI** con tendencia (up/down/flat)
   - **Metrices de apoyo** (2-3 máx)
   Comparación** - período sobre el período o segmento durante el segmento
3. Incluir la fila ** "Actions"** - qué debe hacerse basándose en los datos actuales
4. Aplicar los principios de la tabla de cálculo de Kaushik:
   - No más de 1 página por audiencia
   - Cada métrica tiene una anotación "y qué"
   - Incluir al menos un punto de referencia competitivo
5. Defina la frecuencia de refrescos (real-time, diario, semanal)

### Fase 4: Implementar el seguimiento

1. Mapa de cada KPI a un **data fuente** (GA4, CRM, análisis sociales, etc.)
2. Definir **tracking eventos** necesarios para las métricas de comportamiento
3. Crear un **measurement documento**:
   - Nombre del evento, gatillo, parámetros, fuente
4. Identificar **data brechas** - métricas que queremos pero no podemos medir aún
5. Prioridad gap-closing por impacto en la calidad de las decisiones

## Formato de salida

```yaml
analytics_framework:
  business: "{name}"
  business_questions: ["{q1}", "{q2}", "{q3}"]
  omtm: "- ¿Qué? - ¿Qué?" 
  stdc_metrics:
    see: {kpi: "", target: "", source: ""}
    think: {kpi: "", target: "", source: ""}
    do: {kpi: "", target: "", source: ""}
    care: {kpi: "", target: "", source: ""}
  total_kpis: {number}
  dashboard:
    pages: {number}
    refresh: "{real-timeSilencioso, semanalmente" 
    sections: ["{section1}", "{section2}"]
  tracking_plan:
    events_defined: {number}
    data_gaps: ["{gap1}", "{gap2}"]
  deliverables:
    - analytics-framework.md
    - dashboard-design.md
    - tracking-plan.md
```

## Condiciones de veto

1. **Nunca incluye una métrica sin la prueba "¿Qué?"** - cada métrica debe conducir una decisión
2. **Nunca supere el total de 15 KPI** - la sobrecarga métrica destruye el enfoque
3. **Nunca construir un tablero sin la fila de Acciones** - datos sin acción es la decoración
4. ** NUNCA pista sin plan de medición** - ad-hoc seguimiento crea datos no fiables
5. **Nunca saltar puntos de referencia competitivos** - los datos internos sin contexto no tienen sentido

## Criterios de finalización

- [ ] 3-5 preguntas de negocios definidas y mapeadas a See-Think-Do-Care
- [ ] DMMM aplicado con objetivos, metas, KPIs, objetivos, segmentos
- [ ] OMTM (Una Métrica Que Importa) identificado
- [ ] Panel de mando diseñado con máx 15 KPIs y Actions fila
- [ ] Plan de seguimiento creado con eventos y fuentes de datos
- [ ] Se identificaron y priorizaron las deficiencias de datos
- [ ] La salida coincide con el esquema anterior
