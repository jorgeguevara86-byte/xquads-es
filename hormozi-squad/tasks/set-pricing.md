---
task: setPricing()
responsavel: "@hormozi-pricing"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: pricingStrategy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Valor entregado calculado con dimensiones financieras y emocionales" 
  - "[ ] Modelo de precios seleccionado con racionalidad" 
  - "[ ] Plan de prueba definido" 
---

# Task: Set Pricing Strategy

** ID de usuario: **HORMOZI-003
**Version:** 1.0.0
**Command:** `*set-pricing`
** Agente: ** Hormozi Precios (hormozi-pricing)
**Purpose:** Diseño value-based estrategia de precios que maximiza los ingresos sin competir en el precio.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silencioso cadena Silencioso de usuario inducido por Silencio producto o servicio al precio Silencio
Silencio audiencia Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio willingness-to-pay context /
| current_price Silencio número Silencio Usuario prompt Silencio No Silencio Precio existente si es aplicable 
| cost_structure TENCIÓN ANTERIOR ANTERIOR NO TENIDO Costo para entregar (COGS, cumplimiento, etc.) TENIDO
| competitor_prices Silencio lista Silencio Usuario prompt Silencio No Silencio Precio de referencias Silencio
| business_model TENEDA TENIDO ANTERIOR NO TENIDO Una sola vez, suscripción, empatado, usage-based |
| revenue_target Silencio número Silencio Usuario prompt Silencio No Silencio Target monthly/annual ingresos /

---

## Preconditions

- Producto o servicio definido con entrega de valor claro
- Estructura de la oferta completada (idealmente a través create-offer.md primero)

---

## Fases de Ejecución

### Phase 1: Value Assessment
1. Calcular el ROI que el cliente recibe del producto
2. Aplicar la Regla 10x: el precio debe ser 1/10 del valor mínimo entregado
3. Determinar el "costo de inacción" — ¿qué no compra los cuesta?
4. Identificar inversiones comparables que el cliente ya hace
5. Evaluar el valor emocional más allá del ROI financiero

## Fase 2: Arquitectura de precios
1. Elija el modelo de precios:
   - Premium (alto precio, alto toque, menos clientes)
   - Volumen (precio más bajo, systems-based, muchos clientes)
   - Híbrido (con niveles de entrada y de prima)
2. Establecer el precio del anclaje (el número "debería ser" basado en el valor)
3. Establecer el precio real como una fracción del ancla
4. Opciones de pago de diseño:
   - Paga...in-full con incentivo de descuento
   - Plan de pago con prima para conveniencia
   - Suscripción con lock-in beneficios
5. Crear fichas de precios si es aplicable:
   - Bien: oferta básica sólo
   - Mejor: Bonos de Core + velocidad
   - Mejor: Core + todos los bonos + acceso premium

## Fase 3: Justificación de precios
1. Construir el price-to-value narrativa
2. Calcular el daily/weekly desglose de costos ("menos que un café por día")
3. Crear la pila de comparación (lo que más cuesta tanto pero ofrece menos)
4. Definir el cronograma del ROI - ¿cuándo paga la inversión por sí misma?
5. Escriba la copia de la sección de precios para materiales de venta

### Fase 4: Optimización de precios
1. Establecer el precio inicial de la prueba
2. Definir la metodología de prueba de precios:
   - Prueba a 2x precio actual primero (la mayoría de las empresas menos precio)
   - Tasa de conversión de monitores e ingresos (no sólo conversión)
   - Los ingresos por plomo importan más que la tasa de conversión
3. Definir los desencadenantes del aumento de precios
4. Planificar la estrategia anual de aumento de los precios

---

## Formato de salida

```markdown
## Pricing Strategy: {Product Name}

**Model:** {premium / volume / hybrid}
**Price:** ${price}
**Value Delivered:** ${value}
**Value-to-Price Ratio:** {X}:1
**Cost of Inaction:** ${cost}/year

---

### Value Assessment

| Dimension | Value | Rationale |
|-----------|-------|-----------|
| Financial ROI | ${X} | {calculation} |
| Time Saved | {hours} | {at $X/hour = $Y} |
| Emotional Value | {qualitative} | {description} |
| Cost of Inaction | ${X}/year | {what they lose by not buying} |

### Pricing Tiers

| Tier | Includes | Price | Target Customer |
|------|----------|-------|----------------|

### Payment Options

| Option | Price | Terms | Incentive |
|--------|-------|-------|-----------|

### Price Justification Narrative
{Ready-to-use copy for sales materials}

### Testing Plan
| Phase | Price | Duration | Success Metric |
|-------|-------|----------|----------------|

### Price Increase Strategy
{Annual increase plan with triggers}
```

---

## Condiciones de veto

- NUNCA precio basado únicamente en los precios de la competencia - que es una carrera al fondo
- NUNCA precio más bajo para aumentar las ventas sin primera prueba a precios más altos
- Nunca ofrecer descuentos sin una razón estratégica (cirugía, lealtad, volumen)
- NUNCA precio inferior a 10x de los gastos de entrega - los márgenes deben apoyar el crecimiento
- NUNCA fijar precio sin calcular el valor entregado primero

---

## Criterios de finalización

- [ ] Valor entregado calculado con dimensiones financieras y emocionales
- [ ] 10x Regla aplicada y validada
- [ ] Modelo de precios seleccionado con racionalidad
- [ ] Tiers y opciones de pago diseñados
- [ ] La justificación de precios escrito
- [ ] Plan de prueba definido
- [ ] Estrategia de aumento de precios documentada
