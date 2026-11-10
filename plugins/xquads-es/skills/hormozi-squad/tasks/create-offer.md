---
task: createOffer()
responsavel: "@hormozi-offers"
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
  - campo: grandSlamOffer
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] La Ecuación de Valor anotó en los 4 cuadrantes" 
  - "[ ] Problemas mapeados para la solución de vehículos con nombres propietarios" 
  - "[ ] Oferta pila montada con núcleo + bonificaciones" 
---

# Task: Create Grand Slam Offer

** ID de usuario: **HORMOZI-001
**Version:** 1.0.0
**Command:** `*create-offer`
**Agente:** Ofertas de Hormozi (hormozi-offers)
**Purpose:** Construir una Oferta de Grand Slam utilizando la Ecuación de Valores de Ofertas de $100M.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silencioso cadena Silencioso de usuario inducido por Silencio
Silencios Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio
| current_price Silencio número Silencio Usuario prompt Silencio No Silencio Precio existente si es aplicable 
| delivery_method Silencio Silencio Silencio Silencio Usuario prompt Silencio No Silencio Cómo se entrega el producto Silencio
Silencioso Silencio Silencio Silencio Silencio No Silencio
Silenciosos competidores Silencio lista Silenciosos Usuarios prompt Silencio No Silencio Ofertas competidores Silencio

---

## Preconditions

- Producto básico o servicio identificado
- Público objetivo definido con puntos de dolor claros y resultados de sueño

---

## Fases de Ejecución

## Fase 1: Sueño de la preparación de resultados
1. Definir el resultado del sueño en las palabras del cliente (no en la suya)
2. Identificar la brecha entre dónde están y dónde quieren estar
3. Listar todos los problemas que se interponen entre el cliente y el resultado del sueño
4. Para cada problema, lista el sub-problems y problemas adyacentes
5. Califique cada problema por gravedad (cuánta dolor causa 1-10)
6. Identificar los problemas que han intentado y no han resuelto antes

### Fase 2: Calidad de la Ecuación de Valor
1. Aplicar la Ecuación del Valor Hormozi: Valor = (Resultado de Dream x probabilidad percibida) / (Delay temporal x esfuerzo &quot; Sacrificio)
2. Maximizar el numerador:
   - Resultado del sueño: Hacer el resultado tan específico y vívido como sea posible
   - Percibido de probabilidad: Pruebas de ataúd, garantías y historial
3. Minimizar la denominación:
   - Retraso del tiempo: Comprime el tiempo al primer resultado
   - Momento &amp; Sacrificio: Quitar la fricción, hacerlo por ellos cuando sea posible
4. Puntuación de cada cuadrante (1-10) para la oferta actual
5. Identificar qué cuadrante tiene más margen para mejorar

### Fase 3: Oferta Arquitectura
1. Transformar cada problema en un vehículo de solución (curso, herramienta, plantilla, servicio, comunidad, etc.)
2. Nombre de cada vehículo de solución con nombre propietario
3. Método de entrega y formato de la asignación a cada vehículo
4. Apilar los vehículos en una oferta cohesiva:
   - Oferta principal: El vehículo de transformación principal
   - Bonos de velocidad: cosas que comprimen el tiempo para dar resultado
   - Bonos de Effort: cosas que reducen el trabajo requerido
   - Prueba de bonificaciones: cosas que aumentan la confianza
5. Diseñar la garantía utilizando la pila de garantía Hormozi:
   - Incondicional (reembolso completo, sin preguntas)
   - condicional (reembolso si haces X y no te das Y)
   - Anti-garantía (esta no es para ti si...)
   - Rendimiento (trabajaremos gratis hasta que llegues a X)
6. Establecer el precio basado en el valor entregado, no costo o competidores

### Fase 4: Oferta de Naming y Posicionamiento
1. Crear un nombre de oferta convincente que implique la transformación
2. Escribe el one-line Proposición de valor
3. Defina el calificativo "Esto NO es para usted" para aumentar la exclusividad percibida
4. Crear el scarcity/urgency mecanismo
5. Escribe la diapositiva de la pila (resumo visual de todo incluido)

---

## Formato de salida

```markdown
## Grand Slam Offer: {Offer Name}

**Dream Outcome:** {specific outcome}
**Avatar:** {dream customer}
**Price:** ${price}
**Value Equation Score:** {X}/10

---

### Value Equation Breakdown

| Quadrant | Score | Strategy |
|----------|-------|----------|
| Dream Outcome | X/10 | {how we maximize} |
| Perceived Likelihood | X/10 | {how we maximize} |
| Time Delay | X/10 | {how we minimize} |
| Effort & Sacrifice | X/10 | {how we minimize} |

### Problems → Solutions Map

| Problem | Solution Vehicle | Proprietary Name | Delivery |
|---------|-----------------|-------------------|----------|

### Offer Stack

| Component | What It Does | Value |
|-----------|-------------|-------|
| Core Offer | {description} | ${value} |
| Speed Bonus 1 | {description} | ${value} |
| Effort Bonus 1 | {description} | ${value} |
| Proof Bonus 1 | {description} | ${value} |

**Total Value:** ${total}
**Your Price:** ${price}

### Guarantee
{Full guarantee statement with type}

### Scarcity/Urgency
{Mechanism and rationale}

### Qualifier
"This is NOT for you if..."

### Stack Slide Copy
{Ready-to-use visual stack summary}
```

---

## Condiciones de veto

- Nunca crear una oferta sin aplicar la Ecuación de Valor
- NUNCA precio basado en los precios de los competidores - precio basado en el valor proporcionado
- Nunca saltes el problem-solution mapeo — cada solución debe resolver un problema real
- Nunca crea una garantía de que el negocio no puede cumplir
- Nunca añadir bonos que distraen de la transformación central

---

## Criterios de finalización

- Resultado de sueño definido en el lenguaje del cliente
- [ ] La Ecuación de Valor anotó en los 4 cuadrantes
- [ ] Problemas mapeados para la solución de vehículos con nombres propietarios
- [ ] La pila de la Oferta montada con núcleo + bonificaciones
- [ ] Garantía diseñada y documentada
- [ ] Precio con value-based justificación
- [ ] Mecanismo de escasez definido
- [ ] Copia de diapositivas de Stack escrita
