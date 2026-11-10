# Instalar en ChatGPT Work

## Fácil: copiar y pegar

1. Abre **ChatGPT Work en la aplicación de escritorio**, con acceso local a
   archivos y terminal.
2. Pega el [prompt de instalación global](PROMPT-INSTALACION-GLOBAL.txt).
3. Tras instalar, abre una conversación nueva y escribe **@** para seleccionar
   `xquads` u otro equipo. Si la aplicación pide reiniciar, hazlo primero.

El prompt solicita instalación personal, no una instalación limitada a una
carpeta. No prometemos que una sandbox web pueda modificar tu computadora.

## Instalar como plugin desde el catálogo propio

El repositorio incluye `.agents/plugins/marketplace.json` y el plugin de 15
skills en `plugins/xquads-es/`. Un asistente con terminal puede registrar el
catálogo mediante el comando oficial disponible:

```bash
codex plugin marketplace add jorgeguevara86-byte/xquads-es
```

Después, reinicia la aplicación de escritorio, abre el directorio de Plugins,
elige la fuente **Xquads en español** e instala **xquads-es**. Si usas las skills
globales directamente, no dupliques esa instalación con el plugin sin necesidad.

El [ZIP del plugin](https://github.com/jorgeguevara86-byte/xquads-es/releases/latest/download/xquads-es-work-plugin.zip)
sirve como paquete local para herramientas compatibles; no se sube como TXT de
conocimiento. No está publicado ni aprobado en el directorio universal de OpenAI.
La distribución en navegador mediante un plugin del directorio requiere el
proceso de publicación y las políticas de la cuenta; no se garantiza acceso a
instalación de plugins personalizados en todas las cuentas.

La estructura y las referencias se verificaron localmente. La carga y el
selector dentro de una cuenta de ChatGPT Work aún deben probarse.

Fuentes oficiales:
- https://learn.chatgpt.com/docs/build-skills
- https://developers.openai.com/plugins/build/plugins
