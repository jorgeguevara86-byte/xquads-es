---
name: marketing-squad
description: >-
  Escuadrón que reúne al mejor agente de cada disciplina de marketing: mensaje (Donald
  Miller/StoryBrand), copia (Eugene Schwartz), tráfico (Pedro Sobral) y creativo. Uso para punta
  de campaña integrada a punta, cuando la demanda cruza el mensaje, copia, creativo y medios paga
  al mismo tiempo y no vale la pena abrir un cuadrado especializado para cada paso.
  one-linerStoryBrand.
license: MIT
metadata:
  squad: "Squad de comercialización"
  version: "1.0.0"
  agents: "5"
  author: "Xquads by Synkra"
---

# Squad de comercialización

**Dominio:** Elite marketing — el mejor agente de cada disciplina, orquestado en una línea de montaje: mensaje → copy → creativo → distribución

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/marketing-chief.md` Y la definición autocontenida de la cabeza de la
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

** Jefe del equipo** `agents/marketing-chief.md`

**Especialistas (4)**

- `agents/donald-miller.md`
- `agents/eugene-schwartz.md`
- `agents/pedro-sobral.md`
- `agents/visual-generator.md`

## Tasks (6)

- `tasks/build-message.md`
- `tasks/build-traffic.md`
- `tasks/create-creatives.md`
- `tasks/diagnose.md`
- `tasks/review.md`
- `tasks/write-copy.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-full-campaign.yaml`
- `workflows/wf-launch.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
