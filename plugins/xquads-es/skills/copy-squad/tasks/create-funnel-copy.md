---
task: createFunnelCopy()
responsavel: "@russell-brunson"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: funnel_type
    tipo: enum
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: funnel_copy_system
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Arquitectura de embudos mapeado con todas las páginas y correos electrónicos" 
  - "[ ] Toda página y copia de correo electrónico escrita por estándar de formato" 
  - "[ ] Matemáticas de embudo calculadas con tasas de conversión esperadas" 
---

# Task: Create Funnel Copy

** ID de la lista:** COPY-009
**Version:** 1.0.0
**Command:** `*create-funnel-copy`
**Agente: ** Russell Brunson (Rusell Brunson)russell-brunson)
**Purpose:** Escribe copia para todo un sistema de embudos: desde opt-in a través de la venta.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silencioso cadena Silencioso de usuario inducido por Silencio Silencioso producto básico y línea de productos Silencio
Silenciosamente en la audiencia Silencio Silencio inducido por el usuario Silencio Silencio Target avatar con la compra de viaje Silencio
| funnel_type Silencio en el futuro Silencio insinuar usuario lead-magnet, tripwire, webinar, desafío, high-ticket-application, product-launch |
| offer_stack TEN-OTO2 OTO2, abajo, si es aplicable TEN-T
| traffic_source Silencio Silencio Silencio Silencio No Silencio Canal de tráfico primario Silencio
| price_points Silencioso lista Silencio Usuario prompt Silencio No Silencio Precio en cada estadio de embudo Silencio

---

## Preconditions

- Tipo de embudo seleccionado con estrategia de monetización clara
- Unidad de oferta definida con al menos front-end y una subida
- La línea de productos soporta la arquitectura del embudo

---

## Fases de Ejecución

### Fase 1: Arquitectura de embudos
1. Mapea el flujo completo de embudo con páginas y correos electrónicos:
   - **Dibujo de imán de cuentas:** Opt-in → Gracias → Nurture Emails → Página de ventas
   - **Tripwire Funnel:** Opt-in → Oferta Tripwire → OTO1 → Gracias
   - **Dibujo web:** Registro → Confirmación → Recordar Correos → Webinar → Replay → Ventas
   - ** Embalaje de desafío:** Registro → Correos electrónicos diarios → Páginas diarias → Oferta
   - ** Alto truco: ** Aplicación → VSL/Case Estudio → Reserva de llamadas → Seguimiento
   - **Iniciación del producto:** Contenido pre-lanzamiento → Carrito abierto → Mid-Cart → Carrito
2. Defina el "puente epífanía" para cada punto de transición
3. Mapear la progresión de la escalera de valor a través del embudo
4. Identificar dónde entra cada nivel de conciencia en el embudo

## Fase 2: Escribir página Copiar
1. Escribir opt-in/registration página (véase el párrafo 1 del artículo 1 del anexo) write-landing-page.md formato)
2. Escribir confirmation/thank-you página con sorpresa e impulso
3. Escribe página de ventas o páginas OTO:
   - Mantener la continuidad de la página anterior
   - Cada página debe estar sola si llega directamente
   - Páginas OTO: corto, directo, "espera antes de ir" enmarcando
4. Escriba página de downsell (si es aplicable): versión reducida, precio más bajo
5. Escríbete thank-you/access página: confirmar compra, establecer expectativas, reducir el remordimiento del comprador

### Fase 3: Escribe correos electrónicos del embudo
1. Escriba correo electrónico de confirmación (entrega inmediata)
2. Escribir nurture/bridge correos electrónicos entre páginas (ver write-email-sequence.md formato)
3. Escribe correos electrónicos de abandono del carrito (si e-commerce embudo)
4. Escribir post-purchase correos electrónicos a bordo
5. Asegurar que el correo electrónico y la copia de la página sean consistentes en voz y promesa

### Fase 4: Notas de Optimización del embudo
1. Mapear las tasas de conversión previstas en cada etapa
2. Identificar los "puntos de fuga" críticos donde drop-off probablemente
3. Proporción de A/B prioridades de prueba para cada etapa de embudo
4. Sugerir copia de retargeting para cada abandono de fase
5. Calcular las matemáticas de embudo (traffic needed for target revenue)

---

## Formato de salida

```markdown
## Funnel Copy System: {Funnel Name}

**Type:** {funnel_type}
**Stages:** {count}
**Value Ladder:** {front-end} → {OTO1} → {OTO2}
**Target Revenue per Lead:** ${X}

---

### Funnel Map

{Visual text representation of funnel flow}

---

### Page 1: {Page Name}
**Type:** {opt-in / sales / OTO / thank-you}
**Goal:** {conversion action}
{Full page copy per landing page format}

---

### Page 2-N: ...

---

### Email Sequence: {Name}
{Emails per email sequence format}

---

### Funnel Math

| Stage | Expected CVR | Traffic Needed | Revenue |
|-------|-------------|----------------|---------|

### A/B Testing Priorities
| Priority | Stage | Element to Test | Hypothesis |
|----------|-------|----------------|------------|

### Retargeting Copy
{Copy for each abandonment stage}
```

---

## Condiciones de veto

- Nunca construir un embudo sin una progresión de escalera de valor claro
- Nunca escriban páginas OTO que contradicen front-end promesa de oferta
- Nunca saltes el thank-you página — previene el remordimiento del comprador y establece la próxima oferta
- Nunca crear un embudo con más de 2 upsells sin confirmación del usuario
- Nunca ignore las matemáticas - cada embudo debe haber proyectado las tasas de conversión

---

## Criterios de finalización

- [ ] Arquitectura de embudos mapeado con todas las páginas y correos electrónicos
[ ] Todas las páginas copia escritas por formato de página de aterrizaje
- [ ] Todas las secuencias de correo electrónico escritas por formato de correo electrónico
- [ ] Materias de embudo calculadas con tasas de conversión esperadas
- [ ] A/B prioridades de las pruebas definidas para cada etapa
- [ ] Copia de retargeting proporcionada para etapas de abandono
Voz y promesa consistentes en todo el embudo
- [ ] Progresión de escalera de valor es lógica y convincente
