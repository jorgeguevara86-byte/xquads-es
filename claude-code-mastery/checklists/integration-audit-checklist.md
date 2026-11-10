# Lista de verificación de la auditoría de integración

** ID de lista de verificación:**CCM-CL-005
**Referido por:** project-integrator
**Purpose:** Auditoría de la calidad de la integración existente en un proyecto del Código de Claude. Produce un grado marcado (A-F) para identificar lagunas y priorizar mejoras.

[[LLM: INITIALIZATION INSTRUCTIONS - INTEGRATION AUDIT

Esta lista de verificación evalúa lo bien que el Código Claude está integrado en un proyecto.
Úsalo para auditar las configuraciones existentes e identificar oportunidades de mejora.

ENFOQUE DE EJECUCIÓN:
1. Revisar cada artículo contra el estado del proyecto real
2. Marcos [x] para presente y correcto, [ ] para desaparecidos o incorrectos, [N/A] para no aplicable
3. Cuenta de artículos comprobados vs totales de los artículos aplicables
4. Calcular la puntuación y la rejilla
5. Priorizar las brechas por categoría (primera seguridad, luego estructura, luego optimización)

Esta auditoría es non-destructive -- sólo lee e informa.]]

---

## 1. Estructura del directorio

- [ ] `.claude/` directorio existe en raíz del proyecto
- [ ] `.claude/settings.json` está presente y válido JSON
- [ ] `.claude/rules/` directorio existe con al menos un archivo de regla
- [ ] `.claude/CLAUDE.md` exists
- [ ] `.claude/agents/` directorio existe (si proyecto utiliza agentes personalizados)
- [ ] `.claude/skills/` directorio existe (si el proyecto utiliza habilidades personalizadas)

## 2. Calidad de configuración

- [ ] Negar reglas existen para `.env` y patrones comunes de archivos secretos (CRITICAL)
- [ ] Negar reglas existen para `node_modules/`, `.git/objects`, y grandes directorios binarios
- [ ] El modo de permiso se establece en un nivel apropiado (no `auto` para los repos no confiados)
- [ ] Permitir que las reglas se alcancen de forma estrecha (no manta `*` pautas)
- [ ] Las opciones siguen el principio de menos privilegio
- [ ] Sobresueldos locales (`settings.local.json`- ¿Qué?

## 3. CLAUDE.md Health

- [ ] CLAUDE.md existe y no está vacío (CRITICAL)
- [ ] CLAUDE.md es inferior a 500 líneas (menos de 200 preferidas)
- [ ] No referencias de ruta de archivo de escalones (todas las rutas mencionadas resuelven a los archivos existentes)
- [ ] Las instrucciones son específicas para este proyecto (no caldera genérica)
- [ ] Las secciones manejadas (si están presentes) tienen coincidencia start/end marcadores
- No hay instrucciones contradictorias dentro del documento
- [ ] Los ejemplos de código son sintacticamente válidos y utilizan los patrones de proyecto actuales

## 4. Cobertura de gancho

- Al menos uno damage-control gancho existe (PreToolUse para comandos destructivos)
- [ ] ganchos han sido probados (no sólo escrito y nunca validados)
- [ ] Hook scripts manejan errores con gracia (sin excepciones sin manejar)
- Los ganchos tienen tiempo explícito para evitar el bloqueo
- [ ] PostToolUse ganchos no traga silenciosamente errores

## 5. Integración MCP

- [ ] Los servidores MCP están configurados en `.claude/mcp.json` o equivalente (si se utiliza el PCM)
- [ ] Los servidores configurados son accesibles y autenticados
- [ ] El presupuesto de texto para herramientas de PCM se documenta o se limita a límites razonables
- [ ] Se documenta la prioridad de selección de herramientas MCP (prefieren herramientas nativas)
- [ ] No servidores MCP redundantes (cada uno sirve un propósito distinto)

## 6. Reglas de cobertura

- [ ] Existen reglas basadas en el camino para los principales directorios de fuentes (src/, lib/, tests/)
- No hay reglas huérfanas (reglas que se refieren) non-existent patrones de archivos)
- Las reglas usan la primera `paths:` para path-scoped carga (no always-loaded)
Total always-loaded contenido de reglas se mantiene bajo 1000 líneas combinados
- [ ] Las reglas no duplican el contenido ya en CLAUDE.md
- [ ] Nombramiento de archivos de reglas sigue kebab-case convención

## 7. Definiciones de agentes

- Si. `.claude/agents/` existe, cada archivo agente tiene estructura válida
- [ ] Definiciones de agentes incluyen descripciones claras de su función y alcance
- [ ] El acceso de la herramienta del agente está restringido a lo que cada agente necesita
- [ ] Listas de comandos de agente referencia archivos de tareas válidos
- No hay instrucciones contradictorias entre las definiciones de agente

---

## Scoring

**Calculación:** (Comprobados) / (Total items - N/A ítems) x 100

Silencio Silencioso Silencioso puntuación Rango Silencioso
|-------|------------|----------------|
TEN A TENIDO 90-100% TENIDO Excelente integración, production-ready |
Silencio B Silencio 80-89% tención Buena integración, pequeñas mejoras necesarias
Silencio C Silencio 70-79% Silencio Integración adecuada, varias lagunas para abordar Silencio
Silencio D Silencio 60-69% Silencio Bajo promedio, importantes brechas presentes Silencio
Silencio F Silencio Bajo 60% Silencio Intección pobre, retrabajo importante necesario

## Priority Fix Order

1. **Artículos críticos** (denegación de la seguridad las reglas, CLAUDE.md existencia) - Arreglar inmediatamente
2. **Cobertura de gancho** - previene daños accidentales
3. **Cobertura de las reglas** - mejora la exactitud de los agentes
4. ** Calidad de configuración** - optimiza el rendimiento
5. **Definiciones de la asistencia** - mejora el flujo de trabajo del equipo
