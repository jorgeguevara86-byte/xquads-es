---
task: generateHandoff()
responsavel: "@ui-engineer"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: design_files
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: tech_stack
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: handoffDocumentation
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Todos los componentes inventoried y mapeados para el sistema de diseño" 
  - "[ ] Cada valor visual mapeado a un diseño token" 
  - "[ ] Examen de Dev completado con los desembolsos documentados" 
---

# Task: Developer Handoff Documentation

** ID de usuario: ** DESIGN-006
**Version:** 1.0.0
**Command:** `*generate-handoff`
**Agente:** Ingeniero de la UI (UI)ui-engineer) + Dan Mall (dan-mall)
**Purpose:** Generar documentación de entrega completa para desarrolladores design-to-code traducción.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `design_files` | Figma/Sketch archivos o capturas de pantalla TENIDO YES TENIDO
| `design_system` Silencio Sistema de diseño existente referencia Silencio
| `tech_stack` TENCIÓN Marco de Frontend y enfoque CSS ANTERIOR YES ANTERIOR
| `component_list` Silencio Componentes utilizados en el diseño Silencio Preferenciado Silencio
| `interaction_specs` Silencioso Animaciones, transiciones, estados de la hover TENIDO ANTERIOR
| `responsive_requirements` Silenciosos Puntos de descanso y comportamiento de adaptación TENIDO NO TENIDO

## Preconditions

1. Los diseños se ultiman y aprueban
2. Existe un sistema de diseño (o se especifican los valores de ficha)
3. La pila de tecnología es conocida code-specific Orientación
4. Los comportamientos interactivos se documentan o son demostrables

## Fases de Ejecución

### Fase 1: Componentes de inventario

1. Mapa de cada componente único utilizado en los diseños
2. Para cada componente, determinar:
   - ¿Existe ya en el sistema de diseño? (Referencia existente)
   - ¿Es una variante de un componente existente?
   - ¿Es completamente nuevo? (Flag para el diseño de la adición del sistema)
3. Crear un árbol de dependencia de componentes - ¿qué componentes componen a otros?
4. Identificar patrones compartidos — diseños reutilizables, patrones de espaciamiento, patrones de interacción
5. Listar todos los iconos, ilustraciones y activos de los medios necesarios
6. Documento third-party componentes o bibliotecas necesarios

### Fase 2: Especifique las fichas

1. ** Mapping de color** — Mapa de cada color en el diseño a un token de diseño
   - Si no existe token, proponga una nueva ficha semántica
   - Documentar valores de modo ligero y oscuro
   - Verificar las relaciones de contraste (Acumulación: 4,5:1 texto, 3:1 UI)
2. **Mapateo de la fotografía** — Mapa de todos los estilos de texto a las fichas tipográficas
   - Familia de fuentes, tamaño, peso, altura de línea, espaciamiento de cartas
   - Ajustes de escala de tipo responsable
3. **Acelerando la preparación** — Map all padding, margins, and gaps to spacing tokens
   - Espaciamiento interno de componentes
   - Entre el espacio de competencia
   - Sección y page-level espaciamiento
4. **Border and Shadow Mapping** — Mapa de estilos decorativos a fichas
5. **Motion Mapping** — Animaciones de mapa a tokens de movimiento (duración, distensión, propiedades)
6. Exportar un total token-to-design Cuadro de asignación

### Fase 3: Interacciones de documentos

1. ** Transiciones estatales** — Para cada elemento interactivo:
   - Default → Hover: ¿Qué cambios? (color, sombra, escala, cursor)
   - Predeterminado → Focus: ¿Qué cambios? (outline, ring, background)
   - Predeterminado → Activo: ¿Qué cambios? (transform, color)
   - Predeterminado → Discapacitados: ¿Qué cambios? (opacidad, cursor, pointer-events)
2. ** Interacciones micro** — Animaciones desencadenadas por acciones del usuario:
   - Comentarios de prensa de Button
   - Apariencia de validación de formularios
   - Toast/notification entrada y salida
   - Indicadores de carga y pantallas esqueleto
   - Transiciones de páginas
