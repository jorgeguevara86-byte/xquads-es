---
task: reviewBusinessScalingOutput()
responsavel: "@hormozi-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: specialist_output
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: original_request
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: reviewReport
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Todos los elementos de lista de verificación evaluados" 
  - "[ ] Veredicto emitido (APPROVE/REVISE/REJECT)" 
  - "[ ] Valor ecuación y cálculos de ingresos individualmente evaluados" 
---

# Task: Review Business Scaling Output

** ID de usuario:** HORMOZI-CHIEF-002
**Version:** 1.0.0
**Command:** `*review`
**Orquesta:* Jefe Hormozi (Hormozi)hormozi-chief)
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
4. Identificar el modelo de negocio, la etapa de ingresos y la restricción de escalado
5. Determinar el marco Hormozi que se aplica (ecuación de valor, creación de oferta, gen de plomo, etc.)

### Fase 2: Aplicar la lista de verificación de calidad

1. Load checklists/output-quality.md
2. Evalúe cada elemento con respecto a los resultados del especialista.
3. Marque cada elemento: [x] Pasa, [ ] Falla, [N/A] No aplicable
4. Contar fallos CRÍTICOS y fallos totales
5. Preste especial atención a: claridad de la ecuación de valor, ofrecer irresistibilidad y matemáticas de ingresos

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

### Scaling-Specific Notes
- Value equation strength: {assessment}
- Revenue impact estimate: {assessment}
- Implementation feasibility: {assessment}

### Recommendation
{Next step: deliver / revise specific items / redo}
```

---

## Condiciones de veto

- NUNCA apruebe resultados con fallas CRÍTICAS
: NUNCA rechace sin proporcionar comentarios específicos y procesables
: NUNCA modifique los resultados del especialista; solo revise y brinde comentarios
- Nunca apruebe estrategias sin una economía de ingresos claros matemática o unidad
- Nunca apruebe vago consejo de "hacer crecer su negocio" sin palancas concretas

---

## Criterios de finalización

- [ ] Solicitud original re-read y entendida
- [ ] Modelo de negocio y etapa de ingresos identificados
- [ ] Todos los elementos de la lista de verificación evaluados
- [ ] Puntuación calculada
- [ ] Veredicto emitido (APPROVE/REVISE/REJECT)
: [] Se proporcionan comentarios específicos para cualquier falla
- [ ] Valor ecuación y cálculos de ingresos individualmente evaluados
