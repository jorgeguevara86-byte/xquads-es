---
task: auditBusiness()
responsavel: "@hormozi-audit"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: business
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: revenue
    tipo: number
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: businessAudit
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Ecuación de ingresos marcado con los 4 componentes" 
  - "[ ] #1 limitación claramente identificada" 
  - "[ ] 3 recomendaciones prioritarias con impacto de los ingresos" 
---

# Task: Audit Business

** ID de usuario: **HORMOZI-007
**Version:** 1.0.0
**Command:** `*audit-business`
*Agente* *Audición de Hormozi*hormozi-audit)
**Purpose:** Realizar una auditoría comercial completa con metrics-driven diagnóstico.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencios Silencios Silencio Silencio Sugerencia de usuario Silencio Silencio Nombre de empresa, tipo y etapa TEN
Silencio ingreso Silencio número Silencio Usuario prompt Silencio Sí Silencio Ingresos mensuales o anuales Silencio
| profit_margin Silencio número Silencio Usuario prompt Silencio No Silencio Porcentaje actual de ganancia Silencio
| team_size Silencio número Silencio invocar usuario no Silencio Número de employees/contractors |
Silencio canales Silenciosos lista Silenciosos Usuarios prompt Silencio No Silencio Marketing y canales de venta en uso Silencio
| biggest_challenge TENED TENIDO TENIDO ANTERIOR NO TENIDO PRIMERA PRIMERA BUENA CONTRAJE TENCIÓN
TENCIÓN TERMINADA TENIDO objeto TENIDO Insinuación de usuario TENIDO NO TENIDO métricas de negocio disponibles (CAC, LTV, churn, etc.) TENIDO

---

## Preconditions

- Las empresas están en funcionamiento con ingresos
- Propietario dispuesto a compartir números honestos

---

## Fases de Ejecución

## Fase 1: Auditoría del motor de ingresos
1. Diagnostique la ecuación de ingresos: Ingresos = Plomos x Tasa de conversión x Precio x Frecuencia
2. Puntuación de cada componente (1-10):
   - Líderes: Volumen y calidad de los cables entrantes
   - Conversión: Porcentaje de pistas que se convierten en clientes
   - Precio: Promedio de ingresos por transacción
   - Frecuencia: ¿Con qué frecuencia compran los clientes (precio de rescate)
3. Identificar el vínculo más débil en la cadena de ingresos
4. Calcular el impacto de una mejora del 10% en cada componente
5. Determinar la limitación: ¿qué mejora única duplicaría los ingresos?

## Fase 2: Cuenta de la Auditoría
1. Evaluar la oferta actual contra la Ecuación de Valor
2. Partitura cada cuadrante:
   - Resultado del sueño: ¿Es la promesa lo suficientemente convincente?
   - Percibido de la probabilidad: ¿Cree el comprador que funcionará?
   - ¿Cuánto falta para el primer resultado?
   - Effort & Sacrifice: ¿Cuánto trabajo tiene el comprador?
3. Identificar si la oferta es "buena" (problema de lobos) o "abuelo" (irresistible)
4. Valores de referencia: ¿está el negocio bajo precio por el valor entregado?

## Fase 3: Auditoría de Operaciones
1. Evaluar el sistema de entrega:
   - ¿Puede el negocio cumplir 2x volumen actual sin romper?
   - ¿Cuál es el costo de entrega por cliente?
   - ¿Dónde están los cuellos de botella en cumplimiento?
2. Evaluar al equipo:
   - Las dependencias de la persona clave
   - La claridad y la rendición de cuentas en función del papel
   - Utilización de la capacidad
3. Evaluar las finanzas:
   - Margen bruta
   - Margen neto
   - Previsibilidad de la corriente de efectivo
   - Costo de adquisición de clientes vs Valor de tiempo de vida

### Fase 4: Prescripción de crecimiento
1. Identificar el límite #1 para retener el negocio de vuelta
2. Proporcionar 3 recomendaciones específicas y prioritarias:
   - Ganancia rápida (aplicable esta semana)
   - Juego de mediano plazo (imponible este mes)
   - Cambio estratégico (ejecución este trimestre)
3. Cálculo del impacto de los ingresos de cada recomendación
4. Definir el próximo enfoque de 90 días
5. Identificar qué hacer para detener la acción ( auditiva de subtracción)

---

## Formato de salida

```markdown
## Business Audit: {Business Name}

**Revenue:** ${X}/month
**Margin:** {X}%
**Stage:** {startup / growth / scale / optimize}
**#1 Constraint:** {identified constraint}

---

### Revenue Engine

| Component | Score | Current | 10% Improvement Impact |
|-----------|-------|---------|----------------------|
| Leads | X/10 | {metric} | +${X}/month |
| Conversion | X/10 | {metric}% | +${X}/month |
| Price | X/10 | ${metric} | +${X}/month |
| Frequency | X/10 | {metric}x/year | +${X}/month |

**Weakest Link:** {component}
**Doubling Lever:** {which component to focus on}

### Offer Assessment

| Quadrant | Score | Issue | Fix |
|----------|-------|-------|-----|
| Dream Outcome | X/10 | {issue} | {fix} |
| Perceived Likelihood | X/10 | {issue} | {fix} |
| Time Delay | X/10 | {issue} | {fix} |
| Effort & Sacrifice | X/10 | {issue} | {fix} |

### Operations Assessment
**Scalability:** {can/cannot handle 2x volume}
**Bottleneck:** {identified bottleneck}
**CAC:LTV Ratio:** {X}:1

### Growth Prescription

| Priority | Recommendation | Timeline | Revenue Impact |
|----------|---------------|----------|----------------|
| 1 | {quick win} | This week | +${X}/month |
| 2 | {medium play} | This month | +${X}/month |
| 3 | {strategic shift} | This quarter | +${X}/month |

### Stop Doing List
1. {thing to stop}
2. {thing to stop}

### 90-Day Focus
{One clear priority for the next 90 days}
```

---

## Condiciones de veto

- NUNCA auditoría sin números de ingresos reales - estimaciones producen estimate-quality asesoramiento
- Nunca recomendar más de 3 prioridades - el enfoque es el punto
- NUNCA ignorar el lado de las operaciones - crecimiento sin capacidad de cumplimiento mata a las empresas
- NUNCA salte la lista de "parar de hacer" - la resta es tan importante como adición
- Nunca proporcionar asesoramiento genérico; cada recomendación debe vincularse a los números de negocio específicos

---

## Criterios de finalización

- Ecuación de ingresos anotado con los 4 componentes
- [ ] El más débil enlace y la palanca duplicada identificado
- [ ] Oferta auditada contra la Ecuación de Valor
Operaciones evaluadas para escalabilidad
- [ ] #1 restricción claramente identificada
- [ ] 3 recomendaciones prioritarias con impacto de los ingresos
- Deja de hacer la lista proporcionada
- [ ] 90 días de enfoque definido
