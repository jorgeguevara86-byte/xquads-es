---
task: designUxFlow()
responsavel: "@ux-designer"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: feature_or_product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: target_users
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: uxFlow
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Investigación de usuario realizada con información documentada" 
  - "[ ] 2-3 personas creadas con metas y puntos de dolor" 
  - "[ ] Wireframes creado para todas las pantallas y flujos clave" 
---

# Task: UX Research &amp; Flow Design

** ID de usuario: ** DESIGN-005
**Version:** 1.0.0
**Command:** `*design-ux-flow`
**Agente:** UX Designer (ux-designer)
**Fuente:** Realizar investigaciones de usuarios y diseñar experiencias de usuarios desde personas a través de cables.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `feature_or_product` ← confidencialidad Lo que se está diseñando Silencio Silencio
| `target_users` Silencio ¿Quién usará este Silencioso
| `business_goals` ← Lo que el negocio quiere lograr TENIDO TERRITORIO
| `existing_research` TENIDO Antes investigación de usuarios, análisis TENIDO NO TENIDO
| `constraints` TENIDO Técnica, tiempo, limitaciones presupuestarias TENIDO NO TENIDO
| `competitive_context` 

## Preconditions

1. El alcance de la alimentación o del producto se define
2. Grupo de usuarios objetivo al menos se identifica con facilidad
3. Los objetivos empresariales se articulan

## Fases de Ejecución

### Fase 1: Investigación del Usuario

1. **Definir las preguntas de investigación** — ¿Qué necesitamos aprender a diseñar bien?
2. **Identificar los métodos de investigación** basados en las necesidades de los proyectos:
   - Entrevistas de usuario (cualitativa - comprensión de motivaciones y dolor)
   - Encuestas (cuantitativas - hipótesis validantes a escala)
   - Consulta contextual (usuarios conservadores en su entorno natural)
   - Clasificación de tarjetas (bajoforma modelos mentales para la arquitectura de la información)
   - Análisis competitivo (¿cómo resuelven otros este problema?)
   - Revisión analítica (¿qué nos dice los datos existentes?)
3. **Investigación del conducto**: Ejecute métodos seleccionados
4. **Sintetizar los resultados** — Identificar patrones, temas y perspectivas
5. **Crear declaraciones de información** — "Los usuarios necesitan [X] porque [Y], pero actualmente [Z]"
6. Documentar todas las conclusiones en un repositorio de investigación

### Phase 2: Persona &amp; Journey Mapping

1. **Crear personas de usuario** (2-3 personas principales):
   - Demografías, papel y contexto
   - Objetivos y motivaciones
   - Puntos de dolor y frustraciones
   - Comportamientos y hábitos
   - Cita que captura su esencia
   - Nivel de competencia técnica
2. **Mapa viaje actual** (As-Is):
   - Ataque el usuario pasa hoy
   - Acciones en cada etapa
   - Pensamientos y sentimientos en cada etapa
   - Puntos y oportunidades de dolor
   - Puntos de contacto (donde interactúan con los product/service)
3. **Mapa el viaje deseado** (Para-ser):
   - Mejora de las etapas con puntos de dolor resueltos
   - Nuevos puntos de contacto e interacciones
   - Levantamiento emocional en momentos clave
   - Momentos de delicia

### Fase 3: Arquitectura de la Información

1. **Inventario de contenido** - Qué content/features ¿Debe organizarse?
2. ** Resultados de clasificación de tarjetas** — ¿Cómo es natural que los usuarios grupúsquen información?
3. **Mapa de la selección / Mapa de la aplicación** — Estructura jerárquica pages/screens
4. ** Modelo de navegación** - Navegación primaria, secundaria y contextual
5. **Nombrar convenciones** — Etiquetas que se ajusten a los modelos mentales de los usuarios (no a la jerga interna)
6. **Buscar y filtrar** — Cómo los usuarios encuentran contenido dentro de la estructura
7. Validar IA con pruebas de árboles (¿pueden los usuarios encontrar lo que necesitan?)

