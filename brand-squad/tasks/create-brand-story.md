---
task: createBrandStory()
responsavel: "@donald-miller"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: problem
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "StoryBrand BrandScript" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Los 7 elementos SB7 definidos" 
  - "[ ] Se creó un discurso breve y de ascensor" 
  - "[ ] Copia de estructura alámbrica del sitio web proporcionada" 
---

# Tarea: Crear historia de marca

**ID de tarea:** MARCA-004
**Version:** 1.0.0
**Command:** `*create-brand-story`
**Agente:** Donald Miller (donald-miller)
**Propósito:** Construir una narrativa de marca utilizando StoryBrand SB7 Framework.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| marca | cadena | Mensaje de usuario | Sí | Nombre de la marca y qué hace |
| audiencia | cadena | Mensaje de usuario | Sí | Cliente objetivo y su mundo |
| problema | cadena | Mensaje de usuario | Sí | El problema que resuelve la marca |
| solución | cadena | Mensaje de usuario | Sí | Cómo lo soluciona la marca |
| brand_values | lista | Mensaje de usuario | No | Valores y creencias fundamentales |
| founder_story | cadena | Mensaje de usuario | No | Historia del origen del founder/company |
| proof_elements | lista | Mensaje de usuario | No | Testimonios, resultados, credenciales |

---

## Preconditions

- Posicionamiento de marca definido (lo que representa la marca)
- Se comprenden los deseos y temores del público objetivo.

---

## Fases de Ejecución

### Fase 1: StoryBrand BrandScript (SB7)
1. Defina cada uno de los 7 elementos:
   - **Un personaje:** El cliente es el héroe, no la marca. Defina quiénes son y qué quieren.
   - **Tiene un problema:** Defina el villano (la causa raíz) y 3 niveles de problema:
     - Externo: El problema tangible, surface-level 
     - Interno: Cómo les hace sentir el problema
     - Filosófico: Por qué esto está simplemente mal
   - **Conoce a un guía:** Posiciona la marca como el guía sabio que ha estado allí. Expresar:
     - Empatía: "Entendemos por lo que estás pasando"
     - Autoridad: "Tenemos la experiencia para ayudar"
   - **Quién les da un plan:** Proporcione un plan simple de 3 pasos:
     - Paso 1: {action} — Lo que el cliente hace primero
     - Paso 2: {action} — ¿Qué sucede a continuación?
     - Paso 3: {action} — El paso final hacia el resultado
   - **Y los llama a la acción:** Defina el CTA directo y el CTA de transición:
     - Directo: "Compra ahora", "Programa una llamada", "Regístrate"
     - Transicional: "Descargar la guía", "Ver el video", "Hacer el cuestionario"
   - **Eso les ayuda a evitar el fracaso:** ¿Cómo es la vida si NO actúan? Pinta lo que está en juego negativo.
   - **Y termina en éxito:** ¿Cómo es la vida cuando tienen éxito? Pinta la transformación positiva.

### Fase 2: Ejecución de la historia
1. Escribe el one-liner (logline de la marca):
   - Problema + Solución + Resultado en una frase
   - Debe ser lo suficientemente memorable como para repetirlo en una cena.
2. Escriba la narrativa de la historia de la marca (2-3 párrafos):
   - Abierto con la lucha del cliente.
   - Presentar la marca como guía.
   - Revelar el plan y la transformación.
3. Escriba la copia de estructura alámbrica del sitio web usando StoryBrand:
   - Encabezado: Promesa de transformación
   - Lo que está en juego: lo que pueden perder
   - Propuesta de Valor: Qué ganan
   - Guía: Por qué deberían confiar en ti
   - Plan: El camino de 3 pasos
   - CTA: Qué hacer a continuación
4. Escribe el discurso del ascensor (60 segundos)

### Fase 3: Aplicaciones de historias
1. Cree una copia story-based para los puntos de contacto clave:
   - Página Acerca de: La marca como guía (no héroe)
   - Email de bienvenida: Empatía + autoridad + primer paso
   - Biografía de redes sociales: breve + CTA
   - Apertura del discurso de venta: Problema del cliente + empatía
2. Escribe la "historia de la fogata": una versión de 2 minutos contada en voz alta.
3. Cree las preguntas frecuentes como resolución de la historia (las preguntas se asignan a los elementos SB7)
4. Desarrollar el marco testimonial (qué preguntas hacer a los clientes para que sus historias sigan el arco SB7)

---

## Formato de salida

```markdown
## Brand Story: {Brand Name}

**Framework:** StoryBrand SB7

---

### BrandScript

#### 1. Character (Hero = Customer)
**Who they are:** {description}
**What they want:** {desire}

#### 2. Problem
**Villain:** {root cause}
**External:** {tangible problem}
**Internal:** {how it feels}
**Philosophical:** {why it's wrong}

#### 3. Guide (Brand)
**Empathy:** {we understand statement}
**Authority:** {proof of expertise}

#### 4. Plan
1. {Step 1}
2. {Step 2}
3. {Step 3}

#### 5. Call to Action
**Direct CTA:** {primary action}
**Transitional CTA:** {softer entry point}

#### 6. Failure (Stakes)
{What happens if they don't act}

#### 7. Success (Transformation)
{What life looks like after}

---

### One-Liner
{Problem + Solution + Result in one sentence}

### Brand Narrative
{2-3 paragraph story}

### Elevator Pitch
{60-second spoken version}

### Website Wireframe Copy
{Header, stakes, value prop, guide, plan, CTA sections}

### Touchpoint Applications
| Touchpoint | Copy Approach | Key SB7 Element |
|-----------|--------------|-----------------|

### Testimonial Framework
{Questions to ask customers for story-aligned testimonials}
```

---

## Condiciones de veto

- NUNCA haga de la marca el héroe: el cliente siempre es el héroe
- NUNCA omita el problema interno: la mayoría de las compras están impulsadas por sentimientos internos, no por problemas externos.
- NUNCA presente un plan con más de 3 pasos: la simplicidad es confianza
- NUNCA escriba una historia de marca sin riesgos (fracaso): sin riesgos, sin urgencia
- NUNCA olvides la CTA de transición: no todos están listos para la pregunta directa.

---

## Criterios de finalización

- [ ] Los 7 elementos SB7 definidos
- [ ] Frase escrita y memorable
- [ ] Narrativa de marca escrita (2-3 párrafos)
- [ ] Lanzamiento de ascensor creado (60 segundos)
- [ ] Se proporciona una copia de estructura alámbrica del sitio web
- [ ] Historia aplicada a puntos de contacto clave
- [ ] Marco testimonial incluido
