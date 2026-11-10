---
task: critiqueCopy()
responsavel: "@copy-master-chief"
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
  - "[ ] Auditoría de psicología de persuasión completada" 
---

# Task: Critique Copy

** ID de la lista:** COPY-M-011
**Version:** 2.0.0
**Command:** `*critique-copy`
**Agente:** Copia Jefe de Jefe (copy-master-chief)
**Purpose:** Entregar una crítica de copia estructurada de 8 puntos con evaluación anotada, correcciones priorizadas y auditoría de psicología de persuasión.

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

# Champion Reference

Use estos marcos críticos como normas de referencia:

1. **El Test de Gary Halbert "Leerlo en voz alta"** - Si no suena como una persona hablando con otra, reescribirlo
2. ** Auditoría del nivel de conciencia de Eugene Schwartz** — ¿Está la copia en la etapa correcta de sensibilización?
3. **David Ogilvy "¿Podría hacerme comprar?"** — La prueba definitiva honesta de la eficacia de la copia
4. ** Auditoría de Razón de Hopkins*: ¿Tienen todas las afirmaciones una razón para creer?
5. ** El listado de "Crímenes de Copia" de Joanna Wiebe** — Detección sistemática de los crímenes conversion-killing errores

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

## Fase 2: Auditoría de Psicología de Persuasión
1. Auditoría Cialdini's 7 principios:
   - ¿Por cada principio: Presente? ¿Dónde? ¿Qué tan fuerte (1-5)?
   - Identificar qué principios faltan por completo
   - Principios de bandera que están presentes pero mal ejecutados
2. Auditoría de Blair Warren 5 palancas:
   - ¿La copia anima sueños, justifica fracasos, temores allay, confirma sospechas, lanza rocas?
   - ¿Qué palancas están activadas?
3. Densidad de persuasión de puntaje: Total de principios activos / Total posible (12)
4. Identificar la brecha de persuasión #1 con mayor impacto potencial

### Phase 3: Deep Critique
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

### Fase 4: Recomendaciones Accesibles
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

### Persuasion Psychology Audit

| Cialdini Principle | Present? | Strength (1-5) | Location | Fix Needed? |
|-------------------|----------|----------------|----------|-------------|
| Reciprocity | Y/N | X | {where} | {Y/N} |
| Commitment | Y/N | X | {where} | {Y/N} |
| Social Proof | Y/N | X | {where} | {Y/N} |
| Authority | Y/N | X | {where} | {Y/N} |
| Liking | Y/N | X | {where} | {Y/N} |
| Scarcity | Y/N | X | {where} | {Y/N} |
| Unity | Y/N | X | {where} | {Y/N} |

| Warren Lever | Present? | Location |
|-------------|----------|----------|
| Encourage dreams | Y/N | {where} |
| Justify failures | Y/N | {where} |
| Allay fears | Y/N | {where} |
| Confirm suspicions | Y/N | {where} |
| Throw rocks | Y/N | {where} |

**Persuasion Density:** {X}/12 principles active ({percentage}%)
**#1 Persuasion Gap:** {missing principle + where to add it}

---

### Detailed Critique

#### {Criterion Name} — {Score}/10
**Issue:** {what's wrong — cite exact text}
**Impact:** {what it costs}
**Fix:** {specific recommendation}
**Rewrite:** {before -> after example}

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
- [ ] Auditoría de Psicología de Persuasión completada (7 Cialdini + 5 Warren)
- [ ] Densidad de persuasión anotada
- [ ] #1 brecha de persuasión identificada con la recomendación de corrección
- [ ] Crítica detallada para todos los criterios que marcan abajo 7
- [ ] Los 3 ejemplos de reescritura proporcionados
Lista de fijación priorizada con enrutamiento especializado
- [ ] sección de triunfos rápidos incluido
- [ ] Fuerza reconocida
