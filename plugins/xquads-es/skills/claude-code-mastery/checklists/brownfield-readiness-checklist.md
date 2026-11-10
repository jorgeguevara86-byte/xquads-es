Lista de verificación de la luminosidad de Brownfield

** ID de lista de verificación:**CCM-CL-006
**Referido por:** project-integrator
**Purpose:** Verificación de la lentitud antes de integrar el Código Claude en un proyecto existente (campo desbrozado). Asegura que se analice el repositorio, se descubrieran convenciones, se mapean archivos sensibles y se mitiguen los riesgos.

[[LLM: INITIALIZATION INSTRUCTIONS - BROWNFIELD READINESS

Esta lista de verificación se utiliza ANTES de añadir configuración de Código Claude a una
proyecto existente. Garantiza que entendamos la base de código, protegemos
archivos sensibles e integrarse sin interrumpir los flujos de trabajo existentes.

ENFOQUE DE EJECUCIÓN:
1. Analizar la estructura del repositorio y la herramienta existente
2. Descubra convenios y modalidades ya utilizadas
3. Mapa TODOS los archivos y secretos sensibles
4. Evaluar las consideraciones de equipo para las opciones de configuración
5. Riesgos de documentos y preparación del plan de reversión
6. Todos los elementos críticos deben pasar antes de comenzar la integración

La integración de Brownfield se expone sin cuidado y descompone los flujos de trabajo.
Tómese el tiempo para entender antes de modificar.]]

---

## 1. Análisis de repositorios

El repositorio Git es inicializado y tiene historia de compromiso.
- [ ] `.gitignore` existe y cubre patrones comunes (node_modules, generar salida, archivos de OS)
- [ ] CI/CD oleoducto está presente (GitHub Actions, GitLab CI, Jenkins, etc.)
- [ ] El depósito tiene una estrategia de ramificación definida (main/develop, trunk-based, etc.)
- [ ] El administrador del paquete se identifica (npm, hilo, pnpm, bun) con el presente de Lockfile
- [ ] El sistema de construcción se identifica y funciona (`npm run build` o obras equivalentes)
- [ ] El lenguaje y el marco del proyecto se documentan o identifican

## 2. Herramienta existente

- [ ] El interinter se configura (ESLint, Prettier, etc.) con las reglas existentes
- [ ] El marco de prueba está presente (Jest, Vitest, Mocha, pitest, etc.)
- [ ] Las reglas de formato de código se definen y se aplican
- [ ] Los ganchos pre-commit existen (husky, lint-staged, etc.)
- [ ] Los archivos de configuración IDE están presentes (.vscode/, .idea/, etc.)
- [ ] Otras herramientas de codificación AI se configuran (Copilot, reglas del cursor, etc.)

## 3. Discovery de Convenciones

- [ ] Patrones de natación identificados (camelCase, PascalCase, kebab-case para archivos)
- [ ] Estructura del directorio mapeado (src/, lib/, app/, components/, etc.)
- [ ] Estilo de importación identificado (absoluto vs relativo, alias de ruta)
- [ ] Patrones de manipulación de errores documentados (try/catch, Tipos de resultados, límites de error)
- [ ] Enfoque de gestión del Estado identificado (si proyecto de frontend)
- [ ] Pautas de API documentadas (REST, GraphQL, tRPC, etc.)
- [ ] Prueba convención de nombres de archivo identificado (*.test.ts, *.spec.ts, __tests___/)

#4. Archivos sensibles

- [Todos] `.env` ficheros localizados y catalogados (CRITICAL)
- [ ] Archivos de credenciales identificados (contables de servicio, claves de API, certificados) (CRITICAL)
- [ ] Enfoque de gestión secreta documentado (vault, env vars, archivos de configuración)
- [ ] `.gitignore` ya excluye archivos secretos (verificar, no asumir)
- [ ] No secretos comprometidos encontrados en la historia de la git (el escáner secreto si está disponible)
- [ ] Archivos de clave privados (*.key, *.pem, *.p12) localizados y mapeados
- [ ] cadenas de conexión de bases de datos identificadas y su método de almacenamiento documentado

## 5. Consideraciones del equipo

- [ ] Tamaño del equipo documentado (solo, pequeño equipo, gran equipo)
- [ ] Preferencia de permiso decidido (explore para solitario, pedir equipos, auto para confianza CI)
- [ ] La estrategia de configuración local compartida vs decidido (settings.json vs configuración.local.json)
- [ ] proceso de revisión de código existente documentado (Revisiones de RRP, programación de pares)
- [ ] Equipo familiarizado con las herramientas de codificación AI evaluadas
- [ ] Plan de comunicación para introducir el Código de Claude a miembros del equipo definido

6. Evaluación de riesgos

- [ ] Rutas críticas identificadas (auth, pagos, procesamiento de datos) que necesitan reglas de negación extra
- [ ] Plan de Rollback existe (puede eliminar .claude/ directorio de forma limpia) (CRITICAL)
No existe un directorio .claude/ que sería sobrescrito
- [ ] La integración no modificará las existentes CI/CD sin aprobación explícita
- [ ] El primer ámbito de integración es limitado (comienza con CLAUDE.md + ajustes, añadir reglas incrementalmente)
- [ ] Medio ambiente de prueba disponible para validar la integración antes team-wide rollout

---

## PASS/FAIL Criteria

**PASS:** Todos los elementos marcados (CRITICAL) son revisados. Los archivos sensibles son completamente mapeados. Plan de Rollback documentado. Evaluación de riesgos completa con las atenuaciones para cada riesgo identificado.

**FIL:** Cualquier elemento (CRITICAL) no revisado. Archivos sensibles no identificados completamente. No hay plan de devolución. Evaluación de riesgo incompleto.

**Acción sobre FAIL:** Completamente sensible cartografía de archivos antes de cualquier trabajo de integración. Plan de devolución de documentos. Si los secretos se encuentran en la historia de la git, dirijan ese problema de seguridad antes de proceder con la integración de Claude Code.
