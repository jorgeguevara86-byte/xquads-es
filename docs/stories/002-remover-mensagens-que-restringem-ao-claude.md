# Story 002 — Remover as mensagens que dizem que o Xquads é só para o Claude

**Epoto:** Distribución de Xquads
**Estatus:** Hecho
** Creado en:** 2026-09-29
** Agente creador: ** @master
**Depende de:** [Story 001](001-portabilidade-universal-agent-skills.md) (Done)

---

# Descripción #

Story 001 ha hecho que Xquads sea instalado en cualquier cliente compatible con el Agente Skills,
y el repositorio fue publicado.*documentação enfocado en el estudiante seguía diciendo que
El producto es del Código Claude**. Los estudiantes que usan Codex informan que un mensaje aparece
restringir el uso a Claude.

Encuesta de lo que el estudiante lee efectivamente:


|---|---|---|
 `/downloads`  Node.js 18+, Git, **Código de Claudio (CLI antropopico)**"
 `/downloads` . Pasos: descargar ZIP, extraer, "copiar los equipos/ carpeta a su proyecto aios-core" `install.sh` |
TENISTERIO, `/downloads` Silencio Lista de escuadrones incompleta (faltam Copy Master, Marketing Squad, Xquads Chief) Silencio Subvende o pacote Silencio
 `xquads/README.md`  `cp -r ... ~/.claude/commands/` y "Requisitos: equipos instalados en `~/.claude/commands/`"... ensucia el camino que sólo funciona en el Código Claude. .
 `claude-code-mastery/README.md`  `/AIOS:agents:<agente>` 

El README principal y el 15 `SKILL.md` Han tenido razón desde la historia 001: el problema se ha convertido en
en los archivos que no tocó.

# Valor de negocio

Los estudiantes de Codex están bloqueados por documentación, no por tecnología: el producto ya funciona
para ellos desde entonces 27/09. Cada día con el mensaje en el aire es estudiante renunciando a algo que ya está
listo y generando soporte innecesario.

# Criterios de aceptación

- **AC1** - La página `/downloads` no presenta ningún cliente de AI como un requisito previo.
  Los requisitos previos se convierten en lo que es realmente necesario (Git), y los nombres de las páginas
  explícitamente los clientes compatibles.
- **AC2** - Pasos de instalación `/downloads` reflejar el flujo real: el comando único del
  `install.sh`, y no la carpeta de flujo ZIP extinto + copia a `aios-core`.
**AC3** - La lista de equipos `/downloads` está completo y coincide con el repositorio (15).
- **AC4** - `xquads/README.md` enseña instalación universal; instalación por
  `~/.claude/commands/` Parece que sólo se le ha etiquetado como una alternativa heredada al Código Claude.
- **C5** - `claude-code-mastery/README.md` presenta la activación de una manera agnóstica; la activación de la forma agnóstica de la
  sintaxis `/AIOS:agents:x` Es sólo una alternativa heredada.
**AC6** — Ningún archivo de página de repositorio o página web presenta a un cliente de AI como
  requisito de usar Xquads, verificado por el escaneo automatizado.
**AC7** – AC6 check entry into suite `scripts/testar.sh`- Para no retroceder.
**AC8** — Las 40 pruebas existentes continúan pasando; construyen los pases del sitio.

## Escopo

### IN
- `~/Desktop/Projetos/xquads/src/app/downloads/page.tsx` - requisitos, pasos y lista
- `~/xquads-squads/xquads/README.md`
- `~/xquads-squads/claude-code-mastery/README.md`
- Nuevo cheque `~/xquads-squads/scripts/testar.sh`

### OUT
- Reescribir las READMEs de las otras 13 equipos (no tiene sección de instalación o restricción)
- Recrear la descarga ZIP (el botón de hoy conduce a la forma de plomo + VSL; cambiar esto es
  decisión comercial, no documentación)
- Cambiar el contenido técnico de la equipo `claude-code-mastery` (es sobre herramientas de agente
  a)
- Sincronizar `~/Desktop/Projetos/xquads/squads/` con el repo instalado (story separate)
- Desplazamiento del sitio sin autorización explícita

# Dependencias

- Historia 001 (Done e publicada em `4d04da3`)

## Complexidade

**P** — cuatro archivos, cambios de texto y un nuevo cheque. No hay lógica de negocio.

## Riscos


|---|---|---|
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
 `npm run build` y el forro antes de escalar



# Los criterios de Done

- [x] AC1 a AC8 verificada
- [x] `bash scripts/testar.sh` Paso
- [x] `npm run build` y `npm run lint` pasar en el sitio
- [x] Sweep confirma cero menciones al cliente como requisito
Nada subió sin autorización explícita del propietario

Resultados de QA

**Carta:**Páginas de la mano: **Date:**2026-09-29


|---|---|---|
.1 . . Revisión del código . . OK - cambios de texto y un nuevo bloque JSX; forro limpio en el archivo jugado . .


 `SKILL.md`, cero personas y cero cambios en `install.sh`. Site Lint: 56 problemas antes, 56 más tarde, ninguno en el archivo editado
Silencio 5 Silencioso desempeño Silencio N/A — sem impact Silencio
 `rel="noopener noreferrer"`; no se recopilan nuevos datos


*Verificar visualmente*

Página renderizada en escritorio y móvil (375x812).
línea en lugar de requerir desplazamiento horizontal: en el escritorio apareció cortado en `instal` y
No me di cuenta de que faltaba un texto.

*Extra corrección, dentro del espíritu de AC3*

El bloque "Lo que es inclusivo" dijo "96+ Agentes". Corregido a 183, que es el número real.

# Observaciones que se registran

- El botón sigue diciendo "Descargar Xquads (ZIP)" pero conduce a una forma de plomo y luego
  VSL — no bajo ningún archivo. Está en el OUT de esta historia porque es decisión comercial
  deliberado (se introdujo la red de dirección a propósito), no un defecto de documentación.
- La tarjeta AIOS Core sigue enseñando `npx aios-core install`, un flujo diferente al de
  Fuera de alcance aquí.

# Change Log


|---|---|---|
Silencio 2026-09-29 Silencio @mestre Silencio Story criada (Draft) Silencio
 10/10 - GO. Draft - Confeccionado

Silencio 2026-09-29 Silencio @qualidade TENIDO QA gate PASS (en inglés)7/7, AC 8/8). Listo - Confeccionado
