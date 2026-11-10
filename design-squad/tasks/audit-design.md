---
task: auditDesign()
responsavel: "@dave-malouf"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: organization_context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: current_design_practice
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: designAudit
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Los tres lentes evaluados con puntajes y resultados específicos" 
  - "[Top 3-5] highest-leverage mejoras identificadas" 
  - "[ ] Hoja de ruta gradual creada con hitos" 
---

# Task: Auditoría de diseño &quot; Evaluación de la madurez

** ID de usuario: ** DESIGN-002
**Version:** 1.0.0
**Command:** `*audit-design`
Dave Malouf (en inglés)dave-malouf) + Jefe de diseño (design-chief)
**Purpose:** Evaluar la madurez del diseño en tres lentes e identificar las lagunas con una hoja de ruta de mejora.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `organization_context` tención Tamaño de la empresa, etapa, industria TENIDO YES TENIDO
| `current_design_practice` ← Equipo, herramientas, procesos TENIDO YES ANTERIOR
| `design_artifacts` TENIDO Diseños, sistemas, docs TENIDO TENIDO TENIDO
| `stakeholder_concerns` Silencio Dolor puntos de liderazgo Silencio NO TENIDO
| `product_portfolio` | Products/services el uso de la palabra Silencio Silencio

## Preconditions

1. Acceso a la información actual sobre la práctica del diseño
2. Comprensión de la estructura orgánica y la colocación de los equipos de diseño
3. Voluntad para evaluar honestamente (no sólo validar el enfoque actual)

## Fases de Ejecución

### Fase 1: Evaluar la madurez (3 sentidos)

**Cierto 1: Cómo trabajamos juntos (Gente &amp; Cultura)**
1. Estructura del equipo: centralizada, incrustada, híbrida?
2. La claridad del papel - son funciones de diseño well-defined?
3. Las trayectorias de carrera - ¿los diseñadores tienen trayectorias de crecimiento?
4. Contratar prácticas - ¿Cómo se evalúa el talento del diseño?
5. Colaboración multifuncional: ¿cómo interactúan el diseño, la ingeniería y el producto?
6. La cultura del diseño, ¿se valora el diseño a nivel de liderazgo?
7. Nota: Ad Hoc (1) → Emergentes (2) → Definido (3) → Managed (4) → Optimizado (5)

**Lens 2: Cómo trabajamos (Proceso &quot; flujo de trabajo)**
1. Proceso de diseño - ¿Hay una metodología consistente?
2. Práctica de investigación - ¿Cómo se recopilan y utilizan las ideas de los usuarios?
3. Proceso de despachado - ¿Cómo consiguen los diseños a los ingenieros?
4. Garantía de calidad - ¿Cómo se verifica la calidad del diseño?
5. Los bucles de retroalimentación - ¿Cómo aprenden los equipos de los productos enviados?
6. Herramienta - ¿La pila de herramientas es consistente y eficiente?
7. Nota: Ad Hoc (1) → Emergentes (2) → Definido (3) → Managed (4) → Optimizado (5)

**Cierra 3: En lo que trabajamos (Proyecto de salida)**
1. El sistema de diseño - ¿existe uno? ¿Se utiliza consistentemente?
2. Accesibilidad - ¿Es práctica estándar de cumplimiento de la CMG?
3. La consistencia visual - ¿son los productos visualmente coherentes?
4. Calidad UX - ¿Son productos utilizables e intuitivos?
5. La innovación - ¿está el equipo empujando los límites del diseño?
6. Documentación - ¿se registran y comparten decisiones de diseño?
7. Nota: Ad Hoc (1) → Emergentes (2) → Definido (3) → Managed (4) → Optimizado (5)

### Fase 2: Identifique Gaps

1. Map current age scores across the three lenses
2. Identificar el lowest-scoring lente — este es el cuello de botella primario
3. Dentro de cada lente, identifique las lagunas específicas:
   - ¿Qué existe pero está rota o inconsistente?
   - ¿Qué falta?
   - ¿Qué está funcionando bien y debe ser preservado?
