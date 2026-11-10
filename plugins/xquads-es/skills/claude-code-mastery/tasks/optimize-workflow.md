# Task: Optimize Claude Code Workflow

** ID de la lista:** CCM-PI-003
**Version:** 1.0.0
**Command:** `*optimize-workflow`
**Agente:**Conduit (project-integrator)
**Purpose:** Optimize Claude Code workflow for maximum productivity by analyzing usage patterns, identifying bottlenecks, and configuring permissions, shortcuts, and automatización.

---

## Overview

```
  Configuración actual
       |
       v
  +---------------------+
  Silencio 1. Analizar el uso Silencioso
  |    Patterns          |
  +---------------------+
       |
       v
  +---------------------+
  | 2. Identify          |
  |    Bottlenecks       |
  +---------------------+
       |
       v
  +---------------------+
  | 3. Optimize          |
  |    Permissions       |
  +---------------------+
       |
       v
  +---------------------+
  Silencio 4. Configurar el teclado Silencio
  |    Shortcuts         |
  +---------------------+
       |
       v
  +---------------------+
  | 5. Configure         |
  TENER Auto-Memory TENIDO
  +---------------------+
       |
       v
  +---------------------+
  | 6. Generate          |
  Silencioso Plan de Optimización
  +---------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_path Silencio Silencio Silencio Silencio Usuario o cwd Silencio Sí Silencio Debe contener .claude/ directorio Silencio
| pain_points TENEDAJE[] TENIDO Usuario TENIDO No TENIDO Bloqueos descritos (por ejemplo, "demasiados avisos de permiso") TENIDO
| workflow_type Silencio en el futuro Usuario Silencio No Silencio `solo-dev`, `team-review`, `ci-cd`, `exploratory` |

---

## Preconditions

- La integración del Código de Claude existe (.claude/ directorio presente)
- El usuario ha utilizado el Código Claude en este proyecto al menos una vez

---

## Fases de Ejecución

### Fase 1: Analizar patrones de uso

Examinar la configuración actual para inferir patrones de uso:

1. **CLAUDE.md análisis**: qué instrucciones están presentes, qué falta
2. **settings.json review**: current allow/deny reglas, cuán restrictivas
3. **Inventario de reglas**: cuántas reglas, qué dominios cubren
4. **Presentación de gancho**: qué automatización existe
5. **Command/skill inventario**: comandos y habilidades personalizadas definidas
6. ** Estimación del tamaño de proyecto**: recuento de archivos, distribución de idiomas

Clasifique la madurez de configuración actual:
TENIDO Nivel TENIDO Descripción TENIDO Signos Típicos TENIDO
|-------|-------------|---------------|
Silencioso Principio Silencio Minimal configuración Silencio Única CLAUDE.md, sin reglas, sin ganchos ANTERIENTE
Silencio Intermedio Silencio Funcional Silencio CLAUDE.md + configuración + algunas reglas Silencio
← Avanzadas Silencio Optimizado Silencio Reglas completas, ganchos, habilidades, MCP configurado TEN
Silencio Expert TEN TENIDO Totalmente automatizado TEN CI/CD integración, ganchos personalizados, equipos de agente TEN

### Fase 2: Identificar cuellos de botella

Compruebe si los asesinos de productividad comunes:

1. **Insinuaciones de la misión**: ajustes excesivamente restrictivos para la aprobación reiterada
   - Busque falta permite reglas para comandos comunes (npm, git, herramientas de construcción)
   - ¿Comprobaste si `Bash` herramienta no tiene permisos (causas rápida en cada comando)
2. ** Ejecución de la herramienta lenta**: servidores MCP con alta latencia, caching perdido
3. **Context bloat**: CLAUDE.md más de 150 líneas, demasiados always-loaded Normas
4. **Automatización de la minería**: tareas repetitivas que podrían ser ganchos o habilidades
5. **Context rot**: sesiones largas sin estrategia de compactación
6. ** Instrucciones de secretaría**: orientación duplicada CLAUDE.md y normas

Para cada embotellado encontrado, estimación de impacto: ALTO, MEDIO, LOW.

### Phase 3: Optimize Permission Strategy

Diseña una estrategia de permiso que equilibra la seguridad y la velocidad:

1. ** La salvación permite** (adición a settings.json permitir la lista:
   - Construir comandos: `npm run build`, `npm run dev`, `npm test`
   - Lint ordena: `npm run lint`, `npm run typecheck`
   - Diga órdenes: `git status`, `git diff`, `git log`
   - Servidores y formateadores de idiomas
2. ** El inteligente niega** (guarde o agregue a la lista de denegación):
   - Comandos destructivos: `rm -rf`, `DROP`, `git push --force`
   - Acceso a la producción: URLs de bases de datos, comandos de implementación
   - Senderos sensibles: `.env`, credenciales, secretos
3. **Contextual permissions**: use path-based reglas para directory-specific permite

Presente before/after comparación de los avisos de permisos previstos.

### Fase 4: Configurar los atajos del teclado

Recomendar configuración de teclado para el flujo de trabajo del usuario:

1. **Atajos esenciales** (todos los flujos de trabajo):
   - Escapar rápido: cancelar la operación actual
   - Aceptar la sugerencia: fast-approve uso de herramientas
   - Contexto compacto: compactación manual de disparador
2. **Atajos de desarrollo**:
   - Ejecute pruebas: one-key Ejecución de pruebas
   - Composición rápida: etapa + flujo de compromiso
   - Agente de reversa: cambiar entre modos de agente
3. **Atajos de revisión**:
   - Siguiente archivo: navegar archivos cambiados
   - Approve/reject: acciones de revisión rápida

Proveer tiradores de configuración para el código VS keybindings.json si es aplicable.

## Fase 5: Configure Auto-Memory

Configurar la memoria persistente para cross-session eficiencia:

1. **Recuerdo urgente**: crear `.claude/agent-memory/` estructura
   - MEMORY.md para session-persistent patrones
   - Archivos temáticos para conocimiento de dominio
2. ** Reglas de higiene de memoria**:
   - Qué guardar: patrones confirmados, preferencias de usuario, soluciones de depuración
   - Lo que NO salvar: session-specific conclusiones especulativas, estatales
   - Límites de tamaño: MEMORY.md de 200 líneas
3. **Papeles de memoria**: pre-populate con convenios de proyectos si se detecta

## Fase 6: Generar Plan de Optimización

Elaborar un plan de optimización priorizado:

1. Ordenar todas las recomendaciones por impacto (PRESIDENCIA primera)
2. Grupo por esfuerzo: Ganancias rápidas (traducido 5 min), Media (5-30 min), Inversión (30+ min)
3. Para cada recomendación, proporcionar medidas de aplicación exactas
4. Tiempo total estimado ahorrado por semana después de la optimización

---

## Formato de salida

```markdown
## Workflow Optimization Report

