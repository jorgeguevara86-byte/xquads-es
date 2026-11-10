---
task: evaluateTechnology()
responsavel: "@cto-architect"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: company
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: current_stack
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: technology_strategy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Pila actual inventariada en todas las capas" 
  - "[ ] Tecnología Radar construido con 4 anillos" 
  - "[ ] Se creó una hoja de ruta tecnológica de 12 meses" 
---

# Tarea: Evaluar tecnología

**ID de tarea:** CLEVEL-004
**Version:** 1.0.0
**Command:** `*evaluate-technology`
**Agente:** Arquitecto CTO (cto-architect)
**Propósito:** Evaluar la estrategia tecnológica, incluida la evaluación de la pila actual, el radar tecnológico, los registros de decisiones arquitectónicas y el análisis de construcción versus compra.

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `company` | Mensaje de usuario | Sí | Nombre de la empresa y descripción del producto |
| `current_stack` | Usuario | Sí | Pila de tecnología e infraestructura actuales |
| `team` | Usuario | Sí | Tamaño, habilidades y estructura del equipo de ingeniería |
| `challenges` | Usuario | No | Desafíos técnicos conocidos o deuda |
| `strategic_pillars` | vision-chief | No | Pilares estratégicos que la tecnología debe apoyar |

## Preconditions

