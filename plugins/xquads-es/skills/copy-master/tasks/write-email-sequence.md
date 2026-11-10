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
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Write Email Sequence

** ID de la lista: * COPY-M-004
**Version:** 2.0.0
**Command:** `*write-email-sequence`
*Agente* *André Chaperon*andre-chaperono Ben Settle (ben-settle)
**Purpose:** Escribe secuencias de correo electrónico que construyen relaciones y impulsan la acción a través de la psicología de narración serializada y persuasión.

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

# Champion Reference

Estudiar estos real-world campeón de las secuencias de correo electrónico antes de escribir:

1. **Secuencias de la Opera de Salto de Andre Chaperon** (Locura de AutoResponder) — El estándar de oro para narrar el email serializado con bucles abiertos anidados
2. **El estilo de correo electrónico diario de Ben Settle** (Email Players) — Anti-guru, personality-driven correos electrónicos diarios que venden sin vender
3. **La secuencia de cuatro días de Frank Kern "4 Day Cash Machine"** — secuencia de 4 mensajes de correo electrónico que generó millones en 4 días, estructura de correo electrónico de lanzamiento de libros de texto
4. **Deiss Ryan / DigitalMarketer Welcome Sequence** — Serie de indoctrinamiento que construye confianza en 5 emails antes de cualquier lanzamiento
5. **El carro de Rintz Close Emails** (Agora Financial) — secuencias emocionales de transmisión en línea fija que combinan urgencia con cambios de creencias

---

## Fases de Ejecución

### Fase 1: Arquitectura de secuencia
1. Definir el arco narrativo a través de la secuencia completa
2. Mapa email-by-email propósito utilizando el marco de secuencia:
   - **Soap Opera:** Garganta - confianza Backstory - confianza Epiphany - confianza ocultado Beneficios - confianza Urgency
   - **Día:** E-mails de valor independiente con ventas suaves incrustadas
   *Nurture:** Education - confiar en confianza - autoridad de confianza - Puente de confianza para ofrecer
   - **Launch:** Anticipación - valor de confianza - propiedad Social Proof - propiedad Objeción Handling - confianza Cesta Open - confianza FAQ - estrecho
   - **Bienvenido:** Gratitud - confianza Quick Win - confianza Historia - confianza Esperaciones - confianza Siguiente Paso
   - **Cart Abandon:** Recordder - Objeción de títulos Handle - Confía Final Urgency
3. Asignar un tema emocional por correo electrónico
4. Planifique los bucles abiertos entre correos electrónicos (técnica de firma de Chaperon)

## Fase 2: Capa Psicológica
1. Mapa Cialdini principios a través del arco de secuencia:
   - **Emails externos:** Reciprocidad (valor libre), Alegría (historias personales)
   **Emails mínimos:** Proofo Social (testimonios), Autoridad (creenciales)
   - **Emails más recientes:** Escarta (deadline), Compromiso (invirtieron la lectura del tiempo)
   - **A lo largo de:** Unidad (identidad compartida y valores)
2. Aplicar las palancas de Blair Warren por correo electrónico:
   - Welcome/Nurture: Anime sueños, Teme Allay
   - E-mails de historia: Justificar fallos, confirmar sospechas
   - Vender correos electrónicos: Tire piedras a los enemigos (la antigua manera), Anime los sueños (la nueva manera)
3. Asegurar que cada email active al menos 1 principio Cialdini
4. Etiqueta cada correo electrónico con su conductor psicológico primario

### Fase 3: Escribe cada correo electrónico
1. Escriba líneas de asunto (2 opciones por correo electrónico, una curiosity-based, uno benefit-based)
2. Escribe texto de vista previa que complementa (no repite) la línea de asunto
3. Escriba el cuerpo de correo electrónico siguiendo el one-email-one-idea Regla
4. Abra cada correo electrónico con un gancho que gana la siguiente frase
5. Cierre cada correo electrónico con un bucle abierto (mid-sequence) o CTA (emails de venta)
6. Mantener voz consistente en todo el mundo — el lector debe sentir que conocen al remitente
7. Incluir líneas P.S. en la venta de correos electrónicos

### Fase 4: Optimización de secuencias
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

### Persuasion Map
| Email # | Cialdini Principle | Warren Lever | Emotional Theme |
|---------|-------------------|--------------|-----------------|

---

### Email 1: {Title}
**Send:** {timing — e.g., Immediately, Day 1}
**Subject A:** {subject line option 1}
**Subject B:** {subject line option 2}
**Preview:** {preview text}
**Purpose:** {purpose in the sequence}
**Open Loop:** {what loop is planted or resolved}
**Psychology:** {Cialdini principle + Warren lever}

{Full email body}

P.S. {if applicable}

---

### Email 2: {Title}
...

---

### Sequence Map

| # | Title | Purpose | Emotion | Open Loop | CTA | Cialdini | Warren |
|---|-------|---------|---------|-----------|-----|----------|--------|

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
- [ ] Capa Psicológica aplicada - Principios Cialdini mapeados por correo electrónico
Blair Warren se identifica por correo electrónico
