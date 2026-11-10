---
task: writeManifesto()
responsavel: "@manifestador"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: identity_architecture
    tipo: string
    origem: "Resultado de la fase 2" 
    obrigatorio: true
  - campo: cause
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: manifesto
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Manifiesto incluye los 7 componentes" 
  - "Enemigo llamado fuerza sistémica, no persona" 
  - "[ ] La llamada a la acción incluye el primer paso concreto" 
---

# Task: Write Manifesto

** ID de la lista:** MOVIMIENTO-004
**Version:** 1.0.0
**Command:** `*write-manifesto`
**Agente:** Manifestor (manifestrador)
**Purpose:** Crear un manifiesto de movimiento poderoso que declara creencias, nombre al enemigo y llama a la gente a la acción

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `identity_architecture` TEN Fase 2 salida TENIDO Sí TENIDO Marco completo de identidad de identitario TEN
| `spark_analysis` Silencio Fase 1 salida Silencio Sí Silencio Análisis fenomenológico con el núcleo narrativo TEN
| `cause` Silencio invocar a un usuario Silencio Silencio La causa del movimiento Silencio
| `tone` Silencio Usuario Silencio No Silencio Desired tone: revolucionario, inspirador, urgente, poético TEN
| `length` TENIDO Usuario TENIDO No TENIDO Duración del objetivo: corto (500w), estándar (1000w), épico (2000w) ANTE

## Preconditions

- Arquitectura de identidad completada (MOVEMENT-003)
- Análisis de chispa disponible con núcleo narrativo
- Sistema de creencias definido con convicción central
- Marcos de movimiento cargados (`data/movement-frameworks.yaml`)

## Fases de Ejecución

## Fase 1: Declare Reality

1. Abra con el **undeniable verdad** - una declaración sobre el mundo que el público reconoce inmediatamente
2. Describa el **current estado** en términos vivos, emocionales
3. Nombre del **pain** que la gente siente pero raramente articular
4. Utilice el núcleo narrativo del análisis de chispa como base
5. Escribe 2-3 párrafos que hacen que el lector piense "alguien finalmente lo dijo"

### Fase 2: Creencias del Estado

1. Declarar "Creemos..." declaraciones extraídas de la arquitectura de identidad
2. Liderazgo con el **central convicción** - la creencia más fuerte
3. Construir un **crescendo** de creencias -- cada una más ambiciosa que la última
4. Incluir el **contrarian creencia** - lo que creemos que otros no
5. Sección de creencias finales con el **aspirational creencia** - el sueño
6. Escribir declaraciones de creencias 3-7, cada uno de sus propios párrafos

### Fase 3: Nombre al enemigo

1. Identificar el **systemic enemigo** -- una fuerza, un sistema o una mentalidad (nunca una persona)
2. Articulado **why este enemigo persiste** - lo que lo mantiene en el poder
3. Describa el **cost de inacción** - qué sucede si nada cambia
4. Enmarcar al enemigo como **defeatable** -- poderoso pero no invencible
5. Usar lenguaje que se une contra el enemigo sin promover el odio

### Fase 4: Envision the Future

1. Pintar el **promised tierra** - cómo es el mundo cuando el movimiento tiene éxito
2. Que sea **specific y sensorial** - el lector debe ver, sentir y escucharlo
3. Conectar el futuro a **individual transformación** - cómo cambia la vida de cada persona
4. Conectarse a **collective impacto** - cómo el community/world cambios
5. Puente de sueño a posibilidad - "Esto no es sólo un sueño, está a su alcance"

## Fase 5: Llamar a la Acción

1. Cambio de visión a **invitation################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
2. Definir el **first paso** - una acción concreta que cualquiera puede tomar hoy
3. Establecer el **commitment** -- lo que significa ser parte de esto
4. Cerrar con el **battle llanto** - una frase que captura todo
5. Terminar con una línea que hace eco en la mente del lector

## Formato de salida

```yaml
manifesto:
  title: "{Título de Manifiesto}" 
  movement: "{Nombre de movimiento}" 
  word_count: {number}
  tone: "{Revolutionary sometidainspirational someurgent somepoetic}" 
  components:
    reality_declaration: "{abrir la verdad}" 
    belief_count: {number}
    central_belief: "{}}}} {}}" 
    named_enemy: "{Enemigo sistémico}" 
    promised_land: "{Resumen de la visión de futuro}" 
    battle_cry: "{una frase}" 
    call_to_action: "{primer paso}" 
  full_text: "{completo texto manifiesto}"
  usage_guidelines:
    - "{donde y cómo utilizar este manifiesto}" 
    - "{Directrices de adaptación para diferentes formatos}" 
```

## Condiciones de veto

1. **NUNCA nombre una persona o grupo específico como el enemigo** - enemigos deben ser fuerzas sistémicas o mentalidades
2. **Nunca escriba creencias que contradicen la arquitectura de identidad** - el manifiesto expresa identidad, no la inventa
3. **Nunca usen lenguaje odioso, discriminatorio o deshumanizador** - los movimientos inspiran, no destruyen
4. **Nunca saltar la llamada a la acción** - un manifiesto sin acción es un ensayo
5. **Nunca producir genérico, platitude-filled texto** - Cada frase debe llevar peso y especificidad

## Criterios de finalización

- La declaración de la realidad se abre con la verdad innegable
Al menos 3 declaraciones de creencias arraigadas en la arquitectura de identidad
Enemigo llamado fuerza sistémica (no persona o grupo)
- La visión futura es específica y sensorial
- [ ] La llamada a la acción incluye un primer paso concreto
El grito de batalla es una frase memorable
El manifiesto dice que es un documento cohesivo e emocionalmente convincente.
- [ ] Palabra cuenta dentro del rango de destino
- [ ] La salida coincide con el esquema anterior
