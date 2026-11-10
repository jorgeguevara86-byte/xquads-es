# Change Impact Assessment Checklist

** ID de lista de verificación:** CCM-CL-002
**Referido por:** config-engineer, roadmap-sentinel
**Fuente:** Evaluar sistemáticamente el impacto de las modificaciones de configuración del Código de Claude antes de aplicarlas. Garantiza la compatibilidad atrasada, la integridad de la seguridad y la disciplina presupuestaria contextual.

[[LLM: INITIALIZATION INSTRUCTIONS - CHANGE IMPACT ASSESSMENT

Esta lista de verificación se utiliza antes de aplicar cambios de configuración al Código Claude
artefactos (.claude/ directorio, configuraciones, reglas, ganchos, configuración MCP).

ENFOQUE DE EJECUCIÓN:
1. Identificar todos los archivos que cambiarán
2. Para cada categoría, evalúe las conclusiones de los efectos y los documentos
3. Los efectos de la seguridad deben evaluarse explícitamente -- nunca saltar
4. Un plan de devolución es obligatorio para cualquier cambio que toque las reglas o ganchos deniega
5. Presentar la evaluación completa al usuario para su aprobación

Los cambios en la configuración del Código de Claude afectan a TODOS los agentes y sesiones.
Tratar cambios de configuración con el mismo rigor que las implementaciones de producción.]]

---

## 1. Evaluación de la aplicación

- [ ] Listar todos los archivos de configuración afectados por este cambio (settings.json, configuración.local.json, CLAUDE.md, reglas/)
- [ ] Identificar qué agentes son afectados (ver definiciones de agente para dependencias en archivos cambiados)
- [ ] Determinar si el cambio afecta sólo al proyecto actual o a todos los proyectos (en el ámbito global vs local)
Verificar el cambio no toca framework-protected caminos (L1/L2 límites)
- [ ] Documentar la motivación para el cambio (comprsión de la compra, optimización, nueva capacidad, endurecimiento de seguridad)

## 2. Compatibilidad Retrocede

- [ ] Los flujos de trabajo de activación de agente existentes todavía funcionan después del cambio
- [ ] No hay regresiones de permiso (agentes que podrían acceder previamente a los archivos todavía pueden)
- [ ] comandos personalizados definidos en archivos de agente todavía resuelven a caminos de tarea válidos
- [ ] Flujos de trabajo referencia reglas o ajustes cambiados todavía ejecutan correctamente
- [ ] Las integraciones de gancho (PreToolUse, PostToolUse) siguen siendo funcionales
- [ ] Si elimina una regla o un ajuste, no confirme ningún agente o flujo de trabajo depende de ella

## 3. Impacto de la seguridad

- [ ] La denegación de reglas no se debilitan o eliminan sin justificación explícita de seguridad (CRITICAL)
- [ ] No nuevos patrones de archivos sensibles expuestos por permiten adiciones de reglas (CRITICAL)
- [ ] Cambios en el modo de permiso son intencionales (explore/ask/auto transiciones documentadas)
- [ ] patrones de archivos secretos (.env, credentials.json*.key, *.pem) permanecen en las reglas de la negación
- [ ] El acceso al servidor MCP no se amplía más allá del alcance previsto
- [ ] Hook scripts no introducen nuevo sistema de archivos escriba acceso a áreas protegidas

## 4. Impacto del contexto

- [ ] Cálculo CLAUDE.md línea con elta (antes vs después del cambio)
Conteo reglas de archivos delta (added, removed, modified)
- [ ] Evaluar el presupuesto delta del contexto del MCP (nuevos servidores añadir el contexto de arriba)
Verificar el total always-loaded context stays within performance budget
- Si añadiendo algo nuevo always-loaded contenido, identificar qué se puede mover a path-scoped Normas
No se introdujo duplicación innecesaria entre CLAUDE.md, reglas y definiciones de agente

## 5. Plan de redondeo

- Los cambios pueden ser revertidos con un solo control de git o pasos manuales documentados
- [ ] El respaldo de la configuración actual existe antes de aplicar cambios (CRITICAL)
- [ ] El procedimiento de redondeo se documenta en notas de cambio
- [ ] Si el cambio implica modificaciones de gancho, la versión anterior de gancho se conserva
- [ ] Base de datos o cambios estatales persistentes (si los hay) tienen un camino de inversión

---

## PASS/FAIL Criteria

**PASS:** Todos los impactos evaluados y mitigados. La sección de seguridad tiene cero elementos no comprobados.

**FIL:** Cualquier artículo en Seguridad Impacto no se controla sin justificación, O ningún plan de devolución documentado, O evaluación de alcance incompleta.

**Acción sobre la FAIL:** Abordar todas las lagunas de seguridad y el plan de devolución de documentos antes de proceder. config-engineer si no está seguro de las implicaciones de seguridad.
