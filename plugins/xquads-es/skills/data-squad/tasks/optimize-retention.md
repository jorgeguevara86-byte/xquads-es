---
task: optimizeRetention()
responsavel: "@peter-fader"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: business
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: customer_data
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: retention_optimization
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Serie de CLV completa con 4 niveles" 
  - "[ ] Puntaje de salud del cliente definido con 6 dimensiones" 
  - "[ ] Libros de juego de intervención diseñados por nivel de riesgo" 
---

# Task: Optimize Retention

** ID de usuario:** DATOS-004
**Version:** 1.0.0
**Command:** `*optimize-retention`
**Agente: ** Peter Fader (Peter Fader)peter-fader) + Nick Mehta (nick-mehta)
**Fuente:** Optimize la retención de clientes y el valor de vida a través de segmentación CLV, predicción de churn e intervenciones de éxito

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `business` Silencio invocar usuario Silencio Sí Silencio descripción de la empresa y modelo (SaaS, e-commerce, etc.) TENIDO
| `customer_data` Silencio Usuario Silencio Sí Silencio Datos disponibles del cliente (transacciones, compromiso, soporte) Silencio
| `current_retention` TENIDO Usuario TENIDO No TEN La tasa de retención actual y patrones conocidos de churn TEN
| `revenue_model` Silencioso usuario Silencio No Silencio Precio modelo, ARPU, expansión ingresos 
| `support_structure` Silencio Usuario Silencio No Silencio Estructura actual del equipo de CS y procesos Silencio

## Preconditions

- Los datos de transacción o compromiso del cliente existen
- Se define el modelo de negocio (suscripción, transacción, híbrido)
- Marcos de medición cargados (`data/metrics-frameworks.yaml`)

## Fases de Ejecución

Fase 1: Segmento por CLVpeter-fader)

1. Aplicar **Análisis de base de clientes** principios:
   - No todos los clientes son creados iguales
   - El comportamiento pasado predice comportamiento futuro (con incertidumbre)
   - La heterogeneidad del cliente es el punto de partida
2. Calcular ** Componentes de la LCLV**:
   - ¿Cuándo fue la última vez? transaction/engagement
   - ¿Qué tan a menudo hacen? transact/engage
   - **Monetario:** ¿Cuánto gastan por transacción
3. clientes de segmento en **value Tiers**:
   - **Platinum (top 5%):** Mayor compromiso
   - **Gold (next 15%):** ClV fuerte, comportamiento confiable
   **Estilador (nexto 30%):** CV moderado, potencial de crecimiento
   - ** Bronce (50 % inferior): ** Bajo CLV, alta heterogeneidad
4. Aplicar el **BG/NBD modelo** lógica:
   - Estimar la probabilidad de que cada cliente esté "vivo" (activo)
   - Predecir las transacciones futuras esperadas por cliente
   - Identificar clientes con probabilidad declinante (pre-churn)
5. Calcular **customer riesgo de concentración** - qué porcentaje de ingresos proviene de un 20% superior

### Fase 2: Identifique las señales de Churn (nick-mehta)

1. Defina el **Punto de Salud Customer** con 6 dimensiones:
   - **Uso del producto:** Adoptación de características, frecuencia de inicio de sesión, tiempo en la aplicación
   - **Interacción de apoyo:** Volumen de entradas, sentimiento, tasa de escalada
   **Iniciación:** El correo electrónico abre, asistencia a eventos, actividad comunitaria
   ** Resultado de la actividad:** Están logrando sus objetivos con el producto
   - ** Relación:** puntuación del NPS, participación de patrocinador ejecutivo
   **Financial:** Timeliness de pago, tendencia de valor contractual
2. Peso cada dimensión por poder predictivo para el churn
3. Identificar **leading indicadores de la churn** (precede churn en 30-90 días):
   - Declinación de uso √ 30% month-over-month
   - Billetes de apoyo con sentimientos negativos
   - Se perdió la QBR o se examinaron las reuniones
   - Salida de campeón (contacto sale de la compañía)
   - Estabilización de adopción de características (sin nuevas características adoptadas en 60 días)
4. Crear **churn riesgo de puntuación** (0-100):
   - 0-25: Healthy
   - 26-50: Monitor
   - 51-75: At Risk
   - 76-100: Critical
5. Segmento at-risk clientes por **save potencial** (alto, medio, bajo)

