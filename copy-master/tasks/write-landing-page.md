---
task: writeLandingPage()
responsavel: "@joe-sugarman"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: page_type
    tipo: enum
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: landing_page_copy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Meta de conversión única definida y mantenida" 
  - "[ ] Todas las secciones escritas por tipo de página arquitectura" 
  - "[ ] CTA aparece al menos 3 veces con action-oriented texto" 
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Write Landing Page Copy

** ID de la lista: * COPY-M-008
**Version:** 2.0.0
**Command:** `*write-landing-page`
* Agente Joe Sugarman (Agente Joe Sugarman)joe-sugarman)
**Purpose:** Escribe una copia de la página de aterrizaje que crea una diapositiva deslizante imparable desde el titular hasta el CTA, reforzado por la psicología de persuasión.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service ser ofrecido Silencio
Silencios Silencio Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio
| page_type Silencio en el futuro Silencio insinuar usuario opt-in, ventas, webinar-reg, camarera, producto, checkout 
Silencio oferta Silencioso objeto Silencio Usuario prompt Silencio Silencio Lo que el visitante consigue para tomar acción Silencio
| traffic_source Silencio Silencio Silencio Silencio Usuario prompt Silencio No Silencio Dónde vienen los visitantes (ads, email, orgánico, social) Silencio
| awareness_level Silencio enum Silencio Usuario prompt Silencio No Silencio Conciencia nivel de tráfico entrante Silencio
| page_length TENCIÓN TENIDO TENIDO ANTERIOR NO TENIDO (A)opt-in), medio (webinar), largo (sales) — auto-detected de tipo TENIDO

---

## Preconditions

- Tipo de página seleccionado con meta de conversión clara
- Oferta definida (incluso para opt-in páginas — ¿qué obtienen?)
- Fuente de tráfico identificada para calibrar la conciencia y la mensajería

---

# Champion Reference

Estudiar estos real-world campeón de landing pages antes de escribir:

1. ** Página de la destilería de Boston** — Simple, benefit-driven, prueba social pesada, tono conversacional, sola CTA repetido
2. **Ramitir las páginas de venta de larga duración de Sethi** (IWT) — Manejo de objeción de gran densidad, con frecuencia, voz de personalidad en todas partes
3. **Paginas de entrada de los canales** (Russell Brunson) — Copia mínima, gancho claro, "libre + envío" oferta framing
4. **Agora Financial Advertorials** — Páginas de aterrizaje traducidas por historia disfrazadas de contenido editorial, masiva cold-traffic convertidores
5. ** Páginas de Copiadoras de Joanna Wiebe** — copia optimizada de CRO, micro-copy mastery, botón texto A/B disciplina de ensayo

---

## Fases de Ejecución

## Phase 1: Page Strategy
1. Definir el único objetivo de conversión (una página, una acción)
2. Identificar el estado de ánimo del visitante cuando lleguen:
   - De anuncio frío: escéptico, curioso, bajo confianza
   - De correo electrónico: caliente, algo confiado, esperando lo que se prometió
   - De la orgánica: modo de investigación, comparando opciones
3. Mapear la "slippery slide" — cada elemento debe tirar hacia el CTA
4. Decide la arquitectura de la página basada en el tipo:
   - Opt-in: Headline - título Benefit bullets - título Forma - título CTA (short)
   - Ventas: AIDA completa con secciones de prueba (long)
   - reg: Headline - confiar Lo que aprenderás - Confeccionista Cred - confianza Date/Time - título CTA (medio)

## Fase 2: Capa Psicológica
1. Mapa Cialdini principios en secciones de página:
   - **Hero:** Autoridad (creenciales) o Prueba Social (conteo de usuarios)
   -Problema: ** El amor (comprensión compartida de su lucha)
   - **Solución:** Compromiso (pequeño acuerdo antes de la gran pregunta)
   - **Proof:** Social Proof (testimonios, logos, números)
   - **Offer:** Reciprocidad (valor de bonos excede el precio) + Escasa (oferta limitada)
   - **CTA: ** Unidad ("juntarnos") + Compromiso (texto de botón como micro-commitment)
2. Aplicar las palancas de Blair Warren:
   - Sección de héroes: Anime sueños o Confirme sospechas
   - Sección de problemas: justifica los fracasos
   - Sección de Solución: Teme a Allay
   - Sección CTA: Anime los sueños (estado de futuro después de hacer clic)
