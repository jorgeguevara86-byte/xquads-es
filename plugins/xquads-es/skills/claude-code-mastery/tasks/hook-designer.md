# Task: Diseño de ganchos personalizados

** ID de la lista:** CCM-PI-006
**Version:** 1.0.0
**Command:** `*hook-designer`
**Agente:**Conduit (project-integrator)
**Purpose:** Diseño personalizado Claude Code ganchos para un proyecto identificando necesidades de automatización, eligiendo tipos y eventos apropiados de ganchos, diseñando lógica de ganchos y produciendo implementation-ready especificaciones.

---

## Overview

```
  Necesidades de automatización
       |
       v
  +---------------------+
  Silencio 1. Identificar el gancho tóxico
  |    Needs             |
  +---------------------+
       |
       v
  +---------------------+
  Silencio 2. Elija el tipo de gancho Silencio
  |    & Category        |
  +---------------------+
       |
       v
  +---------------------+
  Silencio 3. Seleccione eventos Silencio
  +---------------------+
       |
       v
  +---------------------+
  Silencio 4. Diseño Hook Logic Silencio
  +---------------------+
       |
       v
  +---------------------+
  Silencioso 5. Implementar &quot; Test Silencioso
  +---------------------+
       |
       v
  +---------------------+
  | 6. Integration       |
  |    Verification      |
  +---------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| hook_purpose TENEDA TENIDO TENIDO Usuario TENIDO Sí TENIDO Descripción de lo que el gancho debe automatizar TENIDO
| trigger_event TENEDA TENIDO TENIDO Usuario TENIDO No TENIDO Evento específico si se conoce (por ejemplo, "PreToolUse", "Stop") TENIDO
| project_path Silencio Silencio Silencio Usuario o cwd Silencio Sí Silencio Directorio de proyectos para contexto TEN

---

## Preconditions

- Código Claude instalado y funcional
- Comprensión del flujo de trabajo y de los puntos de dolor del proyecto
- `.claude/` directorio existe (o se creará)

---

## Fases de Ejecución

### Fase 1: Identifique las necesidades de gancho

Analizar la automatización solicitada contra las capacidades de gancho:

1. **Categorizar la necesidad**:
   - Seguridad: bloqueo de comandos peligrosos, validación de entradas
   - Automatización: auto-formatting, auto-logging, administración estatal
   - Calidad: revestimiento en caja, prueba de compromiso, revisión completa
   - Observabilidad: tiempo, seguimiento de tokens, monitoreo de costos
   - Gestión del contexto: compactación, actualizaciones de memoria, persistencia del estado

2. **Validato hook-suitability**: algunas necesidades se atienden mejor por:
   - Skills/commands (user-triggered, not event-triggered)
   - Reglas (instrumentos estáticos, no lógica de tiempo de ejecución)
   - CI/CD (post-merge, no durante el período de sesiones)

Si la necesidad no es hook-suitable, recomendar la alternativa adecuada.

### Fase 2: Elija el tipo de gancho y la categoría

Los ganchos de Código de Claude operan en dos modos de transporte:

Silencio transporte Silencio Idioma Silencio Mejor para Silencio Constraint Silencio
|-----------|----------|----------|------------|
Silencio comando Silencio Any (bash, node, python) Silencio Operaciones de archivo, llamadas de API, lógica compleja Silencio Debe salir dentro del tiempoout Silencio
Silencio pronto Silencio N/A (retorno texto) Silencio Inyectar contexto en conversación TENIDO Agregado al contexto asistente TEN

** Categorías de gancho por evento:**

← Evento Silencioso Cuando Fuegos Silenciosos Usos comunes Silencio
|-------|-----------|-------------|
TENCIÓN PreToolUse TENED Antes de cualquier llamada de herramienta TEN Bloque comandos peligrosos, validar entradas TEN
← PostToolUse Silencio Después de completar la herramienta Silencio Resultados de sesión, capturar métricas, disparador follow-ups |
Silencio Stop Silencio sesión termina normalmente Silencio Guardar estado, generar resumen, actualizar la memoria TEN
← SubagentStop Silencio Subagent completes tención Reunir resultados, fusionar salidas Silencio
Silencio PreCompact Silencio Antes de la compactación del contexto Silencio Preserve crítica state ←
TEN Notification TENIDO El usuario recibe notificación TEN AUTOR AUTOR AUTOR AUTORIZADO TEN
Ø Ø UsuarioPromptSubmit Silencio Usuario envía mensaje ← Preprocesamiento de entrada, enrutamiento Silencio

Seleccione el evento apropiado basado en cuando la automatización debe desencadenar.

### Fase 3: Seleccionar eventos apropiados

Para la necesidad identificada, determinar:

1. **Efecto primario**: el principal desencadenante del gancho
2. ** Condiciones de la guardia**: cuando el gancho debe disparar vs skip
   - Filtro de nombre de la herramienta (para PreToolUse/PostToolUse)
   - Verificación del estado de sesión
   - Pauta de archivo que coincide
3. **Tiempo**: tiempo máximo de ejecución (predeterminado 10s para ganchos de comando)
4. **Comportamiento de emergencia**: qué sucede si el gancho falla
   - `continue`: Procedimientos del período de sesiones (recomendados para non-critical ganchos)
   - `stop`: sesión detiene (utilización solamente para security-critical ganchos)

### Fase 4: Diseño de gancho Logic

Diseñar la implementación de gancho:

1. ** Contrato de entrada**: qué datos recibe el gancho del Código de Claude
   ```json
   {
     "tool_name": "Bash",
     "tool_input": { "command": "rm -rf /tmp/test" },
     "session_id": "abc123"
   }
   ```

2. **Procesamiento de la lógica**: lo que el gancho hace con la entrada
   - Datos de entrada de pares
   - Aplicar lógica empresarial (validación, transformación, taladro)
   - Producción (producto)block/allow, entrada de registro, inyección de contexto)

3. ** Contrato de salida**: lo que el gancho devuelve
   - Para PreToolUse: `{ "decision": "allow" }` o `{ "decision": "block", "reason": "..." }`
   - Para ganchos rápidos: texto plano para inyectar en conversación
   - Para ganchos de comando: código de salida 0 (éxito) o non-zero (Failure)

4. **Requisitos de desempeño**:
   - El gancho debe completarse dentro del tiempo de salida
   - No hay bloqueo I/O sin tiempo fuera
   - Degradación grata por el fracaso

5. ** Gestión de los Estados** (si es necesario):
   - Dónde almacenar estado (archivo, variable ambiente)
   - Formato de Estado (JSON, YAML)
   - Consideraciones de coincidencia

### Fase 5: Implementación y Prueba

Crear la implementación de gancho:

1. **Escribe el script gancho** siguiendo la lógica diseñada
   - Usar el idioma más adecuado para la tarea (Node.js para JSON, Bash para comandos simples)
   - Incluir el manejo de errores y la protección de tiempo
   - Agregar comentarios en línea explicando la lógica

2. **Inscribir el gancho** en settings.json:
   ```json
   {
     "hooks": {
       "{EventName}": [
         {
           "type": "command",
           "command": "node .claude/hooks/{hook-name}.js",
           "timeout": 10000
         }
       ]
     }
   }
   ```

3. **Prueba el gancho**:
   - Detonador manual con entrada de muestra
   - Casos de borde: campos desaparecidos, entrada malformada, simulación de tiempo
   - Verificar código de salida y formato de salida

### Fase 6: Verificación de la Integración

Verificar el gancho funciona dentro de la sesión completa del Código de Claude:

1. Iniciar una sesión del Código de Claude
2. Trigger el evento que dispara el gancho
3. Verificar el gancho ejecutado (ver registros, salida o comportamiento)
4. Confirme no interferencia con otros ganchos o flujo de trabajo normal
5. Rendimiento de comprobación: gancho completa bien dentro del tiempo de salida

---

## Formato de salida

```markdown
## Hook Design Specification

