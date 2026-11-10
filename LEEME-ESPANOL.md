# Xquads — edición en español

Esta copia contiene los 15 squads del proyecto Xquads, con las instrucciones,
personas, tareas, listas de comprobación, catálogos y flujos de trabajo traducidos
automáticamente al español. Se han revisado la estructura, el empaquetado y las
reglas de idioma; no se ha hecho una revisión editorial experta de cada frase.

## Uso

Lee `README.md` para instalar. El punto de entrada general es `xquads/SKILL.md`.
Las instrucciones de los agentes usan español por defecto. Se conservan los
nombres de archivo, identificadores, claves YAML, comandos, enlaces y marcas.
Los scripts ejecutables y fragmentos de código conservan su lógica original;
sus comentarios y algunos mensajes de mantenimiento pueden seguir en portugués.
El generador de SKILL.md incluye un diccionario local para regenerar en español.

## Origen y cambios

- Autoría original: Xquads / Synkra y los autores indicados en cada archivo.
- Fuente: https://github.com/ohmyjahh/xquads-squads
- Commit original: cd5e7985d7886e617e6c84cb4156d35e1b5c69df
- Fecha de esta copia: 2026-11-10.
- Se conserva la atribución y las declaraciones de licencia originales.
  El repositorio fuente no incluye un archivo LICENSE raíz; varios manifiestos
  declaran MIT. Esta traducción no concede derechos adicionales.
- Se omiten únicamente `.git/` y los 8 archivos de metadatos macOS `.DS_Store`.
- Corrección de YAML en `copy-master/data/persuasion-psychology.yaml`:
  la lista de Sugarman se anida en `triggers` para no mezclar mapa y secuencia.
- Algunas definiciones de agentes del original usan YAML ilustrativo no válido;
  se conserva ese formato documental, traduciendo sus valores sin cambiar claves.

## Verificación

Ejecuta `python3 scripts/validar-skills.py` para validar las 15 skills.
La copia se guarda como recurso independiente: no instala ni activa agentes en
el portal y no modifica el código en producción.
