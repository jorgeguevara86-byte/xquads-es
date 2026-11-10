# Instalación global para usuarios

## La opción más fácil

1. Abre Claude Code, Codex u otra aplicación compatible con Agent Skills que
   pueda trabajar con los archivos de tu computadora.
2. Copia y envía [este prompt](PROMPT-INSTALACION-GLOBAL.txt).
3. Tras instalar, abre una nueva sesión si el cliente lo requiere.

La instalación es por usuario, no solo para una carpeta: el instalador crea el
hub global `~/.agents/skills/` y enlaza los clientes que lo necesitan. No requiere
permisos de administrador. El modo `--project` es opcional y NO es el que pide
el prompt global. El modo global y su conservación de skills ajenas se prueban
en `scripts/testar.sh` dentro de un usuario temporal aislado.

## Elegir un equipo

- **Claude Code:** escribe `/` y busca `xquads` o el nombre del squad.
- **Codex:** usa `/skills` para ver el catálogo o `$xquads` para invocarlo.
- Dentro de un equipo, pide los especialistas disponibles o usa `*help`.
- Los nombres que se registran en el catálogo global son los 15 squads; no se
  registra por separado cada persona de sus archivos `agents/`.

El formato del menú y la actualización del catálogo dependen de la versión y
configuración del cliente. El instalador no puede modificar menús internos de
una aplicación que no soporte Agent Skills.

## ChatGPT y Claude en navegador

El menú `/` de Claude Code no es el selector de skills de ChatGPT. Para ChatGPT
Work de escritorio usa la [guía Work](INSTALAR-WORK.md): su selector es `@`.
Un comando ejecutado en una sandbox web no instala archivos en la computadora
del usuario. Para conversaciones sin instalación de plugins o skills, usa la
[guía alternativa de ChatGPT](INSTALAR-CHATGPT.md) o
la [guía de Claude](INSTALAR-CLAUDE.md). Las funciones disponibles dependen de
tu cuenta; la skill de Claude puede activarse donde esa función esté habilitada.

## Instalación manual opcional

```bash
git clone https://github.com/jorgeguevara86-byte/xquads-es.git
cd xquads-es
bash install.sh
```

Estas instrucciones instalan desde tu copia española, no desde el proyecto
original en portugués. La prueba dentro de la aplicación del usuario sigue
siendo necesaria; no se afirma haberla realizado en su computadora.
