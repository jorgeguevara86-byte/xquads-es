# Copiado Squad

Escuadrón de élite de 23 agentes de redacción — 22 legendarios redactores + 1 orquestador (Jefe de Copia).

## Inicio rápido

```
@copy-chief     Activar el orquestador
*diagnose       # Triage your copywriting request
*full-copy-project  # End-to-end copiar el flujo de trabajo del proyecto
```

## Arquitectura de niveles

| Nivel | Nombre | Agentes | Enfoque |
|------|------|--------|-------|
Silencioso **0** Silencioso copy-chief Silencios demanda, comentarios, mediates Silencio
Silencio **1A** Silencio Respuesta directa Leyendas Silencio gary-halbert, eugene-schwartz, claude-hopkins, gary-bencivenga, robert-collier, john-carlton, jim-rutz TEN-forma, impresión, correo
Silencio **1B** Silencio Moderno Copiar &amp; Dibujos Silencioso dan-kennedy, frank-kern, russell-brunson, todd-brown, stefan-georgi, jon-benson, ry-schwartz TEN VSLs, embudos, webinars, lanza TEN
Silencio **1C** Silencioso Correo electrónico &amp; Relación ben-settle, andre-chaperon, dan-koe TEN-E-mail secuencias, correos electrónicos diarios, nutrir TEN
Silencio **1D** Silencio Ofertas &amp; Páginas de Ventas Silencio joe-sugarman, david-ogilvy, clayton-makepeace, parris-lampropoulos, david-deutsch Silencio Oferta arquitectura, anuncios impresos, financial/health |

## Matriz de enrutamiento

El Jefe de Copias envía automáticamente su solicitud al mejor especialista:

Silencioso Solicitud Tipo Silencio Primario Silencio
|-------------|---------|-----------|
| Headline | eugene-schwartz | gary-halbert |
TENIDA Carta de venta / long-form | gary-halbert | john-carlton |
Silencioso de la secuencia de correo electrónico andre-chaperon | ben-settle |
TEN VSL / carta de venta de vídeo TEN  stefan-georgi | jon-benson |
 russell-brunson | todd-brown |
Silencioso Oferta creación Silencio dan-kennedy | joe-sugarman |
Silencio Copia de embudo Silencio russell-brunson | frank-kern |
← Gran idea / concepto de campaña ← todd-brown | eugene-schwartz |
TENCIÓN Puntos de bullet / fascinaciones TENCIÓN gary-bencivenga | clayton-makepeace |
Silencio Correos electrónicos diarios / compromiso Silencio ben-settle | dan-koe |
TENIS Clásico carta de ventas / correo robert-collier | jim-rutz |
TENIDA Copia financiera / sanitaria TENIDO clayton-makepeace | parris-lampropoulos |
TENIDO Marca / copia premium TEN david-ogilvy | david-deutsch |
Silencio Copia de anuncios / anuncios pagados Silencio dan-kennedy | frank-kern |
Silencio Lanzamiento de copia Silencio frank-kern | russell-brunson |
Silencio Personal brand copy Silencio dan-koe | ry-schwartz |
Silencio Copiar revisión / crítica Silencio copy-chief | eugene-schwartz |

## Components

**23 agentes** — 1 orquestador + 22 especialistas
- 13 tareas** write-headline, write-sales-letter, write-vsl-script, write-email-sequence, write-ad-copy, write-landing-page, write-bullets, create-funnel-copy, create-offer, analyze-copy, critique-copy, diagnosticar, revisar
- **2 workflows** — full-copy-project, copy-review-cycle
* 1 lista de verificación* output-quality (porta de calidad para los entregables)
- **2 archivos de fecha** - routing-catalog, copy-frameworks

## Workflows

### Full Copy Project (Proyecto de copia completa)`*full-copy-project`)
Fin-to-end: breve √≠gnose √≠o asignar especialista √≠ escriba √≠ opinión √≥n entrega.

### Copia ciclo de revisión (`*copy-review-cycle`)
Iterative write-critique-revise bucle (máximo 3 iteraciones).

## Requirements

- AIOS >= 4.0.0
