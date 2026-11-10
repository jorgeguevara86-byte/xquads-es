---
task: analyzeCopy()
responsavel: "@copy-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: copy_text
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: copy_type
    tipo: enum
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: copy_analysis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] 8-dimensión marcador completado con notas" 
  - "[ ] #1 fijación de prioridad identificada con sugerencias de reescribir" 
  - "[ ] Recomendaciones de la lista de especialistas" 
---

# Task: Analyze Copy

** ID de la lista: * COPY-006
**Version:** 1.0.0
**Command:** `*analyze-copy`
**Agente:** Jefe de la Copia (copy-chief)
**Purpose:** Analizar la copia existente para identificar las deficiencias, oportunidades perdidas y prioridades de mejora.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| copy_text Silencio Silencio Silencio Silencio Usuario inmediato Silencio Silencio La copia para analizar (pasado o referenciado) Silencio
| copy_type Silencio enum Silencio Usuario prompt Silencio Sí Silencio titular, sales-letter, email, vsl, ad, landing-page, embudo tóxico
TENIDO TERRITORIO TENIDO TENIDO ANTERIOR SI TENIDO Lo que la copia está tratando de lograr TENIDO
| audiencia | cadena | Mensaje de usuario | No | Descripción del público objetivo |
TENCIÓN TERRITORIO TENIDO objeto TENIDO Usuario prompt TEN NO TEN Datos de rendimiento actuales (CTR, tasa de conversión, etc.) TEN
Silencio contexto Silencio cadena Silencio Usuario prompt Silencio No Silencio ¿Dónde y cómo se utiliza la copia Silencio

---

## Preconditions

- Copiar texto completo (la copia parcial produce análisis parcial)
- Tipo de copia identificado para que se apliquen criterios de evaluación correctos

---

## Fases de Ejecución

### Phase 1: First-Pass Read
1. Lea la copia como una perspectiva, notaría dónde se deja caer la atención
2. Identificar la gran promesa (¿hay una?)
3. Identificar el CTA primario (¿está claro?)
4. Nota primera reacción emocional: aburrido, confundido, intrigado, escéptico, convencido
5. Tiempo cuánto tiempo la copia tiene atención antes de que la mente vaga

## Fase 2: Análisis estructural
1. Evaluar el headline/hook:
   - ¿Detiene al lector?
   - ¿Elegi el público adecuado?
   - ¿Promete un beneficio o despierta curiosidad?
2. Evaluar el plomo (primeras palabras 100 a 300):
   - ¿Se gana el siguiente párrafo?
   - ¿El nivel de conciencia está calibrado correctamente?
3. Evaluar el cuerpo:
   - ¿Hay un flujo lógico y emocional claro?
   - ¿Son beneficios concretos o vagos?
   - ¿Está presente la prueba y estratégicamente colocado?
4. Evaluar el cierre:
   - ¿Está clara la oferta?
   - ¿Es específico y factible el CTA?
   - ¿Hay urgencia sin ser falso?
5. Evaluar la "slippery slide" general - ¿puedes dejar de leer en cualquier lugar?

### Fase 3: Alcanzar y Recomendaciones
1. Partida en 8 dimensiones (1-10 cada uno):
   - Power Headline
   - Participación en la iniciativa principal
   - Conexión emocional
   - Prueba y credibilidad
   - Claridad de beneficios
   - Ofrezca fuerza
   - Eficacia del CTA
   - Flujo y legibilidad
2. Calcular la puntuación general (promedio)
3. Identificar la debilidad #1 que produciría la mayor mejora
4. Proporcione 3 reescrituras específicas y factibles para las secciones más débiles
5. Recomendar qué especialista en escuadría de copia podría mejorar cada área débil

---

## Formato de salida

```markdown
## Copy Analysis

**Type:** {copy_type}
**Goal:** {goal}
**Overall Score:** {X}/10
**Verdict:** {Weak / Needs Work / Solid / Strong / Elite}

---

### Scorecard

| Dimension | Score | Notes |
|-----------|-------|-------|
| Headline Power | X/10 | {brief note} |
| Lead Engagement | X/10 | {brief note} |
| Emotional Connection | X/10 | {brief note} |
| Proof and Credibility | X/10 | {brief note} |
| Benefit Clarity | X/10 | {brief note} |
| Offer Strength | X/10 | {brief note} |
| CTA Effectiveness | X/10 | {brief note} |
| Flow and Readability | X/10 | {brief note} |

---

### #1 Priority Fix
{The single change that would have the biggest impact}

### Top 3 Rewrite Suggestions
1. **{Section}:** {Current text} → {Suggested rewrite} — {Why this is better}
2. ...
3. ...

### Specialist Recommendations
| Weak Area | Recommended Agent | Why |
|-----------|-------------------|-----|

### What's Working Well
{Acknowledge strengths — what to preserve}
```

---

## Condiciones de veto

- Nunca analice sin leer la copia completa
- Nunca dar una puntuación sin justificación específica
- Nunca proporcionar sólo crítica - siempre reconocer lo que funciona
- Nunca recomiendo reescrituras que cambien la oferta o promesa de núcleo sin marcarlo
- NUNCA ignorar las métricas de rendimiento si se proporciona - datos anula la opinión

---

## Criterios de finalización

- [ ] Copia completa lee y first-pass impresión documentada
- [ ] Análisis estructural completado (cabeza, plomo, cuerpo, cierre)
- [ ] 8-dimensión marcador completado con notas
- [ ] #1 fijación de prioridad identificada
- [ ] 3 sugerencias específicas de reescritura proporcionadas
- [ ] Recomendaciones de la lista de especialistas
- [ ] Fuerza reconocida
