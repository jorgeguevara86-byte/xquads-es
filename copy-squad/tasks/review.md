---
task: review()
responsavel: "@copy-chief"
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
---

# Task: Review Copywriting Output

** ID de la lista: * COPY-CHIEF-002
**Version:** 1.0.0
**Command:** `*review`
**Orquestador:** Jefe de la Copia (copy-chief)
**Propósito:** Revisar la producción del especialista comparándola con la lista de verificación de calidad, calificar y aprobar o solicitar revisión.

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

### Fase 3: Anota y decide

| Puntuación | Veredicto | Acción |
|-------|---------|--------|
| Todo CRÍTICO pasa, < 2 non-critical falla | APROBAR | Entregar al usuario |
| Todos los CRÍTICOS pasan, 2+ non-critical fallan | REVISAR | Volver al especialista con comentarios específicos |
| Cualquier falla CRÍTICA | RECHAZAR | Devolución al especialista, entrega en bloque |

### Fase 4: Salida

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
- [ ] Puntuación calculada
- [ ] Veredicto emitido (APPROVE/REVISE/REJECT)
: [] Se proporcionan comentarios específicos para cualquier falla
- [ ] Titular, plomo, y CTA evaluado individualmente
