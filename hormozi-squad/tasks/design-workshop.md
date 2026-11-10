---
task: designWorkshop()
responsavel: "@hormozi-workshop"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: topic
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: duration
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: workshopDesign
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Promesa de transformación única definida" 
  - "[ ] 3-5 módulos de enseñanza diseñados con marcos y ejercicios" 
  - "[ ] Ejecutar el espectáculo creado con el tiempo" 
---

# Task: Design Workshop

** ID de usuario: **HORMOZI-008
**Version:** 1.0.0
**Command:** `*design-workshop`
**Agente:** Taller de Hormozi (Hormozi)hormozi-workshop)
**Purpose:** Diseñar un taller que ofrezca un valor masivo y convierta a los asistentes en compradores.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
TENEDO TENEDO TENIDO TENIDO TENIDO TERRITORIO TENIDO Y LA VOLVERSIÓN
Silencios Silencio Silencio Silencio Silencio Silencio Silencio Silencio
tención duración Silencio cadena Silenciosos Usuarios prompt Silencio Sí Silencio 60min, 90min, half-day, full-day, multi-day |
tención formato Silencio enum Silencio Sugerencia de usuario Silencio Sí Silencio virtual, in-person, híbrido Silencio
| backend_offer Silencioso objeto Silencio Usuario prompt Silencio No Silencio Lo que usted vende al final (si taller de conversión) Silencio
Silencio precio Silencio número Silencio Usuario prompt Silencio No Silencio Taller ticket price (0 for free) Silencio
Silencio Silencio Silencio número Silencio Usuario prompt Silencio No Silencio Max attendees Silencio

---

## Preconditions

- Experiencias temáticas disponibles para entregar el contenido
- Si taller de conversión: la oferta de backend debe definirse

---

## Fases de Ejecución

### Fase 1: Arquitectura Taller
1. Defina la promesa de transformación única ("Por el final de este taller, usted lo hará...")
2. Elija el modelo del taller:
   - Valor puro: Sin parcela, construcción de marca y relación
   - Valor + Oferta: 80% de enseñanza, 20% de transición para ofrecer
   - Implementación: Manos a mano donde construyen algo vivo
3. Estructurar los bloques de contenido:
   - Apertura: Gancho + promesa + agenda (10% de tiempo)
   - Bloques de enseñanza: 3-5 módulos básicos (70% del tiempo)
   - Implementation/exercises: Aplicación a mano (encaminada en la enseñanza)
   - Cerrar: Recapitulación + CTA o ofrecer transición (20% de tiempo)
4. Para cada bloque de enseñanza, definir el "momento de la acción" — ¿qué se darán cuenta?

Fase 2: Diseño de contenidos
1. Para cada bloque de enseñanza:
   - Gran idea (un concepto por bloque)
   - Marco o modelo para enseñarlo
   - Ejemplo o estudio de caso para ilustrar
   - Paso de ejercicio o aplicación
   - Transición a siguiente bloque
2. Diseñar el "revelación de los cuadros" — darles un marco patentado
3. Crear hojas de trabajo o plantillas que los asistentes utilizarán
4. Construir puntos de interacción cada 10-15 minutos:
   - Preguntas para el público
   - Incitaciones de compromiso de chat
   - Ejercicios rápidos
   - Polígrafos de votación o votación
5. Planifique el arco energético: comience fuerte, variando ritmo, termine en un pico

### Fase 3: Diseño de Conversión (si es aplicable)
1. Planta "semillas" a lo largo de la enseñanza que apuntan a la oferta:
   - "En mi programa, vamos más allá de esto..."
   - "Mis clientes consiguen un done-for-you versión de este..."
2. Diseñar la transición de la enseñanza a la oferta (el "puente"):
   - Recapitular la transformación que experimentaron
   - Determinar la brecha entre los conocimientos prácticos y la plena aplicación
   - Colocar la oferta como puente para cerrar esa brecha
3. Estructurar la presentación de la oferta:
   - Reafirme el resultado del sueño
   - Revela la oferta y lo que incluye
   - Apilar el valor
   - Presentar el precio con anclaje
   - Maneja las 3 objeciones principales
   - ALC con urgencia
4. Planificar el follow-up para non-buyers

## Fase 4: Logística y Entrega
1. Crear el run-of-show con el tiempo exacto
2. Definir los requisitos tecnológicos (plataforma, herramientas, diapositivas, chat)
3. Planificar la secuencia de registro y recordatorio
4. Crear el post-workshop follow-up plan
5. Definir las métricas de éxito (tasa de asistencia, compromiso, conversión si procede)

---

## Formato de salida

```markdown
## Workshop Design: {Workshop Name}

**Promise:** "By the end, you will {transformation}"
**Duration:** {time}
**Format:** {format}
**Model:** {pure-value / value+offer / implementation}
**Capacity:** {N}

---

### Run of Show

| Time | Block | Content | Energy Level |
|------|-------|---------|-------------|
| 0:00-{X} | Opening | {hook + promise} | High |
| {X}-{Y} | Module 1 | {topic} | Medium |
| ... | ... | ... | ... |
| {Z}-END | Close/Offer | {recap + CTA} | Peak |

### Module Details

#### Module 1: {Title}
**Big Idea:** {concept}
**Framework:** {framework name}
**Example:** {case study}
**Exercise:** {what they do}
**Aha Moment:** {realization}

#### Module 2-N: ...

### Worksheets/Templates
| Resource | Purpose | When Used |
|----------|---------|-----------|

### Conversion Plan (if applicable)
**Seeds planted in:** {modules}
**Bridge script:** {transition language}
**Offer presentation:** {structure}
**Follow-up plan:** {non-buyer sequence}

### Registration and Reminders
| Timing | Communication | Channel |
|--------|--------------|---------|

### Success Metrics
| Metric | Target |
|--------|--------|
```

---

## Condiciones de veto

- Nunca diseña un taller sin una simple promesa de transformación clara
- NUNCA enseña más de 5 conceptos básicos - la profundidad late la anchura
- Nunca más de 15 minutos sin interacción con el público
- NUNCA lanza antes de entregar valor sustancial (mínimo 60% enseñanza pura)
- NUNCA salta el arco energético - los talleres de monotona pierden gente

---

## Criterios de finalización

- Una promesa de transformación definida
- [ ] Modelo de taller seleccionado
- [ ] 3-5 módulos de enseñanza diseñados con marcos y ejercicios
- [ ] Ejecutar el espectáculo creado con el tiempo
- [ ] Puntos de interacción planeados cada 10-15 minutos
- [ ] Plan de conversión diseñado (si es aplicable)
- [ ] Worksheets/templates created
- Registro y registro follow-up secuencias planificadas
- [ ] Metrices de éxito definidas
