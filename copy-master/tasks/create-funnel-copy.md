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
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Create Funnel Copy

** ID de la lista: * COPY-M-009
**Version:** 2.0.0
**Command:** `*create-funnel-copy`
**Agente: ** Russell Brunson (Rusell Brunson)russell-brunson)
**Purpose:** Escribe copia para todo un sistema de embudos: desde opt-in a través de upsell — con la psicología de persuasión tejida a lo largo de todo.

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

# Champion Reference

Estudiar estos real-world campeones embudos antes de escribir:

1. **ClicFunnels "libre + envío" Book Funnel** (Russell Brunson) — Opt-in - título Tripwire book - título OTO course - Conf High-ticket coaching, la escalera de valor en acción
2. **Marcador digital "Máquina de venta invisible"** (Ryan Deiss) — embudo triple con escalera de alta velocidad automática de email, libro de texto email-to- Flujo de OTO
3. **Tai López "67 Pasos" Webinar Funnel** — Webinar reg - confianza Replay - confianza Core offer - confiar High-ticket upsell, escalada a 8 figuras
4. **Jeff Walker's Product Launch Formula** — Pre-launch content - Confectar Cesta open - ConfUrgency sequence, pionera el modelo de embudo de lanzamiento
5. **Dibujo de informe financiero de la Agora**: Informe gratuito opt-in - Noticias de estreno Upsell - confianza Backend high-ticket asesoría longest-running Arquetipo de embudo

---

## Fases de Ejecución

### Fase 1: Arquitectura de embudos
1. Mapea el flujo completo de embudo con páginas y correos electrónicos:
   - **Dibujo de imán de cuentas:** Opt-in - Confía en Gracias - Nurture Emails - Empezar página de ventas
   - **Tripwire Funnel:** Opt-in - confianza Tripwire Offer - Confes OTO1 - confianza OTO2 - confianza Gracias
   - **Dibujo web:** Registro - Confirmación de títulos - confianza Reminder Emails - confianza Webinar - confianza Replay - ventas de título
   - **Dibujo de desafío:** Registro - Campos Elíseos diarios - Confía en Páginas diarias - Ofertas de empleo
   - ** Alto-Ticket:** Aplicación - título VSL/Case Study - titulado Call Booking - confianza Follow-up
   **Iniciación del producto:** Contenido prelanzamiento - confianza Carrito abierto - confiar Mid-Cart - estrecho
2. Defina el "puente epífanía" para cada punto de transición
3. Mapear la progresión de la escalera de valor a través del embudo
4. Identificar dónde entra cada nivel de conciencia en el embudo

## Fase 2: Capa Psicológica
1. Mapa Cialdini principios en etapas de embudo:
   - **Opt-in/Registration:** Reciprocidad (valor libre para el correo electrónico)
   - **Gracias / Tripwire:** Compromiso (la pequeña compra construye consistencia para los más grandes)
   - **Emails de la naturaleza:** El gusto (historias personales), Autoridad (creenciales)
   - **Página de ventas / OTO:** Proofo Social (testimonios, números), Escarta (oferta limitada)
   - ** Páginas de Upsell:** Consistencia (ya compraban — este es el siguiente paso lógico)
   - *Post-purchase* *Unidad (bienvenida a la tribu)
2. Aplicar las palancas de Blair Warren en los puntos clave de transición:
   - Opt-in: Anime los sueños (promise la transformación)
   - Tripwire: Temidos de Allay (bajo riesgo, alto valor)
   - OTO: Confirme sospechas (necesita esta pieza extra para tener éxito)
   - Carro cerrado: Tire piedras a los enemigos (la vieja manera que te falló)
3. Asegurar que cada página de embudo active al menos 2 principios psicológicos distintos

## Fase 3: Escribir página Copiar
1. Escribir opt-in/registration página (véase el párrafo 1 del artículo 1 del anexo) write-landing-page.md formato)
2. Escribir confirmation/thank-you página con sorpresa e impulso
3. Escribe página de ventas o páginas OTO:
   - Mantener la continuidad de la página anterior
   - Cada página debe estar sola si llega directamente
   - Páginas OTO: corto, directo, "espera antes de ir" enmarcando
4. Escriba página de downsell (si es aplicable): versión reducida, precio más bajo
5. Escríbete thank-you/access página: confirmar compra, establecer expectativas, reducir el remordimiento del comprador

### Fase 4: Escribe correos electrónicos del embudo
1. Escriba correo electrónico de confirmación (entrega inmediata)
2. Escribir nurture/bridge correos electrónicos entre páginas (ver write-email-sequence.md formato)
3. Escribe correos electrónicos de abandono del carrito (si e-commerce embudo)
4. Escribir post-purchase correos electrónicos a bordo
5. Asegurar que el correo electrónico y la copia de la página sean consistentes en voz y promesa

## Fase 5: Notas de Optimización de embudos
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
**Value Ladder:** {front-end} -> {OTO1} -> {OTO2}
**Target Revenue per Lead:** ${X}

### Persuasion Architecture
| Funnel Stage | Cialdini Principles | Warren Levers |
|-------------|--------------------|--------------  |
| Opt-in | {principles} | {levers} |
| Tripwire/OTO | {principles} | {levers} |
| Sales Page | {principles} | {levers} |
| Post-Purchase | {principles} | {levers} |

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
- [ ] Capa Psicológica aplicada - Principios Cialdini mapeados por estadio de embudo
- Blair Warren se activa en los puntos clave de transición