4. Las lagunas de referencia cruzadas - ¿las lagunas provocan deficiencias en el proceso?
5. Benchmark contra estándares de la industria para el escenario y tamaño de la empresa
6. Identificar el 3-5 highest-leverage mejoras

### Fase 3: Recomendar mejoras

1. Para cada brecha identificada, recomiende una intervención específica:
   - ** Gana rápido** (1-2 semanas) - Bajo esfuerzo, impacto inmediato
   **A corto plazo** (1-3 meses) — Un esfuerzo moderado, una mejora significativa
   **A largo plazo** (3 a 12 meses) - Inversión estratégica para un cambio duradero
2. Prioridad por los efectos y la viabilidad
3. Identificar dependencias - ¿qué debe ocurrir primero?
4. Necesidades de recursos estimadas: personas, instrumentos, presupuesto
5. Definir las métricas de éxito para cada mejora

### Phase 4: Build Roadmap

1. Crear una hoja de ruta de mejora gradual:
   - **Páse 1 (Mes 1-2):** Fundación — Ganancias rápidas + correcciones críticas
   **Phase 2 (Mes 3-6):** Building — Process standardization + tooling
   - **Página 3 (Mes 6-12):** Escalada: Cambio de cultura + prácticas avanzadas
2. Definir los hitos y los puestos de control
3. Asignación de la propiedad de cada iniciativa
4. Crear un plan de medición - ¿cómo se rastreará el progreso?
5. Plan de comunicación: ¿cómo se informará y se comprometerá a la organización?
6. Definir el modelo de gobernanza para la mejora de la madurez del diseño en curso

## Formato de salida

```yaml
design_audit:
  auditors: [dave-malouf, design-chief]
  organization: "{company}"
  maturity_scores:
    people_culture:
      score: 0
      level: "Ad Hoc ← Emergentes Silencio Definido Silencio Managed ← Optimizado" 
      strengths: ["¿Qué funciona?" ]
      gaps: ["¿Qué es lo que falta?" ]
    process_workflow:
      score: 0
      level: "Ad Hoc ← Emergentes Silencio Definido Silencio Managed ← Optimizado" 
      strengths: ["¿Qué funciona?" ]
      gaps: ["¿Qué es lo que falta?" ]
    craft_output:
      score: 0
      level: "Ad Hoc ← Emergentes Silencio Definido Silencio Managed ← Optimizado" 
      strengths: ["¿Qué funciona?" ]
      gaps: ["¿Qué es lo que falta?" ]
  overall_maturity: 0
  primary_bottleneck: "{objetivo de puntuación más bajo}" 
  top_improvements:
    - improvement: "{description}"
      impact: "ALTO | MEDIANO | BAJO" 
      effort: "ALTO | MEDIANO | BAJO" 
      timeline: "quick_win | short_term | long_term"
  roadmap:
    phase_1: ["{} [artículos de la fundación]" ]
    phase_2: ["{}}} {}}}" ]
    phase_3: ["{Scaling items}" ]
  measurement_plan: ["{metrics to track}" ]
```

## Condiciones de veto

* * NUNCA* evalúa la madurez sin considerar los tres objetivos – están interconectados
** NUNCA** recomendar prácticas avanzadas para una organización en madurez ad hoc - conocerlas donde están
* NUNCA* ignorar a las personas y la cultura — el proceso y las herramientas fracasan sin la cultura correcta
- ** NUNCA** crear una hoja de ruta sin una clara propiedad y hitos
- ** NUNCA** saltar la evaluación de las fortalezas - a partir de lo que funciona, no sólo se centran en las lagunas

## Criterios de finalización

- [ ] Los tres lentes evaluados con puntajes y resultados específicos
- [ ] Gaps identificados y cross-referenced a través de lentes
- [Top 3-5] highest-leverage mejoras identificadas
- [ ] Mejoras priorizadas por impacto y viabilidad
- [ ] Hoja de ruta gradual creada con hitos
- Plan de medición definido para el seguimiento de los progresos
- [ ] Propiedad asignada para cada iniciativa
