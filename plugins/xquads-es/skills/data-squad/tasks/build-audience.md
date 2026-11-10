---
task: buildAudience()
responsavel: "@wes-kao"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: expertise
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: target_audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: audience_strategy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] POV picante identificado y validado" 
  - "[ ] Plataforma seleccionada con análisis de formato ajustado" 
  - "[ ] 30 días de inicio de contenido paquete descrito" 
---

# Task: Build Audience

** ID de usuario:** DATOS-005
**Version:** 1.0.0
**Command:** `*build-audience`
* Agente* Wes Kao (*wes-kao)
**Purpose:** Construir un público comprometido a través de un punto de vista espeluznante, selección de plataformas estratégicas, cadencia de contenido y diseño cohorte

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `expertise` Silencio invocar usuario Silencio Sí Silencio Domain expertise or knowledge area Silencio
| `target_audience` Silencio Silencio Silencio Silencio Silencio Quién debe ser el público
| `current_presence` ← Usuario Silencio No TENIDO El tamaño de la audiencia, plataformas, contenido TENIDO
| `goal` TENIDO Usuario TENIDO No TENIDO Audience goal: authority, leads, community, course launch TEN
| `time_commitment` Silencio Usuario Silencio No Silencio Horarios por semana disponibles para la creación de contenidos Silencio

## Preconditions