**Project:** {project_path}
**Current Maturity:** {level}
**Estimated Improvement:** {X}% fewer interruptions

### Bottlenecks Found

| Bottleneck | Impact | Fix Effort |
|------------|--------|------------|
| {description} | HIGH/MED/LOW | Quick/Medium/Investment |

### Quick Wins (Apply Now)

1. **{title}**: {description}
   ```json
   // Cambio de configuración de salida
   ```

### Medium Effort

1. **{title}**: {description}
   - Step 1: ...
   - Step 2: ...

### Investment Items

1. **{title}**: {description}
   - Tiempo estimado: {X} minutos
   - Prestaciones esperadas: {description}

Optimización de la autorización

*Antes* {N} plazos previstos por período de sesiones
**Después de:** {M} plazos previstos por período de sesiones
**Reduction:** {X}%
```

---

## Condiciones de veto

- ** NUNCA** añadir reglas para operaciones destructivas para reducir los impulsos
- **Nunca** ganchos de seguridad deshabilitados para conveniencia
- ** NUNCA** eliminar las reglas de negar sin explicar el desvío de seguridad
- ** NUNCA** hacer cambios sin presentar el plan primero - esta tarea produce un plan, el usuario lo aplica

---

## Criterios de finalización

- [ ] Patrones de uso analizados y nivel de madurez clasificado
- Bottlenecks identificados con evaluación de impacto
- [ ] Estrategia de permiso diseñado con before/after comparación
- [ ] Atajos de teclado recomendados para el tipo de flujo de trabajo
- [ ] Configuración de memoria sugerida
- Plan de optimización priorizado entregado
