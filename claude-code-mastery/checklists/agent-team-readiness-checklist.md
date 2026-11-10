# Agente Equipo de Readiness Lista de verificación

** ID de lista de verificación:**CCM-CL-003
**Referido por:** swarm-orchestrator
**Fuente:** Validación prepachada antes de lanzar equipos de agentes paralelos o secuenciales. Garantiza que la descomposición de tareas es sólida, los agentes están configurados, se planea el aislamiento y se define la recuperación de fallos.

[[LLM: INITIALIZATION INSTRUCTIONS - AGENT TEAM READINESS

Esta lista de verificación valida que multi-agent plan de ejecución es seguro
para lanzarse, evitará desperdiciar el computador, fusionar conflictos y huérfanos
trabajo capturando problemas de configuración antes de que cualquier agente se despacha.

ENFOQUE DE EJECUCIÓN:
1. Examen del plan de descomposición de tareas
2. Validar la configuración y el acceso de cada agente
3. Confirmar la estrategia de aislamiento impide conflictos
4. Verificar los límites de recursos y las estimaciones de gastos
5. Asegurar la comunicación y combinar estrategias
6. Todos los elementos críticos deben pasar antes de que cualquier agente se desprenda

Los agentes de la cosecha sin validación crean un trabajo costoso de limpieza.]]

---

## 1. Task Decomposition

- [ ] Todos los subtaces se identifican con límites de alcance claro (CRITICAL)
- [ ] Las dependencias entre subtaces son mapeadas (que debe terminar antes de que otros comiencen)
No existen dependencias circulares entre subtaces (CRITICAL)
Cada subtarea tiene un único agente responsable asignado
- [ ] Los productos de subtasis son well-defined (files, artefactos, informes de estado)
[ ] La complejidad estimada por subtask se documenta (small/medium/large)
- [ ] Subtareas seguras paralelas se identifican (no hay modificaciones de archivos compartidos)

## 2. Configuración del agente

- [ ] Archivos de definición de agente (.md) existen para cada agente asignado (CRITICAL)
- [ ] La selección de modelos es apropiada para la complejidad de la tarea de cada agente
- [ ] Restricciones de herramientas coinciden con las necesidades de cada agente (sin acceso innecesario de herramientas)
- [ ] Agentes personas no entran en conflicto con los requisitos de subtask
- [ ] Insinuaciones del sistema o CLAUDE.md el contenido es compatible con funciones de agente
Cada agente tiene acceso a los archivos específicos que necesita read/modify

## 3. Estrategia de la solución

- [ ] Worktree vs espacio de trabajo compartido decisión se toma y documenta (CRITICAL)
- [ ] convención de designación de rama definida (por ejemplo, agente/{agent-id}/{subtask-id})
- Si el espacio de trabajo compartido: file-level estrategia de bloqueo definida para prevenir conflictos
- [ ] Si el aislamiento del árbol de trabajo: rama base para cada árbol de trabajo identificado
- Los agentes que trabajan en la misma base de códigos tienen non-overlapping alcances de los archivos
- [ ] Archivos temporales y artefactos de construcción tienen agent-specific caminos

## 4. Planificación de recursos

- [ ] max_turns está establecido para que cada agente impida la ejecución de fuga (CRITICAL)
- [ ] Antecedentes vs ejecución por sobrecogedor decidido por agente
- Costo total estimado calculado en todos los agentes
- [ ] Precio de techo definido (máximo gasto antes de detenerse)
- [ ] Los límites de tiempo fijados para cada agente despachado
- [ ] Memory/context presupuesto por agente evaluado (los cóbicos pueden alcanzar límites)

## 5. Plan de Comunicación

- [ ] Cómo los agentes comparten resultados intermedios se define (archivos, archivos de estado, stdout)
- [ ] La estrategia de fusión para combinar los productos de los agentes se documenta (CRITICAL)
- [ ] Procedimiento de resolución de conflictos existe para superar los cambios
- [ ] Mecanismo de presentación de informes sobre el estado definido (polling, completion files, events)
- [ ] Punto de integración final identificado (que agente o proceso fusiona todo)
- [ ] Fabricación de artefactos entre agentes secuenciales se especifica

## 6. Plan de redondeo

- [ ] ¿Qué pasa si un agente individual falla se define (CRITICAL)
- [ ] Procedimiento de limpieza para el trabajo parcial del agente fallido está documentado
Otros agentes pueden continuar independientemente si uno falla (degradación grave)
- [ ] El comando de limpieza de Worktree está preparado para post-execution
- El estado de Git puede ser restaurado pre-spawn basal si el equipo entero falla
Se planea la detección y limpieza de ramas huérfanas

---

## PASS/FAIL Criteria

**PASS:** Todos los elementos marcados (CRITICAL) son revisados. Todos los agentes tienen definiciones válidas. La descomposición de tareas no tiene dependencias circulares.

**FAIL:** Cualquier elemento (CRITICAL) no comprobado. Archivo de definición de agente perdido. Confiabilidad circular detectada. No se define estrategia de fusión.

**Acción sobre FAIL:** Fijar todas las lagunas críticas antes de despachar a cualquier agente. Si la descomposición de tareas tiene dependencias circulares, reestructurar el plan. Si las definiciones de agente faltan, cree primero.