3. Diseño micro-copy abajo botones usando fear-reduction idioma (Cialdini: reversión de riesgos)

## Fase 3: Escribir la sección por sección
1. **Sección de Hero:** sub-headline + héroe CTA
   - El titular debe hacer el 80% de la venta
   - Subcabeza aclara o amplifica
   - Hero CTA para ready-to-act visitantes
2. **Sección del problema:** Agitar el dolor actual
   - Usar el lenguaje "tú" - hacerlo personal
   - 3-5 puntos de dolor específicos que el público reconoce
3. ** Sección de la Solución**: Introducir product/mechanism
   - Puente de problema a solución natural
   - Nombrar el mecanismo o la metodología
4. ** Sección de Beneficios:** Beneficios de la pila con especificidad
   - Use iconos o marcadores para la escandalidad
   - Cada beneficio responde "¿qué hay en él para mí?"
5. ** Sección de Pruebas:** Prueba social y credibilidad
   - Testimonios, logos, estadísticas, menciones de medios
   - Colocar estratégicamente (no todos en una cuadra)
6. ** Sección de Servicios:** Lo que obtienen (si página de ventas)
   - Apilar el valor con los productos claros
   - Incluye bonos, garantía, precio
7. **Sección del FFAQ:**
   - 5-7 preguntas que abordan las dudas reales
8. **CTA Final:** Último empujón con urgencia

### Fase 4: Optimización de Conversión
1. Asegurar que el CTA aparezca como mínimo 3 veces en la página
2. Escriba el texto del botón como action-oriented primera persona ("Obtener mi guía libre")
3. Add micro-copy abajo botones para reducir la ansiedad
4. Revisar la página para "puntos de salida" — todo lo que pueda perder al visitante
5. Add mobile-specific consideraciones (párrafos de corto alcance, objetivos de mayor tamaño del CTA)

---

## Formato de salida

```markdown
## Landing Page Copy: {Page Name}

**Type:** {page_type}
**Goal:** {single conversion action}
**Traffic Source:** {source}
**Awareness Level:** {level}

### Persuasion Architecture
| Section | Cialdini Principles | Warren Levers |
|---------|--------------------|--------------  |
| Hero | {principles} | {levers} |
| Problem | {principles} | {levers} |
| Solution | {principles} | {levers} |
| Proof | {principles} | {levers} |
| Offer | {principles} | {levers} |
| CTA | {principles} | {levers} |

---

### [HERO SECTION]
**Headline:** {headline}
**Sub-headline:** {sub-headline}
**CTA Button:** {button text}
**Micro-copy:** {below-button text}

### [PROBLEM SECTION]
{Problem agitation copy}

### [SOLUTION SECTION]
{Solution introduction copy}

### [BENEFITS SECTION]
{Benefits with formatting notes}

### [PROOF SECTION]
{Testimonial placeholders and social proof copy}

### [OFFER SECTION]
{Value stack and pricing — if sales page}

### [FAQ SECTION]
{5-7 Q&A pairs}

### [FINAL CTA SECTION]
{Closing argument + CTA}

---

### Conversion Notes
- **CTA count:** {X placements}
- **Estimated page length:** {scroll depth}
- **Key anxiety reducers:** {list}
- **Mobile considerations:** {list}
- **Cialdini principles per section:** {summary}
```

---

## Condiciones de veto

- Nunca dar la página más de un objetivo de conversión
- Nunca escriba una página de aterrizaje sin un héroe CTA por encima del pliegue
- Nunca use enlaces de navegación - el único elemento clicable debe ser el CTA
- NUNCA escriba respuestas de preguntas frecuentes que introducen nuevas objeciones
- NUNCA ignorar la fuente de tráfico - las páginas de tráfico frío son fundamentalmente diferentes del calor

---

## Criterios de finalización

- [ ] Un objetivo de conversión único definido y mantenido en todo el mundo
Todas las secciones escritas por tipo de página arquitectura
- [ ] CTA aparece al menos 3 veces
El texto de Button es action-oriented primera persona
- [ ] elementos de prueba estratégicamente colocados
- [ ] FAQ maneja objeciones reales
- [ ] Consideraciones móviles señaladas
- [ ] deslizamiento deslizante mantenido - no puntos de salida
- [ ] Capa Psicológica aplicada - Principios Cialdini mapeados por sección
- [ ] Blair Warren palancas identificadas por sección
