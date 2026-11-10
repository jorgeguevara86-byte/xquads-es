# Context Rot Checklist

** ID de lista de verificación:** CCM-CL-007
**Referido por:** project-integrator
**Purpose:** Detectar las referencias de estarilidad, hinchazón y obsoleto en CLAUDE.md Produce un marcador de puntaje (0-100, inferior = más rot) para cuantificar la salud del contexto y priorizar la limpieza.

[[LLM: INITIALIZATION INSTRUCTIONS - CONTEXT ROT DETECTION

Contexto de la podredumbre ocurre cuando CLAUDE.md, reglas y archivos de memoria acumuladas
referencias de establo, instrucciones obsoletas y contenido redundante con el tiempo.
Este degrada la exactitud de los agentes y el presupuesto contextual de los desechos.

ENFOQUE DE EJECUCIÓN:
1. Medida CLAUDE.md tamaño frente a los límites presupuestarios
2. Validar cada ruta de archivo y referencia mencionada en los archivos de contexto
3. Revisar instrucciones contra la realidad actual de la base de código
4. Verificar reglas coinciden con la estructura actual del directorio
5. Archivos de memoria de auditoría para la pertinencia
6. Comprobación de la redundancia en todas las fuentes de contexto
7. Calcular la puntuación de la raíz de los resultados

Contexto de la podredumbre es gradual e invisible hasta que el comportamiento del agente se degrada.
Las auditorías periódicas impiden la acumulación.]]

---

## 1. Verificación de tamaño

- [ ] CLAUDE.md es menor de 200 líneas (para auto-memory proyectos)
- [ ] CLAUDE.md es inferior a 500 líneas totales (máximo absoluto)
- Ningún archivo de reglas excede 200 líneas
Total always-loaded contenido de reglas es bajo 1000 líneas combinados
- [ ] No hay bloques de código innecesarios o ejemplos de verbose (podrían estar en reglas en su lugar)
- [ ] Las secciones administradas son concisas (las tablas preferidas sobre prosa)

## 2. Validez de referencia

- [ ] Todas las rutas de archivo mencionadas en CLAUDE.md resolución a los archivos existentes (CRITICAL)
- [ ] Todos los directorios mencionados en CLAUDE.md resolver a los directorios existentes
- [ ] Todos los ejemplos de comandos referencia scripts válidos o binarios
Todos los nombres de los agentes mencionados CLAUDE.md coinciden las definiciones de agente reales
- [ ] Todas las referencias de la lista de verificación resuelven los archivos de la lista de verificación existentes
- [ ] Todas las referencias de tareas resuelven los archivos de tareas existentes
- [ ] URLs y enlaces (si hay) son accesibles y actuales

## 3. Moneda de instrucciones

- [ ] No hace referencias a APIs o bibliotecas deprecatadas (CRITICAL)
- [ ] No hay referencias a archivos eliminados o renombrados
- [ ] Sintaxis de comandos coincide con las versiones actuales de herramientas (por ejemplo, banderas CLI todavía válidas)
- [ ] Referencias de la versión marco son actuales
- [ ] descripciones del flujo de trabajo coinciden con el comportamiento implementado real
- [ ] Instrucciones de prueba usan el corredor de pruebas actual y patrones
- [ ] Construir comandos coinciden con la corriente package.json scripts

## 4. Salud de la Regla

- Regla `paths:` frontmatter coincide con la estructura actual del directorio (CRITICAL)
No hay patrones de archivo de referencia de reglas que ya no existen en el proyecto
- [ ] El contenido de reglas se ajusta a las normas de codificación actuales
- [ ] Reglas de seguimiento correctamente alcance a sus archivos previstos
- [ ] Ninguna regla ha sido tocada por más de 90 días en un proyecto activo
- [ ] Las reglas no hacen referencia a agentes eliminados o flujos de trabajo deprecatados

## 5. Memory Hygiene

Archivos de memoria automática (MEMORY.md, memoria de agente) contiene contenido relevante
- No hay entradas para el trabajo terminado o abandonado
- [ ] Las entradas de memoria están organizadas por tema (no por vertederos cronológicos)
- No hay entradas de memoria contradicen la corriente CLAUDE.md instrucciones
- [ ] Los tamaños de los archivos de memoria están dentro de los límites (MEMORY.md menos de 200 líneas)
Notas temporales (session-specific) han sido limpiados

## 6. Redundancy Check

No hay instrucciones duplicadas entre CLAUDE.md y reglas de archivos (CRITICAL)
No hay instrucciones duplicadas entre CLAUDE.md y definiciones de agentes
- No hay instrucciones duplicadas entre diferentes archivos de reglas
- [ ] Los patrones comunes se definen una vez y se refieren (no copiado)
- [ ] Si la misma instrucción aparece en múltiples lugares, consolide a una fuente
- [ ] Ajustes en settings.json no re-stated como prose en CLAUDE.md

---

## Rot Score Calculation

Para cada categoría, cuente los elementos fallidos (excluyendo N/A). Aplicar pesos:

Silencioso Silencioso Silencio Silencio Silencio
|----------|--------|---------------|
Silencioso Tamaño Check Silencio 1x per fail Silencio 10 puntos Silencio
Silencioso Referencia Validez Silencio 3x por defecto Silencio 21 puntos Silencio
Silencio instrucción Moneda Silencio 2x por fall Silencio 14 puntos Silencio
Silencio Regla Salud Silencio 2x por defecto Silencio 12 puntos Silencio
Silencioso de la memoria Higiene Silencio 1x por fall Silencio 6 puntos Silencio
Silencio Redundancia Check Silencio 2x per fail Silencio 12 puntos Silencio

**Punto de remate** = 100 - (deducciones totales, capped at 100)

Silencioso puntuación Range Silencio Salud Estado Silencio Acción requerida
|-------------|--------------|-----------------|
Silencio 80-100 Silencio Saludable Silencio mantenimiento rutinario sólo Silencio
TEN 60-79 TENIDO ENVEJER ANTERIOR DE LA PROPAGACION DE LA BIENVENCIÓN EN 1-2 Sprints TENIDO
Silencio 40-59 Silencio Rotting Silencio Reparación inmediata sprint necesita ←
Silencio 0-39 Silencio crítico Silencio contexto completo reconstrucción recomendado Silencio

## Priority Fix Order

1. **Referencia Validez** fallas - caminos rotos causan errores de agente
2. **Instrucción Moneda** fracasos - instrucciones obsoletas causan comportamiento equivocado
3. **Destino**: fracasos: duplica el presupuesto del contexto de los desechos y causa conflictos
4. **La salud de la rublo** fallas - reglas de establo cargan contenido innecesario
5. **Evaluación de los fallos** - bloat degrada todas las operaciones
6. ** Insuficiencias de la higiene de memoria** - agentes de la memoria de los archivos de memoria