- La experiencia de dominio existe y es demostrable
- El público objetivo es identificable
- Marcos de medición cargados (`data/metrics-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Encontrar punto de vista brillante

1. Identificar su **unique intersección** - la combinación de experiencia que sólo tiene
2. Aplicar el marco de POV **Spiky**:
   - **Específico:** No "el marketing es importante" pero "B2B SaaS empresas desperdician el 60% de su presupuesto de marketing en la conciencia de la marca antes de alcanzar la PMF"
   - **Proporción:** Puede ser respaldado por datos, experiencia o resultados
   - **Interesante: * Hace que la gente deje de desplazarse
   - **Contrarian:** Desafíos de la sabiduría convencional
   - **Tu terreno: * Tienes más credibilidad en esto que la mayoría
3. Generar **5-10 candidatos arañazos POV**
4. Probad cada uno contra el ** "¿Alguien podría discutir con esto?"** filtro:
   - Si nadie discuta, no es lo suficientemente arpía
   - Si todo el mundo discuta, no es lo suficientemente creíble.
5. Seleccione el **1 primario despilfarro POV** y **2-3 de apoyo POV**
6. Validar: ¿puede crear 50+ piezas de contenido de este POV?

### Fase 2: Elija Plataforma

1. Evaluar plataformas contra su público y estilo de contenido:
   - **Enlazado en:** B2B, profesional, long-form texto, career-oriented
   - **Twitter/X:** Tech, medios, tomas rápidas, cultura de hilo
   - **Newsletter:** Público propio, buceos profundos, alta confianza
   - * Evergreen, search-driven, estudiantes visuales
   *Podcast:** Larga, construcción de relaciones, audiencia de comunicación
   - **TikTok/Reels:** Alcance amplio, entertainment-first, demos más jóvenes
2. Aplicar la matriz de selección **Platform**:
   - presencia de audiencia (donde ya pasa el tiempo su público)
   - Formato de contenido (acopla tu estilo de creación natural)
   - Mecánica de distribución ( potencial de alcance orgánico)
   - Ruta de la monetización (paginas, cursos, consultoría)
3. Seleccionar **1 plataforma primaria** y **1 plataforma secundaria**
4. Definir el **content-native formato** para cada plataforma
5. Configurar perfiles con POV arañador bio/description

### Fase 3: Cadencia de Contenidos de Diseño

1. Crear el ** Sistema de Pilar de Contenido** (3-5 pilares):
   - Cada columna se conecta al polvo arañador
   - Cada pilar tiene 10+ subtópicos
   - Cubierta de Pilares: educación, opinión, historia, táctica, inspiración
2. Diseño de la **weekly contenido cadencia**:
   - Frecuencia de publicación por plataforma
   - Rotación tipo contenido (pillar 1 Mon, pilar 2 Wed, etc.)
   - Plazos de participación (respondientes a los comentarios, DMs)
3. Construir el ** Motor de Reposición de Contenido**:
   - Larga forma (newsletter/blog) √≥ Short-form (puestos sociales)
   - Tejidos  ⁇  Carousel  ⁇  script de vídeo
   - Cada 1 long-form pieza = 5-10 piezas derivadas
4. Crear un paquete de inicio de contenido **30 días**:
   - 12 post/article outlines
   - 4 piezas "hero" (sinmersiones profundas)
   - 4 ganchos de compromiso (cuestaciones, encuestas, debates)
5. Definir el **minimum cadencia viable** - qué publicar incluso en la peor semana

### Fase 4: Construir la Cohorte y la Medida

1. Diseñar la Pipeline **Audience-to-Cohort**:
   - Contenido gratis √≠e Email capture √ Núrture √≠e Paid cohort
   - Define el **lead imanes** alineados con el arañador POV
   - Diseñar el **nurture secuencia** (5-7 emails)
2. Aplicar ** Principios del curso basado en el cohorte** si procede:
   - Resultados orientados (los estudiantes logran X en semanas Y)
   - Responsabilidad mediante plazos y interacción entre pares
   - Transformación √ Información
3. Definir **audience métricas de crecimiento**:
   - Follower/subscriber Tasa de crecimiento
   - Tasa de compromiso (interacciones / impresiones)
   - Crecimiento de la lista de correo electrónico y tasa abierta
   - Contenido...to-lead Tasa de conversión
   - Audiencia...to-customer Tasa de conversión
4. Conjunto **milestone Metas**:
   - 30 días: Cadence estableció, primero 100 seguidores comprometidos
   - 90 días: Spiky POV reconocido, primero 500 comprometidos
   - 6 meses: Autoridad establecida, camino de monetización claro
5. Crear el **weekly ritual de revisión** - 15 min para comprobar métricas y ajustar

## Formato de salida

```yaml
audience_strategy:
  expertise: "{domain}"
  target_audience: "{description}"
  spiky_pov:
    primary: "{Siguiente asquerosa POV}" 
    supporting: ["{pov1}", "{pov2}"]
  platform:
    primary: "{platform}"
    secondary: "{platform}"
    format: "{ formato de contenido nativo}" 
  content_cadence:
    pillars: ["{pillar1}", "{pillar2}", "{pillar3}"]
    frequency: "{X posts per week}" 
    repurposing_ratio: "1 long-form = {X} derivatives"
  cohort_pipeline:
    lead_magnet: "{description}"
    nurture_length: "{X emails}" 
    cohort_ready: "{yes turbandonoapreviafuturo}" 
  milestones:
    30_day: "{target}"
    90_day: "{target}"
    6_month: "{target}"
  deliverables:
    - spiky-pov-analysis.md
    - content-strategy.md
    - content-calendar-30day.md
    - audience-metrics.md
```

## Condiciones de veto

1. **Nunca empiece a crear contenido sin un POV ardedor** -- el contenido genérico se ahoga en el ruido
2. **Nunca estés en más de 2 plataformas simultáneamente** - esparcido demasiado delgado significa que ninguna tracción en cualquier lugar
3. **Nunca publicar sin un plan de rescate** - cada pieza debe generar múltiples derivados
4. **Nunca mide sólo el número de seguidor** - tasa de compromiso importa más que las métricas de vanidad
5. **Nunca salte el examen "¿Alguien podría discutir?"* - un POV con el que nadie discrepa es invisible

## Criterios de finalización

- [ ] POV picante identificado y validado (1 primario, 2-3 soporte)
- [ ] Plataforma seleccionada con análisis de formato
- [ ] Los pilares de contenido definidos (3-5) con subtópicos
- Cadencia de contenido semanal diseñada
- [ ] 30 días de inicio de contenido de paquete describido
- Audience...to-cohort tuberías mapeadas
- [ ] Conjunto de métricas de crecimiento y hitos (30/90/180 días)
- [ ] La salida coincide con el esquema anterior
