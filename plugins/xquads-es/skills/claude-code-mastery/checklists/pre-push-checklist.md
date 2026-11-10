# Pre-Push Quality Gate Checklist

** ID de lista de verificación:**CCM-CL-001
**Referido por:** config-engineer, roadmap-sentinel
**Fuente:** Validar la configuración del Código Claude cambia antes de empujar a distancia. Garantiza la integridad de la configuración, CLAUDE.md calidad, corrección de reglas, seguridad de ganchos, y la cordura MCP.

[[LLM: INITIALIZATION INSTRUCTIONS - PRE-PUSH VALIDATION

Esta lista valida los cambios de configuración del Código de Claude específicamente.
Complementa el marco de la AIOS pre-push-checklist pero se centra en
.claude/ directorio artifacts, settings.json, reglas, ganchos y config MCP.

ENFOQUE DE EJECUCIÓN:
1. Para cada categoría, verifique cada artículo contra el estado actual del archivo
2. Marcar los elementos como [x] Paso, [ ] Fail, o [N/ANo aplicable
3. Cualquier falla crítica del elemento bloquea el empuje
4. Las fallas no críticas deben documentarse con justificación

Los elementos CRÍTICOS están marcados con el sufijo (CRÍTICO).]]

---

## 1. Ajustes Validación

- [ ] `settings.json` es válido JSON sin errores de sintaxis (CRITICAL)
- [ ] `settings.json` contiene `deny` reglas para `.env`, credenciales y secretos (CRITICAL)
- [ ] `settings.json` contiene `deny` reglas para framework-protected caminos (L1/L2 límites)
No hay claves de API, fichas o secretos codificados en `settings.json`
- [ ] `settings.local.json` se enumeran en `.gitignore` si contiene user-specific anulaciones
- [ ] Por defecto de la autorización (`allow`/`deny`) son intencionales y coinciden con la postura de seguridad del proyecto
- [Todos] `allow` reglas tienen reglas de negar que anulan (sin agujeros abiertos)

## 2. CLAUDE.md Quality

- [ ] CLAUDE.md existe en `.claude/CLAUDE.md` (CRITICAL)
- [ ] CLAUDE.md es inferior a 500 líneas totales (recomendadas por debajo de 200 para auto-memory proyectos)
- [Todos] `AIOS-MANAGED-START` secciones tienen coincidencias `AIOS-MANAGED-END` marcadores (CRITICAL)
- [ ] No hay referencias de ruta de archivo de establo (todos los caminos mencionados existen en el repositorio)
No hay instrucciones duplicadas entre CLAUDE.md y `.claude/rules/` archivos
- [ ] Ejemplos de código en CLAUDE.md son sintacticamente válidos
No hay comentarios de TODO o FIXME CLAUDE.md contenido

## 3. Rules Validation

- [Todos] `.claude/rules/*.md` archivos tienen la delantera YAML válida (si path-scoped)
- Frontmatter `paths:` valores coinciden con directorios existentes o patrones de archivos
- No. always-loaded reglas superiores a 200 líneas (disciplina presupuestaria contexto)
Las reglas de los papeles de los caminos sólo cargan para sus tipos de archivos previstos
- No hay instrucciones contradictorias entre diferentes archivos de reglas
- [ ] Nombres de los archivos de reglas siguen kebab-case convención
- [ ] No hay reglas orfanas (referencias reales files/patterns que ya no existen)

## 4. Seguridad de gancho

- [ ] Todos los ganchos registrados tienen configuración explícita de timeout (CRITICAL)
- [ ] Ningún gancho contiene bucles infinitos o recursión sin límites (CRITICAL)
- [ ] Ganar códigos de salida siguen convención (0 = éxito, non-zero = fracaso)
- [ ] ganchos que modifican los archivos usan patrones de escritura atómica (temp + renombre)
- [ ] PreToolUse ganchos no bloquean las operaciones de herramientas esenciales
- [ ] PostToolUse ganchos manejan los errores con gracia (sin tragar silenciosa)
- [ ] Hojear caminos de archivo en settings.json resolver a los scripts existentes

## 5. Configuración MCP

- [ ] Todos los servidores MCP configurados responden a cheques de salud (si está habilitado)
- [ ] El presupuesto de contexto del MCP se mantiene dentro de los límites de los proyectos (ver core-config.yaml)
No duplicar las entradas de servidor MCP en configuración
- [ ] Los servidores MCP que requieren autenticación tienen credenciales válidas configuradas
- [ ] Los MCP basados en Docker tienen contenedores funcionando y accesibles

---

## PASS/FAIL Criteria

**PASS:** Todos los elementos marcados (CRITICAL) son revisados. Los artículos no críticos tienen menos de 3 fallos, cada uno con justificación documentada.

**FIL:** Cualquier artículo marcado (CRITICAL) no está comprobado, O más de 3 non-critical los elementos fallan sin justificación.

**Acción sobre FAIL:** Arreglar todos los problemas críticos antes de presionar. non-critical cuestiones como deuda técnica si se posterga.
