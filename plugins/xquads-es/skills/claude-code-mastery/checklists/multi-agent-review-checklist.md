# Multi-Agent Review Checklist

** ID de lista de verificación:** CCM-CL-004
**Referido por:** swarm-orchestrator
**Purpose:** Validación posterior a la finalización después de que un equipo de agente termine de trabajar. Garantiza que todos los productos estén presentes, fusionados sin conflictos, cumplan con los estándares de calidad y todos los recursos temporales se limpian.

[[LLM: INITIALIZATION INSTRUCTIONS - MULTI-AGENT REVIEW

Esta lista de verificación valida la salida combinada de una multi-agent ejecución.
Ejecute este AFTER todos los agentes han completado o se han cronometrado.

ENFOQUE DE EJECUCIÓN:
1. Verificar cada agente devolvió un resultado (o documentar por qué no lo hizo)
2. Comprobar conflictos entre los productos de los agentes
3. Validar cada salida con arreglo a sus criterios de aceptación
4. Limpiar todos los árboles de trabajo, ramas y artefactos temporales
5. Ejecutar pruebas de integración en el resultado combinado
6. Todos los elementos fundamentales deben pasar para que la ejecución del equipo sea considerada exitosa

Salteando post-execution revisión conduce a los recursos huérfanos y fracasos ocultos.]]

---

## 1. Output Completeness

- [ ] Todos los agentes despachados devolvieron los resultados (sin fallas silenciosas) (CRITICAL)
- [ ] Agentes que se han presentado tienen documentado su trabajo parcial
- La salida de cada agente coincide con su alcance de subtasco asignado
Ningún agente produjo salida vacía o de marca de posición
- [ ] Los informes de estado de cada agente se recogen y revisan
Agentes que encontraron errores registraron su razón de fracaso.

## 2. Medición de la validación

- No. file-level conflictos entre los productos de los agentes (CRITICAL)
- [ ] Si existen conflictos, se resuelven con la racionalidad documentada
- [ ] Formato de código consistente en todos los productos de los agentes (configurado de la misma lint aplicada)
- No hay duplicado function/variable/component nombres introducidos por diferentes agentes
- [ ] Las declaraciones de importación son consistentes (sin versiones de dependencia conflictivas)
- [ ] Archivos de configuración compartidos (package.json, tsconfig, etc.) se fusionan correctamente

## 3. Control de calidad

- [ ] La salida de cada agente cumple con sus criterios de aceptación de subtascos (CRITICAL)
- [ ] `npm run lint` pasa en la base de código combinado
- [ ] `npm run typecheck` pasa en la base de código combinada (si TipoScript)
Pruebas de unidad de cada agente pasan individualmente
No se introducen regresiones (se siguen realizando pruebas)
- [ ] El código sigue las normas y patrones de codificación de proyectos

## 4. Limpieza de árboles de trabajo

- [ ] Todos los árboles de trabajo creados para esta ejecución son fusionados o eliminados (CRITICAL)
- No quedan ramas huérfanas del trabajo de agente
Los archivos temporales creados por agentes son limpiados
- [ ] Fabricación de artefactos específicos para el agente son eliminados
- [ ] `.git/worktrees/` directorio no tiene entradas de estambre
- [ ] Las reglas de protección de ramas se restablecen si se modifica temporalmente

## 5. Prueba de integración

- [] Producción combinada compiles/builds con éxito (CRITICAL)
- [ ] `npm test` pasa en la base de código integrada completa
- Fin...to-end flujos de trabajo afectados por los cambios todavía funcionan
- [ ] Los contratos de API entre componentes escritos por diferentes agentes son compatibles
- No se introducen dependencias circulares entre nuevos módulos
- [ ] Los parámetros de referencia de rendimiento están dentro de un rango aceptable (no hay degradación significativa)

---

## PASS/FAIL Criteria

**PASS:** Todos los agentes devolvieron los resultados. No hay conflictos de fusión sin resolver. La base de código combinada pasa lint, tipocheck y pruebas. Todos los árboles de trabajo limpiaron.

**FAIL:** Cualquier agente no produjo salida sin razón documentada. Existen conflictos de fusión sin resolver. Fallan las pruebas combinadas. Permanecen los árboles de trabajo o ramas huérfanos.

**Acción sobre FAIL:** Para los productos perdidos, determinar la causa raíz y re-run Para combinar conflictos, resuelva manualmente y documente. Para fallos de prueba, identifique qué producto del agente causa el fracaso y la fijación. Para los recursos huérfanos, ejecute comandos de limpieza.