### Fase 3: Intervenciones de Diseño (nick-mehta)

1. Intervenciones de mapa a las **10 Leyes de éxito del cliente**:
   - Ley 1: Vender al cliente adecuado
   - Ley 2: Alinear la tendencia natural a la churn
   - Ley 3: Los clientes esperan que los haga exitosos
   - Ley 4: Supervisar y gestionar sin descanso la salud
   - Ley 5: Ya no se puede construir la lealtad a través de las relaciones
   - Ley 6: El producto es su único diferenciador escalable
   - Ley 7: Obsesión sobre time-to-value
   - Ley 8: Profundizar la colaboración con data-driven decisiones
   - Ley 9: Ampliación de la conducción cuando los clientes tienen éxito
   - Ley 10: Es una top-down, company-wide compromiso
2. Intervenciones de diseño por nivel de riesgo:
   - **Healthy:** Reseñas de éxito proactivo, señales de expansión
   - **Monitor:** Aumentar puntos táctiles, enviar consejos de uso, comprobar objetivos
   **A riesgo:** Divulgación ejecutiva, plan de éxito, recursos dedicados
   **Crítica:** Ahorre el compromiso del equipo, escalada ejecutiva, oferta de incentivos
3. Definir **playbooks** para cada tipo de intervención
4. Crear **automation reglas** para intervenciones escaladas
5. Diseño de la plantilla **QBR (Revisión de Negocios Quártermente)**

### Fase 4: Medida NRR (peter-fader + nick-mehta)

1. Definir y seguir **Retención de ingresos netos**:
   - NRR = (Iniciar MRR + Ampliación - Contracciones - Churn) / Inicio MRR
   - Meta: √°0% (net positivo = crecimiento sin nuevos clientes)
2. Track **cohort curvas de retención**:
   - Análisis mensual de cohortes
   - Compare formas curvas a través de segmentos
   - Identificar el "punto de flatización" (cuando la retención se estabiliza)
3. Medida **intervention eficacia**:
   - Tasa de ahorro por tipo de intervención
   - Tiempo de intervención a estabilización
   - Costo por salva vs. CLV recuperado
4. Construir el **retention Dashboard**:
   - Tendencia de la RNR (mensual)
   - Distribución de puntajes de salud
   - Gasoducto de riesgo de Churn
   - Tasa de éxito de la intervención
5. Definer **escalation gatillos** para data-chief

## Formato de salida

```yaml
retention_optimization:
  business: "{name}"
  clv_segmentation:
    platinum: {count: "", pct_revenue: ""}
    gold: {count: "", pct_revenue: ""}
    silver: {count: "", pct_revenue: ""}
    bronze: {count: "", pct_revenue: ""}
  concentration_risk: "{top 20% = X% revenue}" 
  health_score:
    dimensions: 6
    churn_signals: ["{signal1}", "{signal2}", "{signal3}"]
  churn_risk_distribution:
    healthy: "{%}"
    monitor: "{%}"
    at_risk: "{%}"
    critical: "{%}"
  nrr:
    current: "{%}"
    target: "{%}"
  interventions:
    playbook_count: {number}
    automation_rules: {number}
  deliverables:
    - clv-segmentation.md
    - health-score-model.md
    - intervention-playbooks.md
    - retention-dashboard.md
```

## Condiciones de veto

1. **Nunca trate a todos los clientes por igual** - La segmentación CLV existe por una razón
2. **Nunca predice el churn con una sola métrica** - los puntajes de salud requieren múltiples dimensiones
3. **Nunca automatizar critical-risk intervenciones** - Se requiere el toque humano para salvar los intentos
4. **Nunca ignore la expansión de la estrategia de retención** -- NRR √≥ 100% es el objetivo
5. **Nunca mide la retención sin análisis de cohortes** - se ocultan las tasas agregadas segment-level problemas

## Criterios de finalización

- Segmento CLV completo con 4 niveles
- [ ] Puntaje de salud del cliente definido con 6 dimensiones
Al menos 5 indicadores principales de la churn identificados
- [ ] Anotación de riesgo de Churn implementada (0-100 escala)
- [ ] Libros de juego de intervención diseñados para cada nivel de riesgo
- [ ] fórmula NRR definida con mecanismo de seguimiento
- [ ] Panel de retención diseñado
- [ ] La salida coincide con el esquema anterior
