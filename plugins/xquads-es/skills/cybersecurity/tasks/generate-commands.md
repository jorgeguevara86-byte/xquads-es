---
task: generateCommands()
responsavel: "@command-generator"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: objective
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: target
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: command_output
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Herramienta apropiada seleccionada con razonamiento" 
  - "[ ] Comando generado con documentación en línea" 
  - "[ ] Evaluación de seguridad completada con advertencias" 
---

# Task: Security Tool Command Generation

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*generate-commands`
**Agente:** Generador de Mando (command-generator)
**Purpose:** Generar precisa, segura y context-appropriate comandos de herramientas de seguridad para operaciones autorizadas.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `objective` Silencio Silencio Silencio Silencio Silencio Silencio
| `target` Silencio vocacional voca miento voca 
| `tool_preference` TENCIÓN Usuario o auto-select Silencio
| `authorization_context` Silencio Silencio Silencio Silencio Silencio Silencio
| `constraints` Silencio Índice límites, robo, tiempo TENIDO NO TENIDO
| `os_context` TENIDO OS/environment Silencio preFERIDO Silencio

## Preconditions

1. La operación está autorizada (CTF, compromiso de protestas, educación, defensa)
2. La meta está dentro del ámbito autorizado
3. Disponibilidad de herramientas confirmada o instalable
4. El objetivo está claramente definido (recon, enum, vuln scan, exploit, defense)

## Fases de Ejecución

### Fase 1: Identificar el objetivo

1. Parse el objetivo del usuario - ¿Qué están tratando de lograr?
2. Clasificación del tipo de operación: reconocimiento, enumeración, exploración de vulnerabilidad, explotación, defensa
3. Identificar las características de destino: IP, dominio, aplicación web, rango de red, servicio
4. Determinación OS/environment context for command compatibility
5. Confirmación del contexto de autorización - rechazo si está claramente no autorizado

### Fase 2: Seleccione la herramienta apropiada

1. Objetivo de coincidencia con la categoría de herramientas de security-tools-catalog.yaml
2. Considerar la disponibilidad de herramientas y la preferencia de los usuarios
3. Si se ajustan múltiples herramientas, recomiendo lo más apropiado con el razonamiento:
   - Cambio de velocidad vs.
   - Cambio de ruido de Stealth vs
   - Requisitos de alcance (objetivo único vs rango)
4. Seleccione la plantilla de comandos del catálogo

## Fase 3: Generar Comando

1. Construir el comando con banderas y opciones apropiadas
2. Personalizar el objetivo y el objetivo específicos
3. Agregue banderas de formato de salida (protegido por salida)
4. Incluir el tiempo libre y rate-limiting banderas cuando proceda
5. Proporcione el comando con comentarios en línea que explican cada bandera
6. Si es complejo, entra en una secuencia de comandos con explicaciones

## Fase 4: Vigilancia de la seguridad

1. **Comprobación de la solución** - ¿El comando sólo afecta al objetivo autorizado?
2. ** Verificación de la destructividad** — ¿Podría este comando causar trastorno del servicio?
3. **Noise check** — ¿Cómo detectable es este comando? Bandera si se requiere el robo
4. **Manejo de datos** - ¿El comando store/transmit ¿Datos sensibles de forma segura?
5. **Comprobación legal** - ¿Es apropiado este comando para el contexto de autorización?
6. Agregue advertencias para cualquier bandera o comportamientos riesgosos
7. Sugerir alternativas más seguras si la solicitud original es de línea fronteriza

## Formato de salida

```yaml
command_output:
  objective: "Lo que el comando logra" 
  tool: "{nombre de la tablilla}" 
  category: "reconozco vuln_scan" 
  authorization: "confirmed — {context}"
  command: "{lleno comando with comments}"
  explanation:
    - flag: "{flag}"
      purpose: "¿Qué hace?" 
  safety_assessment:
    scope_safe: true
    destructive: false
    noise_level: "BAJO | MEDIANO | ALTA" 
    warnings: ["{Cualquier advertencia}" ]
  alternatives:
    - tool: "{herramienta alternativa}" 
      command: "{ comando alternativo}" 
      tradeoff: "¿Por qué prefieres esto?" 
```

## Condiciones de veto

- ** NUNCA** generan comandos para objetivos no autorizados
- ** NUNCA** generan comandos destructivos (DoS, limpiaparabrisas, eliminación de datos) sin salvaguardias explícitas
- ** NUNCA** generan comandos diseñados para evadir la aplicación de la ley
- ** NUNCA** omitir advertencias de seguridad para comandos potencialmente peligrosos
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### mass-targeting comandos sin verificación de alcance

## Criterios de finalización

Objetivo y objetivo claramente identificados
- [ ] Herramienta apropiada seleccionada con razonamiento
- [ ] Comando generado con documentación en línea
- Cada bandera explicada
- [ ] Evaluación de seguridad completada
- Advertencias incluidas para operaciones de riesgo
- [ ] Enfoques alternativos propuestos cuando proceda
