---
task: createOffer()
responsavel: "@dan-kennedy"
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
  - campo: offer_architecture
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Transformación básica y pila de valor definida" 
  - "[ ] 3-5 bonos relevantes diseñados con garantía" 
  - "[ ] estrategia de anclaje de precios y ofrecer copia de pila listo" 
---

# Task: Create Offer

** ID de la lista:** COPY-007
**Version:** 1.0.0
**Command:** `*create-offer`
Dan Kennedy (Dan Kennedy)dan-kennedy) o Russell Brunson (russell-brunson)
**Purpose:** Arquitecto una oferta irresistible que maximiza el valor percibido y elimina la resistencia a la compra.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silencioso cadena Silencioso de usuario inducido por Silencio
Silencio audiencia Silencio Silencio Silencio Sugerencia de usuario Silencio Silencioso comprador de objetivo con contexto presupuestario Silencio
| price_range Silencio Silencio Silencio Usuario prompt Silencio No Silencio Precio aceptable o precio objetivo Silencio
| delivery_method TENEDAD TENIDO TENIDO ANTERIOR NO TENIDO Digital, físico, servicio, híbrido TENIDO
Silenciosos competidores Silencio lista Silenciosos Usuarios prompt Silencio No TENCIÓN Ofertas en el mercado TEN
| existing_assets Silenciosidad lista Silencios de usuario Silencios, contenidos, herramientas ya disponibles Silencio
| business_model TENEDA TENCIÓN SONIDO EL Usuario prompt TEN NO TENIDO Una vez, suscripción, high-ticket, low-ticket |

---

## Preconditions

- Producto o servicio básico definido con una transformación clara que ofrece
- Público objetivo identificado con willingness-to-pay context

---

## Fases de Ejecución

### Fase 1: Arquitectura de valor
1. Definir la transformación central (antes de estado a estado después)
2. Identificar todos los componentes de valor que el producto ofrece:
   - Resultado primario (lo principal que compran)
   - Resultados secundarios (transformaciones de bonos)
   - Velocidad de resultado (valor de compresión de tiempo)
   - Reducción del esfuerzo (valor de la manguera)
   - Reducción del riesgo (valor de seguridad)
3. Calcular el "valor de resultado del sueño" - ¿Qué pagarían si se garantiza?
4. Mapear el valor de la pila de la mayoría al menos impactante

### Fase 2: Oferta Construcción
1. Estructurar la oferta central con entregables claras
2. Diseño de la pila de bonificación (3-5 bonos):
   - Cada bonificación debe resolver un problema relacionado o acelerar el resultado
   - Asignar valores individuales de dólar a cada bono
   - Pedido de bonos por valor percibido (primero más alto)
3. Realizar la garantía:
   - Elija el tipo: money-back, results-based, condicional, incondicional
   - Haga la garantía lo suficientemente audaz como para ser un punto de venta por su cuenta
   - Definir la ventana de garantía y las condiciones
4. Construir el urgency/scarcity elemento:
   - Elija el tipo: time-limited, quantity-limited, bonus-limited, price-increase
   - Asegurar que la escasez sea real o creíble
5. Establecer el precio mediante el anclaje:
   - Establezca el precio "debe ser" (valor total de todo)
   - Mostrar el precio de "podría ser" (descuento del total)
   - Revelar el precio real como una fracción de valor percibido

### Fase 3: Oferta Posicionamiento
1. Escribe la copia de la pila de oferta (cómo se presentará en materiales de venta)
2. Crear la sección de resumen "lo que consigues"
3. Escriba la declaración de garantía como copia independiente
4. Elaborar la descripción de la justificación de los precios
5. Crear objection-handling elementos incorporados en la estructura de oferta
6. Defina el CTA exacto y lo que sucede después de ellos click/call

---

## Formato de salida

```markdown
## Offer Architecture: {Product Name}

**Core Transformation:** {before} → {after}
**Price:** {price}
**Total Perceived Value:** {value}
**Value-to-Price Ratio:** {X}:1
**Guarantee:** {type + window}

---

### Core Offer
{Description of what they get — the main product/service}

### Bonus Stack

| # | Bonus Name | What It Does | Value |
|---|------------|-------------|-------|
| 1 | {name} | {solves X} | ${value} |
| 2 | {name} | {accelerates Y} | ${value} |
| 3 | {name} | {removes Z friction} | ${value} |

### Guarantee
{Full guarantee statement — bold, specific, risk-reversing}

### Urgency/Scarcity
{What creates time pressure — and why it's credible}

### Price Presentation
- Total Value: ${total}
- Not ${high_anchor}
- Not even ${mid_anchor}
- Today: ${actual_price}
- {Payment plan option if applicable}

### Offer Stack Copy
{Ready-to-use copy block for sales page/VSL/email}

### Objection Handlers Built Into Offer
| Objection | How the Offer Addresses It |
|-----------|---------------------------|
```

---

## Condiciones de veto

- Nunca crear una oferta sin garantía - ninguna garantía significa que usted está pidiendo al comprador que lleve todo riesgo
- Nunca añadir bonos no relacionados con la transformación central
- Nunca use la escasez falsa - debe ser real o al mínimo creíble
- NUNCA precio sin anclaje al valor percibido primero
- Nunca deje el vago de CTA - especificar exactamente lo que sucede después

---

## Criterios de finalización

- [ ] Transformación básica claramente definida
- [ ] pila de valor mapeado con valores individuales
- [ ] 3-5 bonos relevantes diseñados y valorados
- [ ] Garantía hecha como punto de venta
- [ ] Urgency/scarcity elemento definido
- [ ] estrategia de anclaje de precios completa
- [ ] Oferta copia de pila lista para uso
- [ ] Manejadores de objetos incrustados en la estructura de oferta
