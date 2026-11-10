---
task: auditAdAccount()
responsavel: "@ads-analyst"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: account_data
    tipo: object
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: adAccountAudit
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] 8-dimensión de la tarjeta de puntuación de salud" 
  - "[ ] Todas las campañas clasificadas por nivel de rendimiento" 
  - "[ ] 5 recomendaciones prioritarias con impacto proyectado" 
---

# Task: Audit Ad Account

** ID de la lista:** TRAFFIC-002
**Version:** 1.0.0
**Command:** `*audit-ad-account`
**Agente:**ads-analyst) o Analista de Desempeño (performance-analyst)
**Fuente:** Auditoría completa de una cuenta de publicidad para identificar las prioridades de desperdicio, oportunidades y optimización.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencio, plataforma, tiktok, linkedin, youtube Silencio
| account_data TENCIÓN ANTERIOR ANTERIOR ANTERIOR Sí ANTERIGEN métricas clave: pasar, CPA, ROAS, CTR, CVR, impresiones ANTE
| time_period Silencio Silencio Silencio Silencio Usuario inmediato Sí Silencioso ventana de auditoría (último 30, 60 o 90 días) Silencio
| business_type TENED TENED SON SONIDO TENIDO NO TENIDO contexto de la industria para benchmarking 
Silencio Silencio Silencio Silencio Silencio Silencio No Silencio , objetivos y metas de negocios 
| num_campaigns Silencio número Silencio Usuario prompt Silencio No Silencio Número de campañas activas ←

---

## Preconditions

- Datos de cuenta disponibles con al menos 30 días de historia
- Acceso a campaign-level métricas (no sólo account-level)
- Objetivos empresariales definidos para el contexto

---

## Fases de Ejecución

## Fase 1: Control de Salud de Cuentas
1. Partir de la cuenta en 8 dimensiones (1-10 cada uno):
   - Estructura: Campaign/ad set/ad y nombramientos de convenios
   - Meta: Calidad de la audiencia, superposición y niveles de agotamiento
   - Creativo: Variedad de anuncios, frescura y distribución de rendimiento
   - Presupuesto: Eficiencia de la asignación en las campañas
   - Bidding: Estrategia de adecuación y optimización
   - Rastreo: Pixel/conversion Precisión de configuración
   - Alineación de embudos: Campañas igualadas a etapas de embudo
   - Rendimiento: parámetros de referencia de la plataforma Metrics vs
2. Cálculo account-level métricas agregadas
3. Compare contra los parámetros de referencia de plataforma para la industria

### Fase 2: Análisis de Campañas
1. Categorizar campañas por nivel de rendimiento:
   - Ganadores: arriba de los objetivos ROAS/CPA (escalas)
   - Performers: métricas at-target (optimice éstas)
   - Underperformers: Degradado, decreciente (fijo o muerte)
   - Zombies: Bajo gasto, bajo volumen, sin propósito claro (matar estos)
2. Para cada infraperformador, diagnostice la causa raíz:
   - Bajo CTR: fatiga creativa o desfase de la orientación
   - Alto CTR pero bajo CVR: página de aterrizaje o número de oferta
   - CVR alto pero alto CPA: Bid o problema presupuestario
   - Bajo alcance: Audiencia demasiado estrecha o presupuesto demasiado bajo
3. Calcular el gasto desperdiciado en los infraperformadores y zombis
4. Identificar las tres principales oportunidades de ingresos en la cuenta

### Fase 3: Análisis creativo y de audiencia
1. Rank todos los anuncios activos por ROAS y volumen
2. Identificar patrones creativos en los mejores intérpretes:
   - Formato (imagen, video, carrusel)
   - Tipo de gancho (pregunta, declaración, shock, historia)
   - Longitud (corte vs copia larga)
   - Estilo visual
3. Identificar las señales de fatiga del público:
   - Frecuencia superior a 3 en las campañas de prospección
   - Declinar CTR con el tiempo en el mismo público
   - Aumento de la tendencia de la CPA en la retargetación
4. Evaluar la superposición de audiencia entre los conjuntos de anuncios

### Fase 4: Recomendaciones
1. Priorizar los resultados por impacto de los ingresos (alto, medio, bajo)
2. Proporcionar 5 recomendaciones específicas y viables:
   - Lista de asesinatos: Qué apagar inmediatamente
   - Lista de escalas: Qué aumentar el presupuesto
   - Lista de fijación: Qué optimizar (y cómo)
   - Lista de pruebas: Qué nuevas pruebas se deben realizar
   - Lista de Construcción: Lo que falta de la cuenta
3. Cálculo de los efectos previstos de las recomendaciones de aplicación
4. Crear una hoja de ruta de optimización de 2 semanas

---

## Formato de salida

```markdown
## Ad Account Audit: {Platform}

**Period:** {time_period}
**Total Spend:** ${X}
**Overall ROAS:** {X}:1
**Account Health Score:** {X}/80
**Wasted Spend:** ${X} ({Y}%)

---

### Account Health Scorecard

| Dimension | Score | Status | Key Issue |
|-----------|-------|--------|-----------|
| Structure | X/10 | {OK/Fix} | {note} |
| Targeting | X/10 | {OK/Fix} | {note} |
| Creative | X/10 | {OK/Fix} | {note} |
| Budget | X/10 | {OK/Fix} | {note} |
| Bidding | X/10 | {OK/Fix} | {note} |
| Tracking | X/10 | {OK/Fix} | {note} |
| Funnel Alignment | X/10 | {OK/Fix} | {note} |
| Performance | X/10 | {OK/Fix} | {note} |

### Campaign Performance Tiers

| Tier | Campaigns | Spend | ROAS | Action |
|------|-----------|-------|------|--------|
| Winners | {N} | ${X} | {X}:1 | Scale |
| Performers | {N} | ${X} | {X}:1 | Optimize |
| Underperformers | {N} | ${X} | {X}:1 | Fix/Kill |
| Zombies | {N} | ${X} | — | Kill |

### Top 5 Recommendations

| # | Action | Type | Projected Impact |
|---|--------|------|-----------------|
| 1 | {recommendation} | {kill/scale/fix/test/build} | +${X}/month |

### Kill List
{Campaigns/ad sets to turn off now}

### Scale List
{Campaigns to increase budget}

### 2-Week Optimization Roadmap
| Week | Day | Action | Expected Impact |
|------|-----|--------|----------------|
```

---

## Condiciones de veto

- NUNCA auditoría con menos de 30 días de datos - ventanas cortas producen conclusiones poco fiables
- Nunca recomiendo escalar sin confirmar el seguimiento es preciso
- Nunca matar campañas en fase de aprendizaje - esperar significación estadística
- Nunca ignoran las campañas zombis - que silenciosamente drenan presupuesto
- Nunca se formulan recomendaciones sin un impacto estimado de los ingresos

---

## Criterios de finalización

- [ ] 8-dimensión de la tarjeta de puntuación de salud
- [ ] Todas las campañas clasificadas por nivel de rendimiento
- [ ] Gasto gastado calculado
Causas de raíz diagnosticadas para los infravaloradores
- [ ] 5 recomendaciones prioritarias con impacto proyectado
- [ ] Listas de asesinatos y escalas proporcionadas
- [ ] 2 semanas de optimización de hoja de ruta creada
