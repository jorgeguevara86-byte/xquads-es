---
task: buildIdentity()
responsavel: "@alina-wheeler"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: positioning
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Sistema de Identidad de Marca" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Sistema de identidad visual definido (colores, tipografía, logo)" 
  - "[ ] Sistema de identidad verbal definido (voz, mensajería, historia)" 
  - "[ ] Resumen de pautas de marca compilado con ejemplos de aplicaciones" 
---

# Tarea: Crear identidad de marca

**ID de tarea:** MARCA-003
**Version:** 1.0.0
**Command:** `*build-identity`
**Agente:** Alina Wheeler (alina-wheeler) o Jean-Noel Kapferer (jean-noel-kapferer)
**Propósito:** Diseñar un sistema integral de identidad visual y verbal para la marca.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| marca | cadena | Mensaje de usuario | Sí | Nombre de la marca |
| posicionamiento | cadena | Mensaje de usuario | Sí | Declaración de posicionamiento (idealmente de create-positioning.md) |
| audiencia | cadena | Mensaje de usuario | Sí | Público objetivo con detalle psicográfico |
| industria | cadena | Mensaje de usuario | Sí | Contexto de la industria |
| brand_personality | lista | Mensaje de usuario | No | Rasgos de personalidad deseados (3-5) |
| existing_assets | lista | Mensaje de usuario | No | Logotipo, colores y fuentes actuales para conservar o reemplazar |
| arquetipo | cadena | Mensaje de usuario | No | Arquetipo de marca si ya está determinado |

---

## Preconditions

- Posicionamiento definido (lo que representa la marca)
- Público objetivo identificado con contexto emocional y aspiracional

---

## Fases de Ejecución

### Fase 1: Definición de Personalidad de Marca
1. Defina 5 rasgos de personalidad utilizando el espectro de personalidad de la marca:
   - Sinceridad: honesto, sano, alegre, down-to-earth
   - Emoción: atrevida, enérgica, imaginativa, up-to-date
   - Competencia: confiable, inteligente, exitoso, líder
   - Sofisticación: upper-class, encantador, elegante, premium
   - Robustez: outdoor, resistente, auténtico, no-nonsense
2. Para cada rasgo, defina cómo se ve en la práctica:
   - Cómo habla la marca (tono de voz)
   - Cómo se ve la marca (estilo visual)
   - Cómo se comporta la marca (experiencia del cliente)
3. Defina el anti-personality — lo que NO es la marca
4. Escriba una descripción de "marca como persona" (si la marca fuera una persona en una cena)

### Fase 2: Sistema de Identidad Visual
1. Defina el sistema de color:
   - Color primario: el color dominante de la marca (con valores hexadecimales, RGB y CMYK)
   - Colores secundarios: 2-3 colores complementarios
   - Colores neutros: fondos, texto y colores de UI
   - Justificación de la psicología del color para cada elección
2. Definir el sistema de tipografía:
   - Tipo de letra principal: para titulares y momentos de marca
   - Tipo de letra secundario: Para el cuerpo del texto y long-form
   - Opciones seguras para la Web
   - Reglas de uso (jerarquía de tallas, uso de peso)
3. Defina la dirección del logotipo:
   - Descripción del concepto del logotipo (lo que representa)
   - Se necesitan variaciones del logotipo (primario, secundario, icon-only, monocromático)
   - Borrar espacio y reglas de tamaño mínimo
   - Fondos en los que funciona el logo (y no)
4. Defina el estilo visual:
   - Estilo de fotografía (brillante, de mal humor, estilo de vida, producto, sincero)
   - Estilo de ilustración (si corresponde)
   - Estilo de iconografía
   - Principios de diseño y preferencias de cuadrícula

### Fase 3: Sistema de Identidad Verbal
1. Defina la voz de la marca:
   - Dimensiones de tono (formal/casual, serious/playful, respectful/irreverent, enthusiastic/matter-of-fact)
   - Voz sobre lo que se debe y no se debe hacer con ejemplos
   - Preferencias de vocabulario (palabras a usar, palabras a evitar)
2. Escriba marcos de mensajería clave:
   - Lema / eslogan
   - Promesa de marca (una frase)
   - Historia de la marca (narrativa del origen, 2-3 párrafos)
   - Declaración de misión
   - Declaración de visión
   - Propuestas de valor por segmento de audiencia
3. Cree una jerarquía de mensajería:
   - Nivel 1: Lo que siempre decimos (mensajes centrales)
   - Nivel 2: Lo que decimos cuando sea relevante (mensajes de apoyo)
   - Nivel 3: Lo que nunca decimos (off-limits temas)

### Fase 4: Resumen de directrices de marca
1. Compile el sistema de identidad en un documento de pautas estructurado.
2. Proporcione ejemplos de uso para aplicaciones comunes:
   - Tarjeta de presentación
   - Perfil de redes sociales
   - Firma de correo electrónico
   - Encabezado del sitio web
   - Plantilla de anuncio
3. Definir las reglas de gobernanza:
   - ¿Quién puede modificar los activos de la marca?
   - Proceso de aprobación de nuevas solicitudes
   - Cadencia de revisión anual

---

## Formato de salida

```markdown
## Brand Identity System: {Brand Name}

**Positioning:** {statement}
**Personality:** {5 traits}
**Archetype:** {archetype}

---

### Brand Personality

| Trait | Expression | Anti-Trait |
|-------|-----------|-----------|

**Brand as a Person:** {description}

### Visual Identity

#### Colors
| Role | Color | Hex | Psychology |
|------|-------|-----|-----------|
| Primary | {color} | #{hex} | {rationale} |

#### Typography
| Role | Typeface | Weight | Usage |
|------|---------|--------|-------|

#### Logo Direction
{Concept description with variation requirements}

#### Visual Style
{Photography, illustration, and layout direction}

### Verbal Identity

#### Brand Voice
| Dimension | Position | Example |
|-----------|----------|---------|

#### Key Messaging
- **Tagline:** {tagline}
- **Brand Promise:** {promise}
- **Mission:** {mission}
- **Vision:** {vision}

#### Brand Story
{2-3 paragraph origin narrative}

### Application Examples
{Description of how the identity applies to key touchpoints}

### Governance
{Who, what, when for brand management}
```

---

## Condiciones de veto

- NUNCA diseñes una identidad sin una base de posicionamiento: la identidad expresa posicionamiento
- NUNCA elija colores o fuentes basándose únicamente en sus preferencias personales; justifíquelo con una estrategia
- NUNCA definas la voz sin ejemplos: las descripciones abstractas no se pueden utilizar
- NUNCA cree un sistema de identidad demasiado complejo para ser aplicado consistentemente
- NUNCA te saltes el "anti-personality" — saber lo que NO eres es tan importante como lo que eres

---

## Criterios de finalización

- [ ] Personalidad de marca definida con 5 rasgos y anti-traits
- [ ] Sistema de color definido con fundamento
- [ ] Sistema de tipografía definido con reglas de uso
- [ ] Dirección del logotipo documentada con necesidades de variación
- [ ] Estilo visual definido (fotografía, ilustración, maquetación)
- [ ] Voz de marca definida con lo que se debe, lo que no se debe hacer y ejemplos
- [ ] Mensajes clave escritos (lema, promesa, historia, misión, visión)
- [ ] Ejemplos de aplicaciones proporcionados
- [ ] Reglas de gobernanza definidas