- La tecnología existe o se está planificando
- Existe equipo de ingeniería o liderazgo técnico
- Marcos ejecutivos cargados (`data/executive-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Evaluar la pila actual

1. Inventario del **current panorama tecnológico**:
   - Frontend: lenguajes, frameworks, herramientas de compilación
   - Backend: Idiomas, frameworks, APIs
   - Datos: Bases de datos, cachés, colas de mensajes
   - Infraestructura: Proveedor de nube, CI/CD, monitoreo
   - Terceros: herramientas SaaS, API, integraciones
2. Evalúe cada tecnología en 5 dimensiones:
   - **Fitness:** ¿Resuelve bien el problema?
   - **Escalabilidad:** ¿Puede soportar un crecimiento 10 veces mayor?
   - **Mantenibilidad:** ¿Es fácil de actualizar y depurar?
   - **Disponibilidad de talento:** ¿Podemos contratar para esto?
   - **Salud de la comunidad:** ¿El ecosistema está creciendo o muriendo?
3. Calcular **technical puntuación de deuda** (1-10 por área):
   - Deuda de código: código heredado, duplicación, pruebas faltantes
   - Deuda de arquitectura: problemas con monolitos, acoplamiento, patrones faltantes
   - Deuda de infraestructura: Procesos manuales, falta automatización
   - Deuda de documentación: Documentación faltante o desactualizada
4. Identificar **critical riesgos**: puntos únicos de falla, brechas de seguridad, problemas de cumplimiento
5. Documentar los hallazgos en un informe de evaluación de tecnología.

### Fase 2: Radar Tecnológico

1. Construye un **Radar tecnológico** con 4 anillos:
   - **Adoptar:** Probado, recomendado para un uso amplio
   - **Prueba:** Vale la pena continuar, probado en un contexto limitado
   - **Evaluar:** Vale la pena explorar, comprender el impacto
   - **Espera:** Proceda con precaución, no comience un nuevo trabajo
2. Categorizar las tecnologías en 4 cuadrantes:
   - **Idiomas y marcos**
   - **Herramientas e infraestructura**
   - **Plataformas y servicios**
   - **Técnicas y patrones**
3. Colocar las tecnologías actuales y candidatas en el radar
4. Para cada tecnología en Trial/Assess:
   - Por qué es interesante
   - Que problema resuelve
   - Riesgo de adopción
   - Enfoque de evaluación recomendado
5. Para cada tecnología en espera:
   - Por qué se lleva a cabo
   - Ruta de migración (si se usa activamente)
6. Cadencia de actualización: revisión trimestral

### Fase 3: Registros de Decisión Arquitectónica (ADR)

1. Cree la **plantilla ADR** para la organización:
   - Título: Título breve descriptivo
   - Estado: Propuesto / Aceptado / Obsoleto / Reemplazado
   - Contexto: ¿Cuál es la situación y el problema?
   - Decisión: ¿Cuál es la decisión que se toma?
   - Consecuencias: ¿Cuáles son los resultados positivos y negativos?
   - Alternativas: ¿Qué otras opciones se consideraron?
2. Documentar **existing decisiones implícitas** como ADR:
   - ¿Por qué se eligió el marco actual?
   - ¿Por qué este proveedor de nube?
   - ¿Por qué esta base de datos?
   - ¿Por qué este patrón de arquitectura?
3. Para cada decisión tecnológica pendiente, cree una **Decisión ADR**:
   - Aplicar la **Matriz Construir-Comprar-Socio**:
     - Construcción: diferenciador central, requisitos únicos, capacidad de equipo
     - Compra: Materia prima, well-served por mercado, más rápido time-to-market
     - Socio: Valor estratégico, integración de ecosistemas, riesgo compartido
   - Califique cada opción según: costo, tiempo, riesgo, valor estratégico, carga de mantenimiento
4. Establecer el **proceso de revisión de ADR**: quién lo aprueba y cuándo revisarlo

### Fase 4: Hoja de ruta tecnológica

1. Alinear la hoja de ruta tecnológica con los **strategic pilares**:
   - Para cada pilar estratégico, identificar habilitadores tecnológicos
   - Para cada habilitador de tecnología, defina el cronograma de implementación
2. Defina la recomendación **Construir vs Comprar** para cada componente principal.
3. Crear la hoja de ruta de la tecnología **12 meses**:
   - Cuarto 1: Fundación (deuda crítica de impuestos, establecimiento de patrones)
   - Cuarto 2: Capacidad (construir nuevas capacidades alineadas con la estrategia)
   - Trimestre 3: Escala (prepare para el crecimiento, optimiza el rendimiento)
   - Cuarto 4: Innovación (explorar nuevas tecnologías, prototipo)
4. Definir **engineering asignación de inversiones**:
   - Desarrollo de las características: X%
   - Deuda técnica:
   - Innovation/R&D: Z%
   - Recomendado: 70/20/10 para la etapa de crecimiento
5. Set **technology KPI**:
   - Frecuencia de despliegue
   - Tiempo de ejecución para los cambios
   - Es tiempo de recuperación (MTTR)
   - Tasa de fallas cambiarias
   - La puntuación de satisfacción de desarrolladores

## Formato de salida

```yaml
technology_strategy:
  company: "{name}"
  current_stack:
    frontend: ["{tech1}", "{tech2}"]
    backend: ["{tech1}", "{tech2}"]
    data: ["{tech1}", "{tech2}"]
    infrastructure: ["{tech1}", "{tech2}"]
  tech_debt_score: "{1-10 average}"
  critical_risks: ["{risk1}", "{risk2}"]
  technology_radar:
    adopt: ["{tech1}", "{tech2}"]
    trial: ["{tech1}"]
    assess: ["{tech1}"]
    hold: ["{tech1}"]
  adrs:
    documented: {number}
    pending_decisions: {number}
  investment_allocation:
    features: "{%}"
    tech_debt: "{%}"
    innovation: "{%}"
  roadmap:
    q1: "{temas y prioridades}" 
    q2: "{temas y prioridades}" 
    q3: "{temas y prioridades}" 
    q4: "{temas y prioridades}" 
  deliverables:
    - technology-assessment.md
    - technology-radar.md
    - adr-log/
    - tech-roadmap.md
    - build-buy-analysis.md
```

## Condiciones de veto

1. **Nunca adoptar nueva tecnología sin un ADR** - decisiones indocumentadas persiguen equipos futuros
2. **Nunca ignore la asignación de la deuda técnica** - El desarrollo de características 100% crea una deuda agravante
3. **Nunca elija la tecnología basada en la hipócrita** - la aptitud para el propósito es el único criterio válido
4. **Nunca construir lo que usted puede comprar para las funciones de productos básicos** - tiempo de ingeniería es el recurso más escaso
5. **Nunca saltar la evaluación de disponibilidad de talento** - la mejor tecnología es inútil si no puedes contratarla

## Criterios de finalización

- [ ] La pila actual inventoried en todas las capas
- [ ] Deuda técnica anotada (1-10) por área
- [ ] Riesgos críticos identificados
- [ ] Radar tecnológico construido con 4 anillos y 4 cuadrantes
- [ ] Al menos 3 ADRs documentados (decisiones existentes)
- [ ] Construir vs Comprar análisis para componentes principales
- Hoja de ruta tecnológica de 12 meses alineada con pilares estratégicos
- [ ] Distribución de inversiones de ingeniería definida
- [ ] Conjunto de KPIs Tecnológicos (Métricas de DORA)
- [ ] La salida coincide con el esquema anterior
