---
task: createIdentity()
responsavel: "@identitario"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: spark_analysis
    tipo: string
    origem: "Producto de la fase 1" 
    obrigatorio: true
  - campo: cause
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: identity_architecture
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Sistema de creencias definido con convicción central" 
  - "[ ] Marcadores tribales diseñados en todas las categorías" 
  - "[ ] Perteneciente a la gradiente definida con 5 niveles" 
---

# Task: Create Identity

** ID de la lista:** MOVIMIENTO-003
**Version:** 1.0.0
**Command:** `*create-identity`
**Agente:** Identitario (identitario)
**Purpose:** Architectar el sistema de identidad completo para un movimiento que incluye creencias, marcadores, rituales y señales

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `spark_analysis` Silencio Fase 1 salida Silencio Sí Silencio Análisis fenomenológico con chispa validada
| `cause` Silencio invocar a un usuario Silencio Silencio La causa o propósito del movimiento Silencio
| `audience` Silencio insinuar usuario Silencio Silencio
| `existing_brand` Silencio Usuario Silencio No Silencio Bienes de marca existentes para incorporar Silencio
| `cultural_context` Silencio Silencio Silencio No Silencio Normas culturales y sensibilidades

## Preconditions

- Análisis de chispa completado y validado (MOVEMENT-002 o Fase 1 de MOVEMENT-001)
- Marcos de movimiento cargados (`data/movement-frameworks.yaml`)
- Intensidad de tensión colectiva √= 3 (movement-grade)

## Fases de Ejecución

### Phase 1: Define Belief System

1. Extracto **core valores** del análisis de chispa (3-5 valores)
2. Traducir valores en **beliefs** -- "Creemos que..."
3. Definir el **central convicción**: la única non-negotiable creencia
4. Establecer **belief jerarquización**: fundación √≥ apoyo √≥n aspiracional
5. Crear el **belief fragmento de manifiesto** - Declaraciones de creencias 3-5
6. Prueba: puede un extraño leer estas creencias y saber inmediatamente si pertenecen

### Fase 2: Diseño de marcadores tribales

1. Definir **language marcadores** - palabras, frases y jerga únicas al movimiento
2. Diseño **visual identidad** - colores, símbolos, dirección del logotipo, estética
3. Crear **behavioral marcadores** - acciones que señalen la membresía
4. Establecer **status marcadores** - cómo los miembros muestran profundidad de compromiso
5. Diseño **greeting/ rituales de reconocimiento** - cómo los miembros se reconocen
6. Construir el inventario ** de marcadores** con las directrices de uso

### Fase 3: Crear rituales

1. Diseño de la **initiation ritual** - la experiencia de entrada para nuevos miembros
2. Crear **daily rituales** - pequeñas prácticas repetidas que refuerzan la identidad
3. Diseño **gathering rituales** - qué sucede cuando la comunidad se reúne
4. Establecer **celebration rituales** - cómo las victorias y los hitos están marcados
5. Crear **storytelling rituales** - cómo los miembros comparten experiencias y testimonios
6. Ritmos de mapa al marco ** Arquitectura Real**: frecuencia, formato, arc emocional

### Fase 4: Establecer señales de crecimiento

1. Definir el **us vs** límite -- claro pero no hostil
2. Crear **recognition señales** - cómo los miembros se identifican entre sí en el salvaje
3. Diseño **inside referencias** - conocimiento compartido de que los miembros de los bonos
4. Establecer **loyalty marcadores** - cómo long-term Miembros reconocidos
5. Crear el **belonging gradiente** -- desde extraño curioso hasta creyente central
6. Definer **boundary reglas** - qué comportamientos conducen a la exclusión

## Formato de salida

```yaml
identity_architecture:
  movement: "{name}"
  identity_stack:
    values: ["{value1}", "{value2}", "{value3}"]
    beliefs:
      central: "{declaración de creencias core}" 
      supporting: ["{belief1}", "{belief2}"]
      aspirational: ["{belief3}"]
    behaviors: ["{behavior1}", "{behavior2}", "{behavior3}"]
    symbols: ["{symbol1}", "{symbol2}", "{symbol3}"]
    rituals: ["{ritual1}", "{ritual2}", "{ritual3}"]
  tribal_markers:
    language: ["{term1}", "{term2}", "{term3}"]
    visual: "{descripción estética}" 
    behavioral: ["{action1}", "{action2}"]
    status: ["{level1}", "{level2}", "{level3}"]
  ritual_architecture:
    initiation: "{description}"
    daily: "{description}"
    gathering: "{description}"
    celebration: "{description}"
    storytelling: "{description}"
  belonging_gradient:
    - level: "Curious"
      description: "¿Qué define este nivel?" 
    - level: "Sympathizer"
      description: "¿Qué define este nivel?" 
    - level: "Member"
      description: "¿Qué define este nivel?" 
    - level: "Advocate"
      description: "¿Qué define este nivel?" 
    - level: "Creyente básico" 
      description: "¿Qué define este nivel?" 
  boundary:
    inclusion_criteria: "¿Qué hace que alguien sea de la misma manera?" 
    exclusion_triggers: ["{trigger1}", "{trigger2}"]
```

## Condiciones de veto

1. **Nunca construir identidad sin una chispa validada** - la identidad debe crecer de la experiencia compartida real
2. **Nunca crear identidad excluyente basada en la demografía** - los movimientos se unen alrededor de las creencias, no rasgos de nacimiento
3. **NUNCA rituales de diseño que requieren engaño** - la autenticidad es fundamental
4. **Nunca saltar el sistema de creencias** - los marcadores sin creencias son traje, no identidad
5. **Nunca crea hostil out-group enmarcando** -- definir "nosotros" positivamente, no "ellos" negativamente

## Criterios de finalización

- Sistema de creencias definido con convicción central y jerarquía
- [ ] Marcadores tribales diseñados en todas las categorías (idioma, visual, conductual, estado)
- Al menos 5 rituales creados que abarcan la iniciación a través de la celebración
Perteneciente a la gradiente definida con 5 niveles
- [ ] señales en grupo establecidas con mecánicos de reconocimiento
- [ ] Reglas de Frontera definidas (inclusión y exclusión)
- [ ] Coherencia de identidad validada contra el análisis de chispa
- [ ] La salida coincide con el esquema anterior