3. ** Apoyo a la tecnología** — Interacciones específicas para móviles:
   - Acciones de golpe
   - Tira para refrescar
   - Larga prensa
   - Pistola para ampliar
4. ** Navegación de teclado** — Orden de pestañas, teclas de acceso directo, gestión de enfoque
5. **Lógica convencional** Show/hide reglas, reglas de validación, divulgación progresiva

### Fase 4: Repasar con Dev

1. Camina por el desvío con el equipo de desarrollo
2. Ambigüedades de clarificación — dirijan cada "qué sucede cuando...?" pregunta
3. Identificar las limitaciones técnicas — ¿qué es difícil o imposible de aplicar?
4. Negociar los intercambios — ¿dónde se puede diseñar un flex para la viabilidad técnica?
5. Convenir en la prioridad de aplicación, que components/screens ¿Primero?
6. Establecer el proceso de evaluación de la situación de los riesgos de desastre: ¿cómo se diseñará la verificación de la aplicación?
7. Documentar todas las decisiones y desgravaciones del examen

## Formato de salida

```yaml
handoff:
  creators: [ui-engineer, dan-mall]
  tech_stack: "{framework}"
  design_system: "{Nombre del sistema}" 
  components:
    existing: ["{componentes del sistema de diseño}" ]
    variants_needed: ["{nuevas variantes de existentes}" ]
    new_required: ["{encimeramente nuevos componentes}" ]
  token_map:
    colors:
      - design_value: "{hex o rgba}" 
        token: "{nombretoken}" 
        usage: "¿Dónde se usó?" 
    typography:
      - design_style: "{nombre de estilo}" 
        token: "{nombretoken}" 
    spacing:
      - design_value: "{valor px}" 
        token: "{nombretoken}" 
  interactions:
    state_transitions:
      - element: "{component}"
        states: "{default → hover → enfoque → active → disabled}" 
        animation: "{duración, calmante}" 
    micro_interactions:
      - trigger: "{acción del usuario}" 
        animation: "{description}"
        duration: "{ms}"
        easing: "{function}"
    keyboard:
      tab_order: ["{Secuencia de elemento}" ]
      shortcuts: ["{key: action}" ]
  responsive:
    breakpoints: ["{ valores px}" ]
    adaptations:
      - breakpoint: "{px}"
        changes: ["{Cambios de fuga}" ]
  assets:
    icons: ["{lista de nicos con formato}" ]
    images: ["{lista de imágenes con tamaños}" ]
    fonts: ["{font files}" ]
  dev_review_notes: ["{decisiones y desvíos}" ]
  qa_checklist: ["{Artículos de verificación}" ]
```

## Condiciones de veto

- ** NUNCA** desactivar los diseños sin mapeo de token - los desarrolladores nunca deben adivinar los valores
- ** NUNCA** saltar documentación de interacción - los mockups estáticos son especificaciones incompletas
- ** NUNCA** omitir comportamiento sensible - si no se especifica, se implementará incoherentemente
- ** NUNCA** saltar la revisión de la dev - una conversación evita días de retrabajo
- **Nunca** despide sin especificaciones de accesibilidad - deben ser parte de la especificaciones, no un pensamiento posterior

## Criterios de finalización

- [ ] Todos los componentes inventoried y mapeados para el sistema de diseño
- Cada valor visual se ha trazado a un token de diseño
- [ ] Transiciones estatales documentadas para todos los elementos interactivos
- [ ] Microinteracciones especificadas con el tiempo y el alivio
- [ ] Navegación de teclado y accesibilidad documentada
- [ ] Comportamiento responsable especificado para todos los puntos de ruptura
- [ ] Activos exportados en formatos requeridos
- [ ] Revisión de Dev completado con los tradeoffs documentados
- [ ] Lista de verificación QA creada para la verificación de la implementación
