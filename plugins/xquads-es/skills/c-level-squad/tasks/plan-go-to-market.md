---
task: planGoToMarket()
responsavel: "@cmo-architect"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: target_market
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: gtm_strategy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] TAM/SAM/SOM definido con sincronización de mercado" 
  - "[ ] Declaración de posicionamiento elaborada con jerarquía de mensajería" 
  - "[ ] Top 3 canales seleccionados con estrategia y presupuesto" 
---

# Tarea: Planificar la comercialización

**ID de tarea:** CLEVEL-003
**Version:** 1.0.0
**Command:** `*plan-gtm`
**Agente:** Arquitecto CMO (cmo-architect)
**Propósito:** Diseñar una estrategia go-to-market integral que cubra análisis de mercado, posicionamiento, estrategia de canal, plan de lanzamiento y métricas de éxito.

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `product` | Mensaje de usuario | Sí | Producto o servicio a llevar al mercado |
| `target_market` | Mensaje de usuario | Sí | Mercado objetivo y perfil de cliente ideal |
| `competitive_landscape` | Usuario | No | Competidores conocidos y su posicionamiento |
| `budget` | Usuario | No | Presupuesto de marketing disponible |
| `timeline` | Usuario | No | Fecha de lanzamiento o limitación de tiempo |

## Preconditions

