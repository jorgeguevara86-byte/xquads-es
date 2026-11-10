---
task: review()
responsavel: "@copy-master-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: specialist_output
    tipo: string
    origem: "Agente Especialista" 
    obrigatorio: true
  - campo: original_request
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: review_report
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Todos los elementos de la lista de verificación evaluados y puntuados" 
  - "[ ] Veredicto emitido (APPROVE/REVISE/REJECT)" 
  - "[ ] Comentarios específicos proporcionados para cualquier falla" 
  - "[ ] Persuasion Psych checkpoint passed" 
---

# Task: Review Copywriting Output

** ID de la lista: * COPY-M-CHIEF-002
**Version:** 2.0.0
**Command:** `*review`
**Orquestador:** Copia Jefe de Jefe (copy-master-chief)
**Purpose:** Revisar la salida especializada contra la lista de verificación de calidad incluyendo estándares de psicología de persuasión, puntuación y aprobación o solicitud de revisión.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| specialist_output | cadena | Agente especialista | Sí | Entregable no vacío |
| original_request | cadena | Mensaje de usuario | Sí | La solicitud original que desencadenó el trabajo |
| specialist_id | cadena | Enrutamiento | Sí | ID del agente que produjo el resultado |

---

## Preconditions

: El especialista completó su tarea y produjo resultados.
: la lista de verificación de calidad de salida está disponible en checklists/output-quality.md

---

## Fases de Ejecución

### Fase 1: Comprender el contexto

1. Vuelva a leer la solicitud del usuario original.
2. Identifique lo que se pidió versus lo que se entregó
3. Anote el especialista que produjo el resultado.
4. Identificar el objetivo de audiencia y conversión de destino
5. Determinar el medio (email, landing page, ad, sales letter, etc.)

### Fase 2: Aplicar la lista de verificación de calidad

1. Load checklists/output-quality.md
2. Evalúe cada elemento con respecto a los resultados del especialista.
3. Marque cada elemento: [x] Pasa, [ ] Falla, [N/A] No aplicable
4. Contar fallos CRÍTICOS y fallos totales
5. Preste especial atención a: fuerza de encabezado, gancho de plomo, ofrecer claridad y poder CTA

## Fase 3: Persuasion Psychology Checkpoint

1. Verificar los principios de Cialdini están presentes y se aplican adecuadamente:
   - Al menos 3 de 7 principios deben estar activos en cualquier medida que sea posible
   - No debe aplicarse ningún principio de manera manipuladora o engañosa
   - Los principios deben ser tejidos naturalmente, no atornillados
2. Verificar que Blair Warren se utilizan palancas:
   - Al menos 2 de 5 palancas deben activarse
   - Los Levers deben coincidir con el estado emocional del público
3. Compruebe la Ecuación de Valor Hormozi (para ofertas solamente):
   - Las 4 dimensiones anotadas
   - Bonos mapeados a dimensiones específicas que mejoran
4. Incorporar cualquier brecha de psicología de persuasión como elementos de la WARN

### Fase 4: Puntuación y decisión

| Puntuación | Veredicto | Acción |
|-------|---------|--------|
TENIENDO TODO CRITICAL, ANTE non-critical fail, control de psicología pasar Silencio APPROVE Silencio Entrega al usuario ←
TENIENDO TODO CRITICAL, 2+ non-critical fail OR psicología brecha ← REVISE Silencio Regresar al especialista con comentarios específicos 
| Cualquier falla CRÍTICA | RECHAZAR | Devolución al especialista, entrega en bloque |

## Fase 5: Salida

Produzca un informe de revisión con veredicto, puntuación y comentarios.

---

## Formato de salida

```markdown
## Review Report

**Specialist:** {name} ({id})
**Verdict:** {APPROVE | REVISE | REJECT}
**Score:** {X}/{total} items passed

### Passed
- {items that passed}

### Issues Found
- [{CRITICAL|WARN}] {description} — {recommendation}

### Persuasion Psychology Checkpoint
- Cialdini principles active: {count}/7 — {list}
- Warren levers active: {count}/5 — {list}
- Hormozi Value Equation: {scored/not-applicable}
- Psychology verdict: {PASS/GAP — description}

### Copy-Specific Notes
- Headline effectiveness: {assessment}
- Emotional resonance: {assessment}
- Conversion likelihood: {assessment}

### Recommendation
{Next step: deliver / revise specific items / redo}
```

---

## Condiciones de veto

- NUNCA apruebe resultados con fallas CRÍTICAS
: NUNCA rechace sin proporcionar comentarios específicos y procesables
: NUNCA modifique los resultados del especialista; solo revise y brinde comentarios
- Nunca apruebe copia que haga reclamaciones no fundamentadas
- Nunca apruebe copia que carece de una clara llamada a la acción

---

## Criterios de finalización

- [ ] Solicitud original re-read y entendida
- [ ] Público objetivo y medio identificado
- [ ] Todos los elementos de la lista de verificación evaluados
- [ ] Persuasion Psych checkpoint completed
- [ ] Puntuación calculada
- [ ] Veredicto emitido (APPROVE/REVISE/REJECT)
: [] Se proporcionan comentarios específicos para cualquier falla
- [ ] Titular, plomo, y CTA evaluado individualmente