Fase 4: Wireframes

1. **Bonitos de fidelidad de lo bajo** — Exploración rápida de opciones de diseño (3-5 alternativas por pantalla clave)
2. **Mid-fidelity wireframes** — Selected approach refinado with:
   - Sujeta la red y espaciamiento
   - Colocación y jerarquía de componentes
   - Prioridad de contenido (lo que es más importante en cada pantalla)
   - Patrones de interacción (cómo se mueven los usuarios entre estados)
   - Estados de error y estados vacíos
   - Estados cargados
3. ** Flujos de usuarios** — Paso a pasoby-step caminos para tareas clave:
   - Feliz camino (todo va bien)
   - Camino de error (lo que sucede cuando las cosas van mal)
   - Casos de borde (con escenarios inusuales pero válidos)
4. **Anotación** — Comportamientos de interacción de documentos, reglas de validación, lógica condicional
5. ** Consideraciones responsables** — Cómo se adaptan los marcos de cable en los puntos de ruptura

## Fase 5: validación &quot; Testing

1. ** Pruebas de uso** — Cables de prueba con 5+ usuarios representativos
2. **Task tasa de éxito** — ¿Pueden los usuarios completar tareas clave?
3. **Hora en la tarea** — ¿Cuánto tarda cada tarea?
4. ** Tasa de emergencia** — ¿Dónde cometen errores los usuarios?
5. **Satisfacción** — ¿Cómo se sienten los usuarios sobre la experiencia?
6. Conclusiones de documentos e itinerarios sobre los marcos de cable
7. Cables de cable validados para diseño visual y desarrollo

## Formato de salida

```yaml
ux_flow:
  designer: "ux-designer"
  feature: "{feature/product name}"
  research:
    methods_used: ["{methods}"]
    key_insights: ["{declaraciones de la vista}" ]
    participants: 0
  personas:
    - name: "{Nombre de persona}" 
      role: "{role}"
      goals: ["{goals}"]
      pain_points: ["{pains}"]
      quote: "{Cúdula representativa}" 
  journey_map:
    stages: ["{Stage list}" ]
    pain_points: ["{dolores de llaves}" ]
    opportunities: ["{ oportunidades de diseño}" ]
  information_architecture:
    site_map: "{descripción de la estructura}" 
    navigation_model: "{Navidulidad patrón}" 
    key_labels: ["{naming}"]
  wireframes:
    screens: ["{ lista de pantalla}" ]
    user_flows: ["{lista de flujo}" ]
    interaction_notes: ["{ructus de teclas}" ]
  validation:
    method: "{Metodo de prueba}" 
    task_success_rate: "{percentage}"
    key_findings: ["Lo que aprendimos." ]
    iterations: ["{Cambios hechos}" ]
```

## Condiciones de veto

- ** NUNCA** saltar la investigación del usuario y saltar directamente a los marcos de cable — las suposiciones conducen al diseño desperdiciado
- ** NUNCA** diseño para una persona única - considerar la gama de usuarios
- ** NUNCA** utilizar la jerga interna en navegación o etiquetas, utilizar el lenguaje del usuario
- ** NUNCA** diseñar sólo el camino feliz - estados de error y casos de borde son parte de la experiencia
- ** NUNCA** Saltar pruebas de usabilidad: diseños no probados son supuestos, no soluciones

## Criterios de finalización

- [ ] Investigación de usuario realizada con información documentada
- [ ] 2-3 personas creadas con goles y puntos de dolor
- [ ] Mapa de viaje creado mostrando estados actuales y deseados
- [ ] Arquitectura de información definida y validada
- [ ] Wireframes creado para todas las pantallas y flujos clave
- [ ] Estados de error, estados vacíos y estados de carga diseñados
- [ ] Pruebas de uso completado con los resultados documentados
- Wireframes se calienta en base a resultados de prueba
