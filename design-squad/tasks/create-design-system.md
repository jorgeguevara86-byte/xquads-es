---
task: createDesignSystem()
responsavel: "@brad-frost"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: project_context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: tech_stack
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: designSystem
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Auditoría de la interfaz completada con incoherencias documentadas" 
  - "[ ] Todas las fichas de diseño definidas (colores, tipografía, espaciado, fronteras, sombras)" 
  - "[ ] Documentación completa con ejemplos y guía de contribución" 
---

# Task: Atomic Design System Creation

** ID de usuario: ** DESIGN-001
**Version:** 1.0.0
**Command:** `*create-design-system`
Brad Frost (Ed. Frost)brad-frost) + Dan Mall (dan-mall)
**Purpose:** Construir un sistema completo de diseño atómico de la auditoría a través de átomos, moléculas, organismos y documentación.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `project_context` Silencioso Aplicación o descripción del producto Silencioso
| `brand_guidelines` Ø Colores, tipografía, logos TENIDO ANTERIOR
| `existing_ui` Silencio Actual pantallas de interfaz o código TENIDO ANTEFERRED
| `tech_stack` Silencio Marco de Frontend y herramientas Silencio
| `team_size` Silencio Diseño y tamaño del equipo dev Silencio NO TEN
| `accessibility_requirements` TENIDO EL objetivo del nivel de WCAG TENIDO NO (por defecto: AA)

## Preconditions

1. El contexto del proyecto y la pila de tecnología se definen
2. Existen pautas de marca (incluso mínimas — colores y fuentes al mínimo)
3. Comprensión de quién consumirá el sistema de diseño (diseñadores, desarrolladores, ambos)

## Fases de Ejecución

### Fase 1: Auditoría Existiendo (brad-frost)

1. Realizar inventario de interfaz — capturar cada componente único
2. Categorizar los elementos existentes de la UI por tipo:
   - Colores, tipografía, espaciamiento, iconos, fronteras, sombras
   - Botones, entradas, etiquetas, placas, enlaces
   - Tarjetas, formularios, navegación, modales, tablas
   - Diseños de páginas, plantillas, patrones sensibles
3. Identificar las inconsistencias — ¿cuántas variaciones existen del mismo componente?
4. Evaluar la accesibilidad actual: cumplimiento de los elementos existentes por la CMG
5. Documentar el " zoológico común" — todo lo que existe hoy
6. Identificar el 20% de los componentes que cubren el 80% de la interfaz

### Fase 2: Define los átomos (brad-frost)

1. **Tokens de color** — Define la paleta mundial, los colores semánticos y component-level alias
   - Global: colores de marca, neutrales, colores de retroalimentación (éxito, advertencia, error, info)
   - Semantic: text-primary, text-secondary, bg-surface, bg-canvas, border-default
   - Component: button-primary-bg, input-border, card-shadow
2. **Tokens de la ecografía** — Familias de fuentes, tamaños, pesos, alturas de las líneas, espaciamiento de cartas
   - Escala: xs, sm, base, lg, xl, 2xl, 3xl, 4xl
   - Semántica: heading-1 a través de heading-6, cuerpo, leyenda, etiqueta, código
3. **Tokens de ritmo** — Escala de espaciamiento constante (4px unidad base recomendada)
   - Scale: 0, 1, 2, 3, 4, 5, 6, 8, 10, 12, 16, 20, 24
4. **Tokens de borde** — Escala radial, anchuras de frontera, estilos
5. **Tokens de sombra** — Niveles de elevación (sm, md, lg, xl)
6. **Tokens de la animación** — Duración, alivio, propiedades de transición
7. **Tokens de punto débil** — Puntos de ruptura responsables
8. Documentar cada átomo con las directrices de uso

### Fase 3: Construir Molecules & Organisms (brad-frost + dan-mall)

** Moléculas (grupos de componentes simples):**
1. Grupo de botones (botón + icono + etiqueta)
2. Campo de entrada (etiqueta + entrada + mensaje de error + ayudador)
3. Barra de búsqueda (introducción + botón + icono)
4. Objeto de medios (imagen + bloque de texto)
5. Objeto de navegación (icon + etiqueta + placa)
6. Cabecera de la tarjeta (avatar + título + subtítulo + acción)

**Organismos (grupos de componentes complejos):**
1. Barra de navegación (logo + artículos nav + búsqueda + menú de usuario)
2. Sección de formularios (cabeza + descripción + múltiples campos de entrada + acciones)
3. Tabla de datos (cabeza + filas + paginación + filtros)
4. Tarjeta (cabeza + medios + contenido + pie + acciones)
5. Modal (superposición + encabezado + contenido + acciones de pie)
6. Sidebar (logo + navegación + información del usuario + pie)

Para cada componente:
- Definir variantes (tamaño, color, estado)
- Especificar estados interactivos (por defecto, aparador, enfoque, activo, desactivado, carga)
- Document props/API
- Escribir requisitos de accesibilidad ( roles de la agenda, teclado nav, lector de pantalla)
- Crear especificación de comportamiento sensible

### Fase 4: Documento (*dan-mall)

1. **Empiezo a la instalación, configuración y uso de primer componente
2. **Principios de diseño** - El "por qué" detrás de las decisiones de diseño
3. **Token Reference** - Catálogo completo de fichas con ejemplos visuales
4. **Catálogo Componente**: Cada componente con:
   - Descripción y propósito
   - Ejemplos en vivo con todas las variantes
   - Props/API documentation
   - No, no, no, con ejemplos visuales.
   - Notas de accesibilidad
   - Códigos de los naipes (copy-paste listos)
5. **Pattern Library** — Composiciones y diseños comunes
6. ** Guía de la contribución** - Cómo add/modify componentes
7. ** Modelo de la gobernanza** — Quién aprueba cambios, versión, proceso de deprecación

## Formato de salida

```yaml
design_system:
  name: "{Nombre del sistema}" 
  creators: [brad-frost, dan-mall]
  methodology: "Diseño atómico" 
  tech_stack: "{framework}"
  accessibility_target: "WCAG 2.1 AA" 
  tokens:
    colors: "{contando de token}" 
    typography: "{contando de token}" 
    spacing: "{contando de token}" 
    borders: "{contando de token}" 
    shadows: "{contando de token}" 
  components:
    atoms: ["{list}"]
    molecules: ["{list}"]
    organisms: ["{list}"]
    templates: ["{list}"]
  documentation:
    getting_started: true
    token_reference: true
    component_catalog: true
    pattern_library: true
    contribution_guide: true
    governance_model: true
  governance:
    versioning: "semver"
    approval_process: "{description}"
    deprecation_policy: "{description}"
```

## Condiciones de veto

** NUNCA** saltar la fase de auditoría -construyendo sin entender lo que existe crea duplicación
* ** NUNCA** definir componentes sin accesibilidad desde el principio; la adaptación es 10x más difícil
- **Nunca** crear fichas sin una convención y jerarquía claras de nombres
- ** NUNCA** saltar documentación - un sistema de diseño indocumentado no será adoptado
- ** NUNCA** construye organismos antes de que los átomos y las moléculas sean sólidos

## Criterios de finalización

- [ ] Auditoría de la interfaz completada con incoherencias documentadas
- [ ] Todas las fichas de diseño definidas (colores, tipografía, espaciado, fronteras, sombras)
- [ ] Atom documentado con las directrices de uso
- Moleculas y organismos construidos con variantes y estados
- [ ] Requisitos de accesibilidad definidos para cada componente
- [ ] Documentación completa con ejemplos y guía de contribución
- [ ] Modelo de gobernanza establecido para el mantenimiento en curso