**Purpose:** {hook_purpose}
**Event:** {event_name}
**Type:** {command|prompt}
**Language:** {node|bash|python}

### Design

**Trigger:** {when the hook fires}
**Guard:** {conditions to skip execution}
**Timeout:** {N}ms

### Input/Output Contract

**Input:**
```json
{input_schema}
```

**Output:**
```json
{output_schema}
```

### Implementation

**File:** `.claude/hooks/{hook-name}.js`
**Registration:**
```json
{settings_json_snippet}
```

*Plan de prueba*

Silencioso Escenario Silencioso Entrada Silencio esperada Salida
|----------|-------|-----------------|
Silencio Caso normal Silencio {input} | {output} |
TEN ANTERIOR Caso Edge ANTE {input} | {output} |
 {input} | {output} |

### Performance

- Tiempo de ejecución previsto: {N}ms
- Timeout configurado: {N}ms
- Modo de fracaso: {continue sometimiento}
```

---

## Condiciones de veto

- ** NUNCA** ganchos de diseño que bloquean todo el uso de herramientas sin escotilla de escape
- ** NUNCA** ganchos de diseño que envían datos a servicios externos sin consentimiento del usuario
- ** NUNCA** fije el tiempo de gancho por encima de 30 segundos (causas de sesión)
- Nunca uso `stop` comportamiento de error para non-security ganchos
- ** NUNCA** ganchos de diseño que modifican código fuente - ganchos observan y cierran, no autorizan

---

## Criterios de finalización

- [ ] Hecho necesidad identificado y validado como hook-suitable
- [ ] Tipo de gancho y evento seleccionado con racional
- [ ] Input/output contrato definido
- [ ] Lógica de gancho diseñado con manejo de errores
- [ ] Aplicación creada y registrada en settings.json
- [ ] Plan de prueba documentado con al menos 3 escenarios
- [ ] Integración verificada en una sesión real
