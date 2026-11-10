---
task: writeEmailSequence()
responsavel: "@andre-chaperon"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: sequence_type
    tipo: enum
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: email_sequence
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Marco tipo de secuencia correctamente aplicado" 
  - "[ ] Todos los correos electrónicos escritos con líneas de doble sujeto" 
  - "[ ] Ámbitos abiertos plantados y resueltos a través de secuencia" 
---

# Task: Write Email Sequence

** ID de la lista:** COPY-004
**Version:** 1.0.0
**Command:** `*write-email-sequence`
*Agente* *André Chaperon*andre-chaperono Ben Settle (ben-settle)
**Purpose:** Escribe secuencias de correo electrónico que construyen relaciones y conducen la acción a través de narración serializada.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service ser promovido TEN ANTE
Silencio audiencia Silencio Silencio Silencio Sugerencia de usuario Silencio Suscripción perfil y estado emocional Silencio
| sequence_type Silencio en el futuro Silencio insinuar usuario soap-opera, diario, nutrido, lanzamiento, bienvenido, cart-abandon |
| num_emails TENN NÚMERO TENIDO NO TENIDO Por tipo: soap-opera=5, diariamente=7, nurture=10, lanzamiento=7, bienvenido=5, cart-abandon=3 |
Silencio oferta Silencioso objeto Silencioso de usuario inducido por Silencio No Silencio soap-opera y tipos de lanzamiento TEN
| brand_voice TENED TENIDO TENIDO ANTERIOR NO TENIDO Tono y personalidad del remitente TEN
| entry_point Silencio Silencio Silencio Silencio Silencio No Silencio opt-in o acción desencadenaron esta secuencia TEN

---

## Preconditions

- Tipo de secuencia seleccionada con gol claro (vesel, nurtura, a bordo, recuperar)
- Puntos de dolor de audiencia y deseos identificados
- Para soap-opera y tipos de lanzamiento: la oferta debe definirse

---

## Fases de Ejecución

### Fase 1: Arquitectura de secuencia
1. Definir el arco narrativo a través de la secuencia completa
2. Mapa email-by-email propósito utilizando el marco de secuencia:
   - **Soap Opera:** Hook → Backstory → Epifanía → Beneficios ocultos → Urgency
   - **Día:** E-mails de valor independiente con ventas suaves incrustadas
   - **Nurtura:** Educación → Confianza → Autoridad → Puente para ofrecer
   - **Launch:** Anticipación → Valor → Proof → Proofo Social → Manejo de la objeción → Carrito Abierto →
   - **Bienvenido:** Gratitud → Ganar rápido → Historia → Expectativas → Próximo paso
   - **Cart Abandon:** Recordar → Mango de Objeción → Urgency Final
3. Asignar un tema emocional por correo electrónico
4. Planifique los bucles abiertos entre correos electrónicos (técnica de firma de Chaperon)

### Fase 2: Escribe cada correo electrónico
1. Escriba líneas de asunto (2 opciones por correo electrónico, una curiosity-based, uno benefit-based)
2. Escribe texto de vista previa que complementa (no repite) la línea de asunto
3. Escriba el cuerpo de correo electrónico siguiendo el one-email-one-idea Regla
4. Abra cada correo electrónico con un gancho que gana la siguiente frase
5. Cierre cada correo electrónico con un bucle abierto (mid-sequence) o CTA (emails de venta)
6. Mantener voz consistente en todo el mundo — el lector debe sentir que conocen al remitente
7. Incluir líneas P.S. en la venta de correos electrónicos

## Fase 3: Optimización de secuencia
1. Revisar el arco emocional - ¿La tensión se acumula a través de la secuencia?
2. Verificar los lazos abiertos se plantan y se resuelven en los momentos correctos
3. Compruebe que ningún email se siente como un independiente - cada uno debe referenciar el hilo
4. Añada recomendaciones de tiempo de envío (la demora entre correos electrónicos)
5. Sugerir desencadenantes de segmentación (clics de enlace, se abre, no-opens)

---

## Formato de salida

```markdown
## Email Sequence: {Name}

**Type:** {sequence_type}
**Emails:** {count}
**Goal:** {sell / nurture / onboard / recover}
**Audience:** {audience}
**Narrative Arc:** {one-line arc description}

---

### Email 1: {Title}
**Send:** {timing — e.g., Immediately, Day 1}
**Subject A:** {subject line option 1}
**Subject B:** {subject line option 2}
**Preview:** {preview text}
**Purpose:** {purpose in the sequence}
**Open Loop:** {what loop is planted or resolved}

{Full email body}

P.S. {if applicable}

---

### Email 2: {Title}
...

---

### Sequence Map

| # | Title | Purpose | Emotion | Open Loop | CTA |
|---|-------|---------|---------|-----------|-----|

### Send Schedule
{Timing recommendations with rationale}

### Segmentation Triggers
{Behavioral triggers and branch recommendations}
```

---

## Condiciones de veto

- Nunca escriba correos electrónicos que puedan leerse en cualquier orden para soap-opera secuencias — la serialización es obligatoria
- Nunca enviar un email de venta antes de al menos 2 value/story correos electrónicos en secuencias de nutricion
- Nunca escriba líneas de asunto más de 50 caracteres
- Nunca saltes los lazos abiertos. soap-opera secuencias — son el motor de la interacción
- Nunca use el mismo tono emocional en correos electrónicos consecutivos

---

## Criterios de finalización

- [ ] Marco tipo secuencial correctamente aplicado
- [ ] Todos los correos electrónicos escritos con líneas de doble sujeto
El arco narante crea tensión a través de la secuencia
- [ ] Ámbitos abiertos plantados y resueltos adecuadamente
Cada correo electrónico sigue one-email-one-idea Regla
- [ ] Enviar recomendaciones de tiempo proporcionadas
- [ ] Segmentation triggers suggested
- [ ] Voz de marca consistente mantenida en todo
