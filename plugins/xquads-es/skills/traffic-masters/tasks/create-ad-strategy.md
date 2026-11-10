---
task: createAdStrategy()
responsavel: "@traffic-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: adStrategy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] 3-5 segmentos de audiencia definidos con detalles de selección" 
  - "[ ] Estructura de campaña mapeada por estadio de embudo" 
  - "[ ] Presupuesto asignado con desglose diario y mensual" 
---

# Task: Create Ad Strategy

** ID de la lista de gastos**
**Version:** 1.0.0
**Command:** `*create-ad-strategy`
**Agente:** Jefe de Tráficotraffic-chief) rutas a experto en plataforma
**Purpose:** Diseño platform-specific estrategia de publicidad pagada con objetivos, dirección creativa y asignación presupuestaria.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silenciosidad cadena Silencio Usuario prompt Silencio Yes Silencio Producto o servicio para anunciar Silencio
Silencio audiencia Silencio Silencio Silencio Usuario prompt Silencio Sí Silencio Popularidad demográfica y psicografÃ3gica Silencio
Silencioso plataforma Silencio enum Silencio Usuario prompt Silencio Sí Silencio facebook, google, youtube, tiktok, linkedin, multi-platform |
Silencio presupuesto Silencio número Silencio Sugerencia de usuario Silencio Silencio Presupuesto de publicidad mensual Silencio
TENVIO TENEDAD TENIDO ANTERIOR ANTERIOR SI TENENCIAS, SEGURIDAD, TC, Líderes, Ventas, app-installs |
Silencioso funnel Silencio cadena Silencioso invocar usuario Silencio No Silencio Página de aterrizaje o embudo URL/description |
| current_performance TEN-OTO TENIDO ANTERIOR NO TENIDO métricas existentes si se ejecutan anuncios ya TEN

---

## Preconditions

- Presupuesto definido con asignación mensual clara
- La página de aterrizaje o embudo existe (o se está construyendo)
- Plataforma seleccionada en función de dónde pasa el tiempo el público

---

## Fases de Ejecución

### Fase 1: Arquitectura Audiencia
1. Definir los segmentos de audiencia primaria (3-5 segmentos):
   - Demografías: edad, género, ubicación, ingresos
   - Psicografías: intereses, comportamientos, puntos de dolor
   - Orientación específica para plataformas: audiencias personalizadas, parecidos, pilas de interés
2. Mapa de cada segmento a una etapa de embudo:
   - Nunca oí hablar de ti (prospección)
   - Calentamiento: Comprobada con contenido o visitada (retargeting)
   - Caliente: Añadido al carrito, precios vistos, compradores anteriores (remarketing)
3. Tamaño de cada audiencia y estimación alcanzan en el presupuesto dado
4. Priorizar los segmentos mediante el programa de actividades conjuntas

### Fase 2: Arquitectura de Campaña
1. Campañas de estructura por etapa objetiva y de embudo:
   - Top of Funnel: Awareness/engagement campañas (conocidos fríos)
   - Medio de embudo: Campañas de consideración (puertas en alerta)
   - Fondo de embudo: Campañas de conversión (audiencias calientes)
2. Definir los conjuntos de anuncios dentro de cada campaña:
   - Audiencias por conjunto de anuncios
   - Asignación presupuestaria por conjunto ad
   - Selección de alojamiento (feed, stories, search, display, in-stream)
3. Establecer estrategia de licitación por campaña:
   - Consideraciones de la fase de aprendizaje
   - Gotas de bid vs.
   - Presupuesto mínimo por anuncio establecido para significación estadística

### Phase 3: Creative Strategy
1. Definir temas creativos por estadio de embudo:
   - TOF: Sensibilización sobre problemas, curiosidad, entretenimiento
   - MOF: Proof, educación, diferenciación
   - Oferta, urgencia, testimonios
2. Especifique los formatos de anuncio por plataforma:
   - Facebook/IG: Imagen estatica, carrusel, video (15s, 30s, 60s), colección
   - Google: Búsqueda (RSA), Visualización, Performance Max, YouTube
   - TikTok: vídeo de estilo UGC, anuncios de chispa, efectos de marca
   - LinkedIn: Imagen individual, carrusel, vídeo, anuncios de conversación
3. Proporcionar información creativa para los primeros 3-5 anuncios por etapa
4. Definir el marco de prueba: qué variables probar primero

### Fase 4: Presupuesto y Marco KPI
1. Asignar presupuesto en etapas de embudo:
   - Se sugiere división: 60% TOF, 25% MOF, 15% BOF (ajustada en base a la madurez)
2. Establecer objetivos de KPI por etapa utilizando parámetros de referencia de plataforma
3. Definir el calendario de optimización:
   - Día 1-3: Dejar que las campañas aprendan, no toques
   - Día 4-7: Matar a los infraperformadores, ganadores de escala
   - Semanal: Refrigerio creativo, expansión de la audiencia
   - Mensual: Revisión completa de la estrategia
4. Crear el plan de escalado: desencadenantes y métodos para aumentar el gasto

---

## Formato de salida

```markdown
## Ad Strategy: {Product Name}

**Platform:** {platform}
**Monthly Budget:** ${budget}
**Objective:** {objective}
**Estimated ROAS:** {X}:1

---

### Audience Segments

| Segment | Type | Size | Targeting | Funnel Stage |
|---------|------|------|-----------|-------------|

### Campaign Structure

| Campaign | Objective | Audience | Daily Budget | Placements |
|----------|----------|----------|-------------|------------|

### Creative Strategy

| Stage | Format | Theme | Hook Angle | CTA |
|-------|--------|-------|-----------|-----|

### Creative Briefs
{3-5 ad creative briefs with copy direction and visual notes}

### Budget Allocation

| Stage | % Budget | Monthly | Target CPA/ROAS |
|-------|---------|---------|----------------|

### KPI Targets

| Metric | TOF | MOF | BOF |
|--------|-----|-----|-----|

### Optimization Schedule
| Timeframe | Action | Criteria |
|-----------|--------|----------|

### Scaling Plan
| Trigger | Method | Budget Increase |
|---------|--------|----------------|
```

---

## Condiciones de veto

- NUNCA campañas de lanzamiento sin un plan de fase de aprendizaje - matando anuncios demasiado tempranos presupuesto de desechos
- Nunca asignar el 100% de presupuesto a BOF - se agotará el público caliente en días
- NUNCA salta el tamaño del público – gastar en audiencias demasiado pequeñas causa fatiga de frecuencia
- Nunca recomiende una plataforma donde el público objetivo no esté activo
- NUNCA establecer objetivos KPI sin referencias de plataformas de referencia

---

## Criterios de finalización

- [ ] 3-5 segmentos de audiencia definidos con detalles de la orientación
- [ ] Estructura de campaña mapeada por el estadio de embudo
- [ ] Estrategia creativa definida por etapa con breves
- [ ] Presupuesto asignado con desglose diario y mensual
- [ ] objetivos KPI fijados por estadio de embudo
- [ ] Calendario de optimización documentado
- Plan de escalado definido con disparadores
