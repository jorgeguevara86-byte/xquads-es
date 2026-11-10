---
name: cybersecurity
description: Usa este equipo para seguridad, auditorías y pruebas autorizadas.
license: MIT
metadata:
  squad: Cybersecurity Squad
  version: 1.0.0
  agents: '15'
  author: Xquads by Synkra
---

# Cybersecurity Squad

**Dominio:** Operaciones de seguridad ofensivas y defensivas

√ ** Uso autorizado solamente.** Este Escuadrón cubre técnicas ofensivas. Activar sólo en combest contratado, CTF, búsqueda de seguridad o defensa de autoinfraestructura. Confirmar el contexto de autorización antes de realizar cualquier operación ofensiva.

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/cyber-chief.md` Y la definición autocontenida de la cabeza de la
   : personalidad, principios, lógica de enrutamiento y límites. Adoptala.
2. Carregue `data/routing-catalog.yaml` como contexto de roteamento. Nao exiba o conteudo,
   simplemente absorberlo.
3. Salude con el `greeting` de la persona y espere la demanda.
4. Al dirigirse a un especialista, lea `agents/<especialista>.md` y asuma
   esa persona, manteniendo el informe que preparó el jefe.
5. Permanece en el equipo hasta recibir `*exit`.

## Ejecutando una tarea

Las tareas en `tasks/` son scripts ejecutables con entradas, pasos y formato de salida definidos. Lea el archivo completo antes de comenzar y siga los pasos en orden. Las tareas marcadas con `elicit: true` requieren una respuesta del usuario en cada punto de obtención; no asuma respuestas ni se salte pasos.

## Agentes

** Jefe del equipo** `agents/cyber-chief.md`

**Especialistas (14)**

- `agents/busterer.md`
- `agents/cartographer.md`
- `agents/chris-sanders.md`
- `agents/command-generator.md`
- `agents/dirber.md`
- `agents/fuzzer.md`
- `agents/georgia-weidman.md`
- `agents/jim-manico.md`
- `agents/marcus-carey.md`
- `agents/omar-santos.md`
- `agents/peter-kim.md`
- `agents/ripper.md`
- `agents/rogue.md`
- `agents/shannon-runner.md`

## Tasks (9)

- `tasks/analyze-vulnerability.md`
- `tasks/assess-security.md`
- `tasks/audit-app-security.md`
- `tasks/diagnose.md`
- `tasks/generate-commands.md`
- `tasks/respond-incident.md`
- `tasks/review.md`
- `tasks/run-pentest.md`
- `tasks/run-recon.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-incident-response.yaml`
- `workflows/wf-pentest-engagement.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/routing-catalog.yaml`
- `data/security-tools-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