- Producto o servicio definido (al menos alcance MVP)
- Existe la hipótesis del mercado objetivo
- Marcos ejecutivos cargados (`data/executive-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Análisis de Mercado

1. Defina el **Mercado Total Direccionable (TAM)**:
   - TAM: demanda total del mercado
   - SAM: Mercado accesible
   - SOM: Mercados de servicios de obtención (realísticos) first-year Objetivo)
2. Conducta **competitive análisis**:
   - Competencias directas (same solución, misma audiencia)
   - Competencias indirectas (solución diferente, mismo problema)
   - Soluciones alternativas (lo que hacen los clientes hoy sin su producto)
3. Aplicar **Estrategia del Océano Azul**: evaluación:
   - ¿Qué factores podemos eliminar (la industria se da por sentado)?
   - ¿Qué factores podemos reducir (over-served por industria)?
   - ¿Qué factores podemos plantear?under-served por industria)?
   - ¿Qué factores podemos crear (la industria nunca ha ofrecido)?
4. Identificar el **market brecha** - necesidades no satisfechas o segmentos insuficientemente conservados
5. Evaluación **market tiempo** - ¿Por qué ahora?

### Fase 2: Posicionamiento

1. Crear la Declaración de Posiciones**:
   - Para [cliente de meta] quién [need/problem], [producto] es una [categoría] que [beneficio clave]. A diferencia [alternativo], nosotros [diferencista].
2. Defina el lienzo de Proposición ** Valor**:
   - Trabajos de clientes (lo que están tratando de hacer)
   - Dolores de los clientes (frustraciones y riesgos)
   - Ganancias de clientes (desdesechos deseados)
   - Aliviadores de dolor (cómo nos enfrentamos a dolores)
   - Ganar creadores (cómo creamos ganancias)
3. Desarrollar **messaging jerarquía**
   - Nivel 1: Un lanzamiento de línea (10 segundos)
   - Nivel 2: Parcela elevadora (30 segundos)
   - Nivel 3: Relación de valor (2 minutos)
   - Nivel 4: Completa narrativa (5 minutos, presentación)
4. Definir **proof puntos** - pruebas que apoyen cada reclamación
5. Crear el **competitive mapa de posición** (2x2 matriz con ejes elegidos)

## Fase 3: Estrategia del Canal

1. Mapear el Viaje de Adquisición de clientes**:
   - Conciencia: ¿Cómo se enteran por primera vez de nosotros?
   - Consideración: cómo nos evalúan
   - Decisión: Cómo eligen comprar
   - A bordo: Cómo empiezan a usar
   - Expansión: Cómo compran más
2. Evaluar los canales utilizando el **Marco de Bolsillo**:
   - Anillo exterior: todos los canales posibles (canales de labrainstorm 19+)
   - Anillo medio: Canales prometedores (6-8 basados en el público adecuado)
   - Anillo interior: Canales básicos (top 3 para probar primero)
3. Para cada canal central, definir:
   - ¿Cómo usaremos este canal?
   - **Tactics:** Campañas específicas y contenidos
   **Presupuesto:** Asignación y CAC esperado
   - **Tiempo: ** Cuando se lanza y se lanza
   - **Métricas de éxito:**
4. Diseño de la **content Motor de marketing**:
   - pilares de contenido (3-5 temas)
   - Tipos de contenido por estadio de embudo
   - Plan de distribución
5. Definir el **marketing-sales handoff** (MQL a los criterios SQL)

### Fase 4: Plan de lanzamiento y medición del éxito

1. Crear el **Launch Sequence** (T-minus timeline):
   - T-60 días: Construyendo audiencias pre-lanzamiento, camarero, beta
   - T-30 días: visor de contenidos, divulgación de PR, alineación de parejas
   - T-14 días: campaña de teaser, acceso temprano
   - T-7 días: Prepa final, alineación de equipo, control de sistemas
   - Día de lanzamiento: Empuje coordinado a través de todos los canales
   - T+7 días: Mantenimiento de momento, comentarios de los usuarios
   - T+30 días: revisión y optimización post-lanzamiento
2. Definir **launch métricas** (primer 30 días):
   - Conciencia: Alcance, impresiones, PR menciones
   - Adquisición: Inscripciones, juicios, demos
   - Activación: Primer valor entregado
   - Ingresos: Primero paga clientes
3. Definir **steady-state métricas** (en curso):
   - CAC ( Costo de adquisición de clientes)
   - LTV/CAC ratio (target √≥ 3:1)
   - Período de reembolso
   - Gasoducto con fuente de comercialización %
   - ROAS específicas para el canal
4. Crear el **90-día post-launch plan de optimización**
5. Definer **pivot dispara** - señales que requieren cambios de estrategia

## Formato de salida

```yaml
gtm_strategy:
  product: "{name}"
  market:
    tam: "{size}"
    sam: "{size}"
    som: "{size}"
    timing: "¿Por qué ahora?" 
  positioning:
    statement: "{declaración de la propuesta}" 
    one_line_pitch: "{presentación de 10 segundos}" 
    differentiator: "{key differentiator}" 
  channels:
    core: ["{channel1}", "{channel2}", "{channel3}"]
    total_budget: "{amount}"
    target_cac: "{amount}"
  launch:
    date: "{date or TBD}" 
    sequence_duration: "90 días (60 pre + 30 post)" 
    key_milestones: ["{milestone1}", "{milestone2}"]
  success_metrics:
    30_day: {signups: "", revenue: "", activation: ""}
    ltv_cac_target: "> 3:1"
  deliverables:
    - market-analysis.md
    - positioning-document.md
    - channel-strategy.md
    - launch-plan.md
    - metrics-dashboard.md
```

## Condiciones de veto

1. **NUNCA lanzamiento sin una declaración de posición** - productos no diferenciados mueren en el mercado
2. **Nunca difundió el presupuesto en más de 3 canales básicos inicialmente** - el foco supera la amplitud en el lanzamiento
3. **Nunca saltar la evaluación del Océano Azul** - compitiendo head-on con los titulares en sus términos es suicidio
4. **Nunca defina las métricas de éxito después del lanzamiento** - si no sabes cómo es el éxito, no puedes medirlo
5. **Nunca ignores el marketing-sales handoff** -- MQL a SQL desperdicia el tiempo de ambos equipos

## Criterios de finalización

- [ ] TAM/SAM/SOM definida con el tiempo de mercado racional
- [ ] Análisis competitivo completado (directo, indirecto, alternativas)
- [ ] Declaración de posicionamiento elaborado con jerarquía de mensajería
- [ ] Top 3 canales seleccionados con estrategia y presupuesto
Secuencia de lanzamiento prevista (T-60 a T+30)
- [ ] métricas de éxito definidas para 30 días y steady-state
- [ ] LTV/CAC período de destino y reembolso previsto
- [ ] La salida coincide con el esquema anterior
