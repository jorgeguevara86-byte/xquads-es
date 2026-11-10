---
task: buildNarrative()
responsavel: "@story-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: story_concept
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: genre_or_context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: false

Saida:
  - campo: narrative_structure
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Marco seleccionado con razonamiento" 
  - "[ ] Todos los latidos estructurales definidos y poblados" 
  - "[ ] arco emocional mapeado de principio a fin" 
---

# Task: Story Structure Creation

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*build-narrative`
**Agente:** Jefe de Historiastory-chief) rutas a Campbell, Snyder, o Harmon
**Purpose:** Construir una estructura narrativa completa utilizando el marco de narración más adecuado.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `story_concept` Silencio Silencio Silencio Silencio Silencio Silencio
| `genre_or_context` Silencioso descripción de usuario Silencio
| `target_audience` Silencio vocacional vocablo viv 
| `format` Silencio, televisión, libro, presentación, marca TENIDO NO TENIDO
| `existing_material` Silencioso borrador, esquema, notas Silencio NO TEN
| `preferred_framework` Silencio, Hero, Beat Sheet, Story Circle TENIDO NO TENIDO

## Preconditions

1. El concepto o la idea de la historia se proporciona (incluso rough/incomplete está bien)
2. Al menos existe un sentido general del público o propósito previsto
3. Catálogo de marcos narrativos es accesible

## Fases de Ejecución

### Fase 1: Identifique el Marco (story-chief)

1. Analizar el concepto de historia — tema, género, escala, núcleo emocional
2. Determinar el mejor partido marco:
   *El viaje de Hierro* *transformaciones épicas, escala mítica, personajes arquetípicos*
   - **Características (Snyder)** - Guiones comerciales, trama apretada, audience-friendly estructura
   - **Círculo de historia (Harmon)** - episodios de televisión, character-driven arcos, viajes relatables
3. Si el usuario especifica un marco, honrar la preferencia
4. Si no hay preferencia, recomiende con razonamiento y confirme antes de proceder
5. Ruta hacia el agente especialista adecuado

### Fase 2: Estructura de construcción

Si Hero es el viaje (joseph-campbell):**
1. Definir el mundo ordinario - establecer normal antes de la perturbación
2. Identificar el Llamado a la Aventura - lo que perturba el status quo
3. Mapear el cruce de la Umbral - compromiso con el viaje
4. Pruebas de diseño, aliados y enemigos - la aventura se desarrolla
5. Elabore el Ordeal — la crisis central y la transformación
6. Define la recompensa, la vuelta por carretera y la resurrección
7. Cerrar con el regreso con el Elixir - la transformación completa

Si la hoja de la botablake-snyder):**
1. Imagen de apertura - tesis visual del mundo antes
2. Tema declarado: la lección que la historia enseñará
3. Set-Up, Catalyst, Debate — introducción a través del compromiso
4. Entrar en Dos - el héroe entra en el upside-down mundo
5. B Historia, Diversión y Juegos - la promesa de la premisa
6. Punto medio, chicos malos cerca - las apuestas escalan
7. Todo está perdido, noche oscura del alma — punto más bajo
8. Entrar en Tres, Finale - la solución y el climax
9. Imagen final - antítesis visual que muestra transformación

**Si el Círculo de Historia (dan-harmon):**
1. USTED - Establecer el carácter en su zona de confort
2. NECESO - Algo falta o desea
3. GO - Entran en una situación desconocida
4. ATENCIÓN - Se adaptan y luchan
5. FIND — Ellos consiguen lo que querían
6. TAKE - Pero pagan un precio pesado
7. RETURN - Ellos vuelven a lo familiar
8. CAMBIO - Son transformados por la experiencia

### Fase 3: Flesh Out Beats

1. Para cada latido estructural, definir:
   - La escena o el momento (lo que sucede)
   - El estado emocional del protagonista
   - El conflicto o la tensión presentes
   - Cómo se conecta al tema
2. Identificar el arco emocional — la evolución de la sensación de mapa de principio a fin
3. Asegurar que las estacas se intensifiquen, cada golpe aumenta la tensión
4. Verificar la integración temática - cada golpe refuerza el mensaje central

### Phase 4: Review Arc

1. Comprobar la integridad — no hay brechas estructurales ni la pérdida de ritmos
2. Verificar la coherencia emocional - el arco se siente natural y ganado
3. Prueba la transformación - ¿Se siente el final satisfactorio e inevitable?
4. Evaluar el pacing - no golpes de lija demasiado largo o precipitaciones demasiado rápido
5. Confirme la alineación del público - ¿Responderá esto al público objetivo?
6. Proporcionar notas de revisión para cualquier punto débil

## Formato de salida

```yaml
narrative_structure:
  concept: "{ concepto de historia}" 
  framework: "Hero's Journey ¦ Beat Sheet ¦ Historia Circle" 
  specialist: "joseph-campbell | blake-snyder | dan-harmon"
  genre: "{ Género identificado}" 
  theme: "{Tema central}" 
  protagonist:
    name: "{character}"
    starting_state: "{antes de la transformación}" 
    ending_state: "{después de la transformación}" 
  beats:
    - beat_number: 1
      name: "{beat name}" 
      description: "¿Qué pasa?" 
      emotional_state: "{feeling}"
      conflict: "{tension}"
      theme_connection: "¿Cómo se relaciona con el tema?" 
  emotional_arc: "{descripción del viaje emocional}" 
  pacing_notes: "{ observaciones de ritmo y tempo}" 
  revision_suggestions: ["{áreas para fortalecer}" ]
```

## Condiciones de veto

- **Nunca** forzar un marco que no se ajuste a la naturaleza de la historia
- ** NUNCA** saltar los latidos o elementos estructurales - cada marco requiere la integridad
- ** NUNCA** ignora el arco emocional a favor de los mecánicos de trama
- ** NUNCA** estructura de construcción sin conectar cada golpe al tema
* * NUNCA** asume el formato – confirma con el usuario cuando ambiguo

## Criterios de finalización

- [ ] Marco seleccionado con razonamiento (o preferencia de usuario honrado)
- [ ] Todos los latidos estructurales definidos y poblados
- El arco emocional se mapeó de principio a fin
- [ ] Tema integrado en cada golpe
- [ ] Pacing evaluado and balanced
Arc revisó para su integridad y coherencia
[ ] Sugerencias de revisión proporcionadas para zonas débiles
