---
task: critiqueCopy()
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
  - campo: critique_report
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Todos los 8 criterios marcados con justificación" 
  - "[ ] falla fatal identificada con ejemplos de reescribir" 
  - "[ ] Lista de fijación priorizada con la enrutamiento especialista" 
---

# Task: Critique Copy

** ID de la lista:** COPY-011
**Version:** 1.0.0
**Command:** `*critique-copy`
**Agente:** Jefe de la Copia (copy-chief)
**Purpose:** Entregar una crítica de copia estructurada de 8 puntos con evaluación anotada y correcciones priorizadas.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| copy_text Silencio Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio Copia completa para la crítica Silencio
| copy_type Silencio enum Silencio Usuario prompt Silencio Sí Silencio titular, sales-letter, correo electrónico, vsl-script, ad, landing-page, embudo, balas Silencio
| original_brief TENTER SON TENIDO ANTERIOR NO TEN Original breve o gol que la copia fue escrita para TEN
| target_audience Silencio Silencio Silencio Silencio No Silencio audiencia intencionada Silencio
| performance_data TENCIÓN TENIDO ANTERIOR NO TENIDO métricas existentes si la copia es viva TEN

---

## Preconditions

- Texto completo de copia proporcionado (no fragmentos)
- Tipo de copia identificado para los criterios de puntuación correctos

---

## Fases de Ejecución

### Fase 1: Evaluación objetiva
1. Lea la copia una vez sin juicio — note las reacciones intestinales
2. Lea nuevamente con el marco de puntuación de 8 puntos activo
3. Para cada uno de los 8 criterios, asigne una puntuación (1-10):
   - Atención.Headline/Hook¿Detiene a la persona correcta?
   - # Interest (en inglés)Lead/Opening¿Se ganan las siguientes 100 palabras?
   - El deseoBenefits/Proof):** ¿Hace que el lector desee el resultado?
   - **Acción (Acción)CTA/Close¿Conforma la acción inmediata?
   - **Especidad:** ¿Son afirmaciones concretas con números, nombres y detalles?
   - **Proof:** ¿Todas las reclamaciones están respaldadas por pruebas?
   - ¿Hay una personalidad consistente y convincente?
   - **Flow:** ¿Puedes dejar de leer en cualquier lugar, o te hace pasar?
4. Calcular la puntuación compuesta y asignar el veredicto:
   - 80-100: Elite - esmalte menor
   - 60-79: Esfuerzos: se necesitan mejoras específicas
   - 40-59: Trabajo de las necesidades - reescrituras significativas requeridas
   - A continuación 40: Weak - considerar comenzar de nuevo con un nuevo enfoque

### Phase 2: Deep Critique
1. Para cada criterio que se ajuste a continuación 7, proporcione:
   - Lo que específicamente está mal (citar el texto exacto)
   - Por qué importa (lo que cuesta en conversiones o en compromiso)
   - Cómo arreglarlo (sugerencia de reescritura específica)
2. Identificar el "efecto mortal" — el mayor número de casos que matan el rendimiento
3. Evaluar la calibración del nivel de conciencia - ¿La copia se lanza al nivel correcto?
4. Comprobación de "crimenes de copia":
   - Hablando de ti mismo antes de hablar del lector
   - Características sin beneficios
   - Reclamaciones sin pruebas
   - Lenguaje vago donde se pueden utilizar específicos
   - Voz pasiva en el CTA
   - Múltiples ACR compitiendo por atención

### Fase 3: Recomendaciones Accesibles
1. Proporcionar una lista de fijación priorizada (el impacto más alto primero)
2. Para los 3 primeros arreglos, escriba ejemplos reales de reescritura
3. Recomendar qué agente especialista podría manejar mejor cada solución
4. Si los datos de rendimiento proporcionados, correlacione puntuaciones débiles con gotas métricas
5. Proporcionar una sección "ganancias rápidas" — cambios que tardan menos de 5 minutos

---

## Formato de salida

```markdown
## Copy Critique Report

**Copy Type:** {type}
**Composite Score:** {X}/80 ({percentage}%)
**Verdict:** {Elite / Strong / Needs Work / Weak}
**Fatal Flaw:** {one-line description}

---

### 8-Point Scorecard

| # | Criterion | Score | Status |
|---|-----------|-------|--------|
| 1 | Attention | X/10 | {Pass/Fix} |
| 2 | Interest | X/10 | {Pass/Fix} |
| 3 | Desire | X/10 | {Pass/Fix} |
| 4 | Action | X/10 | {Pass/Fix} |
| 5 | Specificity | X/10 | {Pass/Fix} |
| 6 | Proof | X/10 | {Pass/Fix} |
| 7 | Voice | X/10 | {Pass/Fix} |
| 8 | Flow | X/10 | {Pass/Fix} |

---

### Detailed Critique

#### {Criterion Name} — {Score}/10
**Issue:** {what's wrong — cite exact text}
**Impact:** {what it costs}
**Fix:** {specific recommendation}
**Rewrite:** {before → after example}

---

### Copy Crimes Detected
- {crime}: {where it occurs}

### Prioritized Fix List
| Priority | Fix | Impact | Effort | Agent |
|----------|-----|--------|--------|-------|
| 1 | {fix} | High | {Low/Med/High} | {agent} |

### Quick Wins (Under 5 Minutes)
1. {quick fix}
2. {quick fix}
3. {quick fix}

### What to Keep
{Acknowledge what the copy does well}
```

---

## Condiciones de veto

- NUNCA Crítica sin marcar los 8 criterios
- Nunca proporcionar puntajes sin justificación y referencias específicas de texto
- Nunca entregar sólo la crítica - siempre reconocer fortalezas
- Nunca sugiera reescrituras que cambien la oferta o promesa fundamental
- Nunca ignore los datos de rendimiento si se proporciona - métricas de las opiniones de Trump

---

## Criterios de finalización

- [ ] Todos los 8 criterios marcados con justificación
- [ ] Marcaje compuesto calculado y veredicto asignado
- [ ] Falda fatal identificada
- [ ] Crítica detallada para todos los criterios que marcan abajo 7
- [ ] Los 3 ejemplos de reescritura proporcionados
Lista de fijación priorizada con enrutamiento especializado
- [ ] sección de triunfos rápidos incluido
- [ ] Fuerza reconocida
