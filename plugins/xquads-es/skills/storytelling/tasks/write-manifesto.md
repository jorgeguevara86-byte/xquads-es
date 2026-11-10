---
task: writeManifesto()
responsavel: "@marshall-ganz"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: movement_or_brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: core_values
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: manifesto
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Historia del Ser elaborado con auténtico origen personal" 
  - "[ ] Historia de Nosotros construye identidad compartida y pertenencia" 
  - "[ ] Texto del manifiesto tejido con el grito de rally" 
---

# Task: Movement/Brand Manifiesto

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*write-manifesto`
Marshall Ganz (Marshall Ganz)marshall-ganz)
**Purpose:** Crear un manifiesto poderoso usando el marco narrativo público (Story of Self, Us, Now).

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `movement_or_brand` Silencioso descripción de usuario Silencio Silencio
| `core_values` Silencio vocacional voca miento voca 
| `target_community` Silencio Quien es para vivir YES
| `urgency_trigger` Silencio, por qué ahora? Silencio preferenciado
| `founder_story` 
| `enemy_or_obstacle` Silencio Lo que el movimiento se opone a Silencio NO TENIDO

## Preconditions

1. El sentido claro de lo que el movimiento o la marca representa
2. Valores básicos articulados (incluso en forma aproximada)
3. Determinación de la comunidad de objetivos

## Fases de Ejecución

### Fase 1: Historia del Ser

1. Identificar el origen personal - ¿qué experiencia creó el compromiso?
2. Encontrar el punto de elección - el momento que cambió todo
3. Definir los valores expresados — ¿qué revela la elección acerca de quién eres?
4. Elabore la narración — hágalo específico, vivo y emocionalmente honesto
5. Conecte la historia personal a la experiencia humana universal
6. Prueba: ¿Responde esta historia "Por qué me importa?" de manera auténtica?

### Fase 2: Historia de nosotros

1. Identificar experiencias compartidas — ¿qué tiene esta comunidad en común?
2. Definir los valores compartidos — ¿qué cree este grupo juntos?
3. Encontrar el desafío colectivo - ¿qué obstáculo nos une?
4. Momentos de arte de "nosotros" — transformamos historias individuales en identidad comunal
5. Construir la pertenencia — hacer que el lector sienta que son parte de algo más grande
6. Prueba: ¿Responde esta historia "Por qué debemos importarnos?" con fuerza?

### Fase 3: Historia de Ahora

1. Definir el reto urgente - ¿qué exige la acción ahora mismo?
2. Arregla la elección - ¿qué debemos decidir, y cuáles son las apuestas?
3. Crear tensión entre esperanza y miedo - ¿qué sucede si actuamos vs si no lo hacemos?
4. Emitir la llamada a la acción —específica, factible, inmediata
5. Pintar el futuro — ¿cómo es el mundo cuando tenemos éxito?
6. Prueba: ¿Responde esta historia "Qué debemos hacer ahora?" con urgencia?

## Fase 4: Proyecto de Manifiesto

1. Tejemos las tres historias en un documento de manifiesto cohesivo
2. Abierto con una declaración audaz — la creencia fundamental declarada sin disculpas
3. Construir de personal a colectivo a urgente
4. Use frases cortas y puntiagudas — los manifiestos están destinados a ser hablados en voz alta
5. Incluir al enemigo o el obstáculo - lo que nos oponemos
6. Cierre con un grito de manifestación - la frase que la gente repetirá y compartirá
7. Examen del poder emocional: cada párrafo debe mover al lector
8. Reparación de pruebas: leer en voz alta, comprobar el ritmo y la cadencia

## Formato de salida

```yaml
manifesto:
  title: "{Título de Manifiesto}" 
  author_agent: "marshall-ganz"
  movement_or_brand: "{name}"
  core_values: ["{values}"]
  target_community: "{audience}"
  story_of_self:
    origin: "{historia personal}" 
    choice_point: "{el momento}" 
    values_expressed: ["{valores revelados}" ]
  story_of_us:
    shared_experience: "¿Qué nos une?" 
    shared_values: ["{convenencias colectivas}" ]
    collective_challenge: "{nuestro obstáculo}" 
  story_of_now:
    urgent_challenge: "¿Por qué ahora?" 
    the_choice: "¿Qué debemos decidir?" 
    call_to_action: "{acción específica}" 
    future_vision: "{el mundo que creamos}" 
  manifesto_text: "{El texto completo del manifiesto}"
  rallying_cry: "{La única frase que la gente repetirá}" 
```

## Condiciones de veto

- ###############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
- ** NUNCA** emite una llamada a la acción sin definir cómo es el éxito
- ** NUNCA** crear división a través del odio - opuesta ideas, no personas
- ** NUNCA** escribe un manifiesto que no se podía leer en voz alta con convicción

## Criterios de finalización

Historia de Sí Mismo elaborada con auténtico origen personal
La historia de nosotros construye identidad compartida y pertenencia
La historia de ahora crea urgencia y define la elección
- [ ] Las tres historias tejidas en manifiesto cohesivo
- Declaración de apertura Bold establecida
- [ ] Llamamiento claro a la acción con pasos específicos
- [ ] Clad de rallye elaborado para la memorabilidad
El manifiesto lee poderosamente cuando se habla en voz alta
