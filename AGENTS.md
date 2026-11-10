# Xquads — instrucciones para agentes

Este repositorio es una colección de **squads de agentes de IA** distribuidos como
[Habilidades del agente](https://agentskills.io), el estándar de extensión de agente abierto.
Cada carpeta de primer nivel con un `SKILL.md` es una habilidad independiente.

## Qué leer primero

Si el usuario describió una demanda pero no dijo qué escuadrón quiere, lea
`xquads/SKILL.md`. Es el jefe general: diagnostica el dominio y activa la plantilla
cierto. Si el usuario nominó el equipo, vaya directamente a su `SKILL.md` .

##Cómo funciona un escuadrón

```
squad/
├── SKILL.md Punto de entrada. Te dice cómo activarlo y qué hay dentro.
├── agentes/Personas autónomos. Leer el archivo = adoptar el agente.
├── tareas/ Scripts ejecutables, con entradas, pasos y salida definida.
├── flujos de trabajo/Secuencias multi-agente ya encadenados.
├── listas de verificación/ Validación de calidad antes de la entrega.
├── datos/Catálogos de enrutamiento y marcos de referencia.
└── configuración/niveles, íconos y metadatos del escuadrón.
Los equipos
```

tienen un **chefe** (`entry_agent` en `squad.yaml`) que diagnostica y
delega y **especialistas** se ejecuta. El jefe no hace el trabajo del jefe.
Especialista
: sin borrador.

## Reglas de activación

1. Todas las rutas dentro de un `SKILL.md` son relativas a la raíz de esa habilidad.
2. Leer el expediente de un agente significa **assumir esa persona en su totalidad**:
   principios, estilo, límites y el `greeting`.
3. Un agente a la vez. El cambio de agente pone fin a la persona anterior.
4. Los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los de la persona).
5. Responder en español, a menos que se solicite explícitamente lo contrario.
6. Las tareas con `elicit: true` requieren la respuesta del usuario en cada punto de
   elicitación. No asuma respuestas ni se salte pasos.

## Fuera de alcance

Los equipos de Xquads cubren marketing, texto, marca, tráfico, narración de historias, diseño,
datos, estrategia, seguridad y movimiento. **El desarrollo de software no es
alcance de este repositorio**: el código va al flujo de desarrollo de
usuário.

Squad `cybersecurity` cubre técnicas ofensivas y solo debe activarse en
contexto autorizado: pentest contratado, CTF, investigación de seguridad o defensa de seguridad
infraestructura propia.

## Mantenimiento del repositorio

- `SKILL.md` es **gerado**, no editado a mano. La fuente es
   `scripts/gerar-skills.py`, que dice `squad.yaml` y `config/config.yaml`. Para
  cambiar un `SKILL.md`, cambiar el generador o la descripción curada dentro de él y
  rode `python3 scripts/gerar-skills.py`.
- `python3 scripts/validar-skills.py` valida el 15 `SKILL.md` según las especificaciones.
  Ejecutar antes de cualquier compromiso que afecte a los escuadrones.
: no ingrese rutas de cliente absolutas (`~/.claude/...`, `~/.codex/...`)
  en las instrucciones de activación. Esto rompe la portabilidad, razón por la cual el
El repositorio
  estará en este formato.
