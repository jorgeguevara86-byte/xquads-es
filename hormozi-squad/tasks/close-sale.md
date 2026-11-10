---
task: closeSale()
responsavel: "@hormozi-closer"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: price
    tipo: number
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: closingFramework
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Todos los 6 pasos CLOSER scripted para el producto específico" 
  - "[ ] 10 objeciones más importantes manejadas con respuestas de aislamiento y sobrecomiso" 
  - "[ ] Blancos KPI fijados" 
---

# Task: Close Sale

** ID de usuario: **HORMOZI-004
**Version:** 1.0.0
**Command:** `*close-sale`
**Agente:** Hormozi Closer (hormozi-closer)
**Purpose:** Diseñar un marco de cierre utilizando el método CLOSER para conversaciones de ventas.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service ser vendido Silencio
TENIDO precio TENIDO número TENIDO Usuario prompt TENSI TENIDO Precio punto de la oferta TENIDO
| sales_context Silencio enum Silencio Usuario prompt Silencio Sí Silencio teléfono, zoom, in-person, DM, chat Silencio
Silencios Silencio Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio Prospect profile Silencio
| common_objections Silencioso lista Silenciosidad de usuario no Silencio No Silencio Conozca las objeciones de ventas anteriores Silencio
| conversion_rate Silencio número Silencio Usuario prompt Silencio No Silencio Tarifa cercana actual si se conoce Silencio

---

## Preconditions

- Oferta definida con proposición de valor claro
- Punto de precio
- Establecimiento de un contexto de ventas (teléfono, vídeo, in-person)

---

## Fases de Ejecución

## Fase 1: Configuración del Marco CLOSER
1. Mapa de cada paso del marco CLOSER al producto específico:
   **C - Clarify:** Preguntas para entender su situación actual
   *L — Label* *Restablece su problema para que se sientan comprendidas
   * * * * * Resúmenes*:* Presentar el camino desde donde están hasta donde quieren estar
   **S — Vender la Vacación:** Vender el resultado, no el proceso
   **E - Explicar Preocupaciones por la vía:** Objeciones de mano antes de que surjan
   **R - Refuerzo y cierre:** Preguntar por la decisión
2. Escribe 3-5 preguntas de descubrimiento para el paso Clarify
3. Preparar las declaraciones de etiquetado para situaciones comunes
4. Construir la narrativa de visión general (3 pasos puente de dolor a solución)

### Fase 2: Manejo de Objeciones
1. Listar las 10 principales objeciones para este punto de precio y producto
2. Para cada objeción, prepare la respuesta "Isolado y sobrecomerto":
   - "Lo entiendo totalmente. {objection}¿Hay algo más?"
   - "Si pudiéramos resolver {objection}¿Estarías listo para avanzar?"
   - Retrocedimiento o evidencia específica para disolver la objeción
3. Preparar respuestas para las 4 objeciones universales:
   - "Necesito pensar en ello" → La urgencia basada en el tiempo + valor de recaptura
   - "No puedo permitirlo" → Costo de la inacción + opciones de pago
   - "Necesito hablar con mi spouse/partner" → Traigan o obtengan un compromiso condicional
   - "Me quemé antes" → Garantía + diferenciación de fracasos pasados
4. Crear el marco de "caminar lejos" para las perspectivas que no son un ajuste

### Fase 3: Desarrollo de scripts
1. Escribe el script de apertura (opporto + configuración de agenda)
2. Escribe la secuencia de preguntas Clarify con puentes de transición
3. Escribir la plantilla de declaraciones de etiqueta
4. Escribe la presentación general (pasaje de tres pasos)
5. Escribe la sección de venta de vacaciones (pintura de salida)
6. Escribir la sección Explicar (maneje de objeción preventiva)
7. Escribe la sección Reforzar y Cerrar con el lenguaje de cierre exacto
8. Escribe el post-close script de confirmación (reducir remordimiento del comprador)

## Fase 4: Marco de ejecución
1. Definir los KPI: tasa de show, tasa de cierre, valor promedio de acuerdo
2. Crear una rúbrica de renombre para llamadas self-evaluation
3. Construir un follow-up secuencia para non-closes
4. Diseño de la estrategia de recuperación "pérdida"
5. Establecer objetivos para la tasa de conversión de cada paso

---

## Formato de salida

```markdown
## Sales Closing Framework: {Product Name}

**Method:** CLOSER
**Price:** ${price}
**Context:** {sales_context}
**Target Close Rate:** {X}%

---

### CLOSER Script

#### C — Clarify
{Discovery questions with transitions}

#### L — Label
{Labeling statement templates}

#### O — Overview
{3-step bridge narrative}

#### S — Sell the Vacation
{Outcome painting script}

#### E — Explain Away Concerns
{Preemptive objection handling}

#### R — Reinforce and Close
{Closing language and assumptive close}

---

### Objection Handling Matrix

| Objection | Isolate | Reframe | Evidence |
|-----------|---------|---------|----------|

### Post-Close Script
{Confirmation and next steps}

### Follow-Up Sequence (Non-Close)
| Day | Action | Message |
|-----|--------|---------|

### KPI Targets

| Metric | Target | Current |
|--------|--------|---------|
```

---

## Condiciones de veto

- NUNCA salta el paso Clarify - vender sin entender es lanzar
- Nunca maneje una objeción sin aislarla primero
- Nunca presionar a alguien que no es un ajuste - calificar con gracia
- NUNCA precio presente antes de establecer valor (Sell la Vacación debe venir primero)
- Nunca cerrar sin un paso claro de la siguiente definición

---

## Criterios de finalización

- [ ] Todos los 6 pasos CLOSER scripted para el producto específico
- [ ] 10 objeciones más importantes manejadas con respuestas de aislamiento y sobrecomiso
- [ ] 4 objeciones universales preparadas
- [ ] Abrir y cerrar scripts escritos
- [ ] script de confirmación de posterior-close incluido
- Secuencia de seguimiento para non-closes definida
- [ ] Blancos KPI fijados
