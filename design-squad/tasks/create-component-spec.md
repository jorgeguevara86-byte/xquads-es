---
task: createComponentSpec()
responsavel: "@design-system-architect"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: component_name
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: tech_stack
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: componentSpec
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Todas las variantes especificadas (tamaño, intención, estado, diseño, contenido)" 
  - "[ ] Tokens de diseño mapeado con cadena descomposición" 
  - "[ ] Requisitos de accesibilidad completos (ARIA, teclado, lector de pantalla)" 
---

# Task: Component Specification

** ID de usuario: ** DESIGN-004
**Version:** 1.0.0
**Command:** `*create-component-spec`
**Agente:** Arquitecto del Sistema de Diseñodesign-system-architect) + Brad Frost (brad-frost)
**Purpose:** Crear una especificación completa de componentes con variantes, fichas, accesibilidad y documentación de API.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `component_name` Silencioso petición de usuario Silencio Silencio
| `component_purpose` ← Qué problema resuelve TENIDO ANTERIOR
| `design_system_context` TENIDO TENIDO TENIDO RESISTENCIAS Y patrones existentes
| `tech_stack` TENIDO Marco (Reacto, Vue, Svelte, etc.) TENIDO YES TENIDO
| `usage_context` Silencio donde se utilizará Silencio preFERRED TERRITOR ANTE
| `reference_examples` TENIDO LAS EJECUCIONES DE LA REFERENCIA TENIENDO TENIBLE

## Preconditions

1. El propósito de los componentes está claramente definido
2. El diseño de token sistema existe (o se creará junto con)
3. La pila de tecnología es conocida por el diseño de API

## Fases de Ejecución

### Fase 1: Define el Purpose

1. Difundir el propósito del componente - ¿qué necesidad de usuario sirve?
2. Identificar dónde se encuentra en la jerarquía atómica: átomo, molécula o organismo
3. Lista de casos de uso - ¿Dónde aparecerá este componente?
4. Defina lo que este componente NO es (prevención de la crepúsculo de alcance)
5. Compruebe los componentes existentes - ¿puede ampliarse un componente existente en su lugar?
6. Determinar las dependencias de los componentes: qué atoms/molecules ¿Se compone?

### Fase 2: Variantes de diseño

1. **Varias de tamaño** — sm, md, lg (cuando sea aplicable)
2. **Color/intent variantes** — primario, secundario, peligro, advertencia, éxito, neutral
3. ** Variaciones estatales**
   - Default (estado de recuperación)
   - Hover (fusa encima)
   - Focus (foco de teclado – anillo de enfoque visible)
   - Activo (ser clicked/pressed)
   - Disabled (non-interactive)
   - Carga (operación de sincronización en curso)
   - Error (insuficiencia de validación)
   - Selected/Checked (Estado de lucha)
4. **Varias de diseño** - inline, block, full-width, comportamiento sensible
5. **Varias de contenido** — with/without icono, with/without descripción, comportamiento de truncación
6. Para cada variante, definir las especificaciones visuales: colores, espaciamiento, tipografía, fronteras

### Fase 3: Especifique las fichas

1. Estilos de componentes de mapa para diseñar fichas (nunca use valores brutos):
   - Background: `{component}-{variant}-bg`
   - Text: `{component}-{variant}-text`
   - Border: `{component}-{variant}-border`
   - Shadow: `{component}-{variant}-shadow`
   - Spacing: `{component}-padding-{size}`
   - Typography: `{component}-font-{property}`
2. Definir la cadena de retroceso de token: componente token → alias token →
3. Asegurar que todas las fichas de color soporte el modo oscuro
4. Documento que fichas son personalizables vs bloqueadas
5. Verificar las relaciones de contraste cumplen con el texto WCAG AA (4.5:1, 3:1 elementos de la interfaz de usuario)

### Phase 4: Document API

1. **Props/Attributes:**
   - Nombre, tipo, valor predeterminado, descripción
   - Requerido vs opcional
   - Valores válidos para enums
2. **Events/Callbacks:**
   - Nombre del evento, carga, cuando se dispara
3. **Slots/Children:**
   - Nombradas ranuras y su contenido esperado
   - Comportamiento de tragamonedas predeterminado
4. **Accessibility:**
   - Papel y atributos ARIA
   - Patrón de interacción de teclado (Tab, Enter, Space, teclas de flecha, Escape)
   - Comportamiento de anuncio del lector de pantalla
   - Gestión de focos (donde va el foco, comportamiento de trampa)
   - Verificación de contrastes de color
5. **Comportamiento responsable:**
   - Adaptaciones específicas para puntos de ruptura
   - Tamaños de objetivos táctiles (mínimo 44x44px)
   - Interacciones específicas para móviles
6. ** Ejemplos del proyecto:**
   - Uso básico
   - Cada variante
   - Composición con otros componentes
   - Patrones comunes

## Formato de salida

```yaml
component_spec:
  name: "{nombre completo}" 
  creators: [design-system-architect, brad-frost]
  atomic_level: "Atom" 
  purpose: "¿Qué hace?" 
  dependencies: ["{required sub-components}"]
  variants:
    sizes: ["{Size list}" ]
    intents: ["{lista de intención}" ]
    states: ["{lista de estado}" ]
  tokens:
    - token: "{nombretoken}" 
      value: "{valor predeterminado}" 
      customizable: true
      dark_mode: "{valor oscuro}" 
  props:
    - name: "{nombre de propiedad}" 
      type: "{type}"
      default: "{default}"
      required: true
      description: "¿Qué controla?" 
  events:
    - name: "{nombre del mismo}" 
      payload: "{tipo de datos}" 
      description: "{Cuando se dispara]" 
  accessibility:
    role: "{ARIA TURNES}" 
    keyboard: ["{Función de interacción}" ]
    announcements: ["{¿Tenerencia de lector de pantallas )" ]
    contrast: "verificada AA" 
  responsive:
    breakpoints: ["{adaptations}"]
    touch_target: "44x44px mínimo" 
  code_examples:
    basic: "{code}"
    variants: "{code}"
    composition: "{code}"
```

## Condiciones de veto

** NUNCA** especificar un componente sin requisitos de accesibilidad - no son opcionales
- **Nunca** utilizar crudo color/spacing valores — siempre referencia fichas de diseño
* * * NUNCA* saltar estados interactivos: el afianzamiento, el enfoque, el activo y los discapacitados son obligatorios
- ** NUNCA** crear un componente que duplica el propósito de un componente existente
- ** NUNCA** omitir patrones de interacción del teclado - no todos los usuarios utilizan un ratón

## Criterios de finalización

- [ ] Objetivo de componente definido con un alcance claro
- [ ] Todas las variantes especificadas (tamaño, intención, estado, diseño, contenido)
- [ ] Tokens de diseño mapeado con cadena descomposición
- [ ] Props/API documentado completamente con tipos y defectos
- [ ] Requisitos de accesibilidad completos (ARIA, teclado, lector de pantalla)
- [ ] Comportamiento responsable definido con objetivos táctiles
- [ ] Ejemplos de códigos previstos para todos los casos de uso principal
- Valores de token de modo oscuro definidos
