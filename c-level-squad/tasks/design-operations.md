---
task: designOperations()
responsavel: "@coo-orchestrator"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: company
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: team_structure
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: operational_design
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Procesos centrales identificados y mapeados" 
  - "[ ] Los 3 principales cuellos de botella identificados con impacto cuantificado" 
  - "[ ] Marco OKR redactado para el trimestre actual" 
---

# Tarea: Operaciones de diseño

**ID de tarea:** CLEVEL-002
**Version:** 1.0.0
**Command:** `*design-operations`
**Agente:** Director de operaciones orquestador (coo-orchestrator)
**Propósito:** Diseñar la excelencia operativa a través del mapeo de procesos, eliminación de cuellos de botella, marcos OKR y cadencia de ejecución.

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `company` | Mensaje de usuario | Sí | Nombre de la empresa y contexto operativo actual |
| `strategic_pillars` | vision-chief | No | Pilares estratégicos de la tarea set-vision |
| `team_structure` | Usuario | Sí | Tamaño actual del equipo, funciones y departamentos |
| `pain_points` | Usuario | No | Desafíos operativos y cuellos de botella conocidos |
| `tools` | Usuario | No | Herramientas operativas actuales (PM, CRM, comunicaciones, etc.) |

## Preconditions

- La empresa tiene al menos una estructura de equipo básica.
- Existe dirección estratégica (aunque sea informal)
- Marcos ejecutivos cargados (`data/executive-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Mapa de Procesos

1. Identifique los **5-7 procesos de negocio principales** (value-creating actividades):
   - Sales/revenue generation
   - Product/service delivery
   - Customer support/success
   - Contratación e incorporación
   - Operaciones financieras
   - Marketing y crecimiento
2. Para cada proceso, asigne:
   - **Pasos:** Actividades secuenciales desde el desencadenante hasta el resultado
   - **Propietarios:** Quién es responsable de cada paso
   - **Transferencias:** Donde el trabajo se transfiere entre people/teams
   - **Herramientas:** Sistemas utilizados en cada paso
   - **SLA:** Tiempo esperado para cada paso
3. Identifique **process vencimiento** para cada:
   - Ad-hoc (sin proceso definido)
   - Definido (documentado pero inconsistente)
   - Gestionado (medido y monitoreado)
   - Optimizado (mejorado continuamente)
4. Documentar el mapa del proceso del estado actual

### Fase 2: Identificar cuellos de botella

1. Para cada proceso central, identifique:
   - **Cuellos de botella:** Donde el trabajo se acumula o se ralentiza
   - **Puntos únicos de falla:** Pasos que dependen de una sola persona
   - **Residuos:** Pasos que añaden tiempo pero no valor (pensamiento Lean)
   - **Bucles de reelaboración:** donde los errores provocan esfuerzos repetidos
2. Cuantificar el impacto de cada cuello de botella:
   - Costo de tiempo (hours/week perdido)
   - Impacto en los ingresos (ofertas retrasadas, clientes esperando)
   - Impacto en la moral del equipo (frustración, riesgo de agotamiento)
3. Priorice los cuellos de botella utilizando la matriz **Impacto vs Esfuerzo**:
   - Ganancias rápidas (alto impacto, poco esfuerzo): hazlo primero
   - Proyectos estratégicos (alto impacto, alto esfuerzo): Planificar cuidadosamente
   - Suplentes (bajo impacto, bajo esfuerzo): Delegar
   - Pérdidas de tiempo (bajo impacto, alto esfuerzo): Eliminar
4. Seleccione **top 3 cuellos de botella** para tomar medidas inmediatas
5. Diseñar soluciones para cada uno (automatización, contratación, rediseño de procesos, cambio de herramientas)

### Fase 3: Diseño de OKR

1. Crear la **Arquitectura OKR** alineada con los pilares estratégicos:
   - **OKR de la empresa:** 3-5 objetivos para el trimestre
   - **OKR del equipo:** 2-3 objetivos por equipo, alineados hacia arriba
   - **OKR individuales:** 2-3 por persona (opcional en la etapa inicial)
2. Para cada objetivo:
   - Escribir como **aspirational resultado** (no es una tarea)
   - Defina **2-3 resultados clave** que sean mensurables y time-bound
   - Establece **confidence nivel** al inicio (normalmente 50 % para objetivos ambiciosos)
   - Asignar **owner** (una persona, incluso para OKR del equipo)
3. Aplique las mejores prácticas de OKR:
   - 60% top-down, 40% bottom-up
   - Puntuación 0,0-1,0 (0,7 es éxito para objetivos ambiciosos)
   - Separe los OKR comprometidos (deben alcanzarse) de los aspiracionales (extenderse)
   - Los OKR NO están vinculados a la compensación
4. Cree la **plantilla de seguimiento de OKR**

### Fase 4: Implementar cadencia

1. Diseñar la **Cadencia Operativa** (ritmo de reunión):
   - **Diario:** Standup de 15 minutos (lo que hice, lo que haré, bloqueadores)
   - **Semanal:** Sincronización del equipo de 60 minutos (revisión de métricas, prioridades, decisiones)
   - **Mensual:** Revisión comercial de 90 minutos (progreso de OKR, salud financiera)
   - **Trimestral:** Sesión de estrategia de medio día (puntuación de OKR, planificación del próximo trimestre)
   - **Anual:** Día completo fuera del sitio (revisión de la visión, planificación anual)
2. Para cada reunión de cadencia, defina:
   - **Plantilla de agenda** (formato estándar)
   - **Asistentes** (quienes deben estar allí)
   - **Decisiones esperadas** (lo que se resuelve)
   - **Artefactos** (lo que obtiene produced/updated)
3. Diseñe el **Protocolo de escalamiento**:
   - Nivel 1: el líder del equipo se resuelve en 24 horas
   - Nivel 2: Jefe de departamento resuelve en 48h
   - Nivel 3: el nivel C se resuelve en 72 h
   - Nivel 4: CEO inmediato (customer-facing crisis, legal, seguridad)
4. Cree el **Panel Operativo** con:
   - Progreso de OKR (red/yellow/green)
   - Métricas de salud del proceso
   - Capacidad y utilización del equipo
   - Indicadores financieros clave
5. Definir el **continuous ciclo de mejora**: cómo evolucionan las operaciones trimestralmente

## Formato de salida

```yaml
operational_design:
  company: "{name}"
  core_processes: {count: 0, mapped: 0, maturity_avg: ""}
  bottlenecks:
    identified: {number}
    top_3: ["{bottleneck1}", "{bottleneck2}", "{bottleneck3}"]
    estimated_time_saved: "{hours/week}"
  okr_framework:
    company_objectives: {number}
    team_objectives: {number}
    quarter: "{Q1/Q2/Q3/Q4 YYYY}"
  cadence:
    daily: "15 minutos de pie" 
    weekly: "Sincronización en equipo de 60 minutos" 
    monthly: "Revisión comercial de 90 minutos" 
    quarterly: "Estrategia de medio día" 
  deliverables:
    - process-map.md
    - bottleneck-analysis.md
    - okr-framework.md
    - operating-cadence.md
    - operational-dashboard.md
```

## Condiciones de veto

1. **NUNCA diseñe OKR sin comprender los procesos actuales** -- Los OKR miden resultados, no reparan procesos rotos
2. **NUNCA implemente todas las reuniones de cadencia a la vez en un equipo pequeño**: comience con las semanales y mensuales, agregue según sea necesario
3. **NUNCA vincules los OKR con la compensación**: esto destruye la cultura de los objetivos ambiciosos.
4. **NUNCA ignores la capacidad del equipo al establecer los OKR**: los objetivos ambiciosos no deberían significar agotamiento
5. **NUNCA mapee procesos sin hablar con las personas que realizan el trabajo** -- el diseño de procesos de la torre de marfil falla

## Criterios de finalización

- [ ] 5-7 procesos centrales identificados y mapeados
- [ ] Madurez del proceso evaluada para cada
- [ ] Los 3 principales cuellos de botella identificados con impacto cuantificado
- [ ] Soluciones diseñadas para cuellos de botella prioritarios
- [ ] OKR de empresa y equipo redactados para el trimestre actual
- [ ] Cadencia operativa diseñada con plantillas de agenda
- [ ] Protocolo de escalamiento definido (4 niveles)
- [ ] Panel operativo diseñado
- [ ] La salida coincide con el esquema anterior
