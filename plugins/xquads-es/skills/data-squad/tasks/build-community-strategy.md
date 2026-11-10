---
task: buildCommunityStrategy()
responsavel: "@david-spinks"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: business
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: community_goal
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: community_strategy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Modelo de SPACES evaluado con dimensión primaria seleccionada" 
  - "[ ] escalera de compromiso diseñado con 7 peldaños" 
  - "[ ] Community Health Score definido con 5 componentes" 
---

# Task: Build Community Strategy

** ID de usuario:** DATOS-003
**Version:** 1.0.0
**Command:** `*build-community-strategy`
**Agente:* David Spinks (David Spinks)david-spinks)
**Purpose:** Diseño community-led estrategia de crecimiento utilizando el modelo de SPACES y la escalera de compromiso

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `business` Silencio invocar a un usuario Silencioso Silencioso o descripción de producto Silencio
| `community_goal` Silencio invocar usuario Silencio Sí Silencio Objetivo principal para la comunidad ←
| `existing_community` Silencio Usuario Silencio No Silencio Situación actual de la comunidad (na, temprano, creciendo, madura) Silencio
| `platform_preference` ← Usuario Silencio No Silencio Plataforma preferida (Discord, Slack, Circle, forum, etc.) Silencio
| `resources` Silencio Usuario Silencio No Silencio Equipo y presupuesto disponibles para la gestión comunitaria Silencio

## Preconditions

- El negocio o el producto existe con usuarios identificables
- El objetivo comunitario se articula (incluso si es amplio)
- Marcos de medición cargados (`data/metrics-frameworks.yaml`)

## Fases de Ejecución

## Fase 1: Definir los Objetivos Modelo de los SPAS

1. Evaluar las dimensiones de los SPACES son las más relevantes:
   **S — Apoyo:** Los miembros se ayudan mutuamente (reducen los costos de apoyo)
   **P — Producto:** Los miembros proporcionan comentarios e ideas (mejora el producto)
   **A — Adquisición:** La comunidad atrae a nuevos clientes (reduce CAC)
   **C — Contribución:** Los miembros crean contenido o código (valor de aumento)
   **E — Participación:** Los miembros se conectan entre sí (aumento de retención)
   **S — Éxito:** Los miembros logran resultados (reduce churn)
2. Esferas de los recursos básicos por impacto empresarial
3. Seleccione **primary dimensión** (1) y **secondary Dimensiones** (1-2)
4. Definir las métricas de éxito para cada dimensión seleccionada
5. Establecer objetivos de 90 días para cada métrica

### Fase 2: Escalera de compromiso de diseño

1. Mapear la escalera de compromiso **Community Engagement** (7 peldaños):
   **Lurker:** Observa pero no participa
   **Siguiente:** Consume contenido, reacciona ocasionalmente
   - **Contributor:** Posts, comments, shares experiences
   - ** Colaborador:** Ayuda a otros, responde preguntas
   * *Cambio: * Aboga públicamente, crea contenido
   - **Asesor:** Moderados, mentores, organiza eventos
   **Asociador:** Co-crea con la marca, papel asesor
2. Para cada rancio, definir:
   - *La acción de los jugadores* - ¿Qué mueve a alguien?
   **Reconocimiento** - cómo se reconoce la progresión
   - **Permisos** - qué se desbloquea en este nivel
3. Diseño **nudge secuencias** para mover a la gente hacia arriba de la escalera
4. Identificar el **critical transición** - que salto de rancio tiene el mayor impacto
5. Crear programas de compromiso para cada rancio

## Fase 3: Lanzamiento del Plan

1. Definir la Comunidad Viable de Medios**:
   - Conteo de miembros fundadores de objetivos (típicamente 20-50)
   - Plan de semillas de contenido (10-20 inicial posts/discussions)
   - Diseño de experiencia de bienvenida
2. Elige la plataforma y configura:
   - Channel/category structure
   - Normas y directrices
   - Flujo de a bordo
3. Contratación **founding miembros**:
   - Identificar super-users de la base de clientes existente
   - Estrategia de invitación personal
   - Beneficios de los miembros fundadores
4. Crear **content calendario** para los primeros 30 días:
   - Tipos de contenido diarios
   - Incitaciones de debate
   - Eventos (AMAs, talleres, retos)
5. Definer **community rituales** - eventos recurrentes que construyen hábito

## Fase 4: Medida

1. Aplicar el **Punto de Salud Comunitaria** con 5 componentes:
   ** Tasa de actividad:** % de los miembros activos en los últimos 30 días
   ** Tasa de respuesta:** % de los puestos que reciben respuestas
   ** Tasa de crecimiento** Nuevos miembros netos por período
   - **Anotación de profundidad:** Interacciones medias por miembro activo
   - **Sentiment:** Positive/negative ratio en los debates comunitarios
2. Diseño de la **reporting Dashboard**:
   - Pulso semanal: 3 métricas superior + momentos notables
   - Revisión mensual: puntuación completa de salud + distribución de escaleras de compromiso
   - Estrategia trimestral: progreso de los recursos espaciales + ajuste por objetivo
3. Definir **intervention dispara**:
   - Tasa de actividad: 20% = crisis de compromiso
   - Tasa de respuesta cautivado 50% = revisión de la estrategia de contenido
   - El sentimiento negativo es una investigación inmediata
4. Crear **feedback loops** - cómo los datos comunitarios informan al producto y a las empresas

## Formato de salida

```yaml
community_strategy:
  business: "{name}"
  spaces_primary: "{S tuertudoP turbaA turba" 
  spaces_secondary: ["{dimension1}", "{dimension2}"]
  engagement_ladder:
    rungs: 7
    critical_transition: "{Rung X para correr Y}" 
  launch_plan:
    platform: "{platform}"
    founding_members_target: {number}
    launch_date: "{date or 'TBD'}" 
    content_seed: {number of initial posts}
  health_score:
    activity_rate: {target: "", current: ""}
    response_rate: {target: "", current: ""}
    growth_rate: {target: "", current: ""}
    depth_score: {target: "", current: ""}
    sentiment: {target: "", current: ""}
  deliverables:
    - community-strategy.md
    - engagement-ladder.md
    - launch-plan.md
    - content-calendar.md
```

## Condiciones de veto

1. **Nunca lanzar una comunidad sin miembros fundadores** - comunidades vacías mueren inmediatamente
2. **Nunca saltar la evaluación de los SPACES** - una comunidad sin propósito de negocio se convierte en un centro de costos
3. **Nunca automatizar toda interacción comunitaria** - la presencia humana auténtica es non-negotiable
4. **Nunca ignore los puntos de sentimiento negativos** - la toxicidad no tocada mata a las comunidades rápidamente
5. **Nunca mide sólo el recuento de miembros** - las métricas de vanidad ocultan comunidades moribundas

## Criterios de finalización

- [ ] Modelo de SPACES evaluado con dimensiones primarias y secundarias seleccionadas
- [ ] Escalera de compromiso diseñada con 7 peldaños y acciones de desencadenación
- [ ] Plan de lanzamiento creado con estrategia de miembro fundador
- [ ] Calendario de contenidos redactado para los primeros 30 días
- [ ] Community Health Score definido con 5 componentes
- [ ] Se establecieron los desencadenantes de intervención
- [ ] 90 días de objetivos fijados para cada métrica clave
- [ ] La salida coincide con el esquema anterior
