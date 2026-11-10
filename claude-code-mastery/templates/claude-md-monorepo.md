# CLAUDE.md — Proyecto Monorepo

## Project Overview

- No me digas.
- **Descripción:** [Descripción del Reino]
- #Tipo: # Monorepo
- **Manager:** [Turborepo / Nx / Lerna / pnpm espacios de trabajo]
- **Estatus:** [Desarrollo / Estadio / Producción]

## Package Structure

```
packages/
  core/ # Comparti-niveles de negocio
  ui/ # Biblioteca de componentes de la UI compartida
  config/ # Config compartido (ESLint, TypeScript, Tailwind)
  utiles/ # Funciones de utilidad compartidas
apps/
  web/ # Aplicación web principal (Next.js)
  api/ # Backend API service
  docs/ # Sitio de documentación
  admin/ # Admin dashboard
tooling/
  eslint-config/ # Configuración compartida de ESLint
  tsconfig/ # Configuración de Tipos de script compartido
  jest-config/ # Configuración Jest compartida
```

## Tech Stack

Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|-------|-----------|-------|
← Construir Silencio Turborepo Silencioso orquestación de tareas y caché ANTE
TENEDA TENCIÓN TERRITOR ANTERIOR Soporte en el espacio de trabajo, estricto acolchado TEN
Silencio Idioma Silencio TipoScript Silencio Tsconfig compartido en herramientas / Silencio
← ← Silencio ESLint Silencio Config en paquetes compartidos
← Testing Silencio Silencio Silencio Config compartido, per-package execution confidencialidad

## Dependencias compartidas

### Paquetes internos (espacio de trabajo:*)
- `@[scope]/core` — lógica empresarial, tipos, constantes
- `@[scope]/ui` — Reactar componentes, fichas de diseño
- `@[scope]/utils` — Funciones de utilidad (fecha, cadena, validación)
- `@[scope]/config` — Archivos de configuración compartidos

### Dependency Rules
- **Reportaciones de la red:** Sólo herramientas de dev (turbo, más bonito, husky)
**Despidos compartidos** Declarados en el paquete que los posee
- **Alineación de la vista** `syncpack` o `manypkg` para mantener las versiones consistentes
* *Dependencias de los usuarios*: *Los componentes de la UI declaran React como dep de pares
- Nunca instalar la misma dependencia en diferentes versiones en paquetes

## Per-Package Conventions

### apps/web (Next.js)
```bash
pnpm --filter web dev        # Dev server
pnpm --filter web build      # Production build
pnpm --filter web test       # Tests
```
- Importaciones de `@[scope]/ui` y `@[scope]/core`
- Usos App Router, sigue patrones de establo completo

### apps/api (Express/Fastify)
```bash
pnpm --filter api dev        # Dev server
pnpm --filter api build      # Compile TypeScript
pnpm --filter api test       # Tests
```
- Importaciones de `@[scope]/core` para tipos compartidos
- Nunca importa de `@[scope]/ui`

### packages/ui (Biblioteca Componente)
```bash
pnpm --filter ui dev         # Storybook
pnpm --filter ui build       # Build for consumption
pnpm --filter ui test        # Component tests
```
- Exportaciones vía package.json `exports` sobre el terreno
- Usos `tsup` o `unbuild` para la compilación

### packages/core (Business Logic)
```bash
pnpm --filter core build     # Compile
pnpm --filter core test      # Unit tests
```
- TipoScript puro, sin dependencias de marco
- Exportaciones de tipos, validadores, constantes

## Cross-Package Imports

```typescript
// Correct: use workspace package name
import { Button } from '@[scope]/ui';
import { formatDate } from '@[scope]/utils';
import type { User } from '@[scope]/core';

// Wrong: never use relative paths across packages
import { Button } from '../../packages/ui/src/Button';
```

## Construir y probar comandos

```bash
# Root commands (run across all packages)
pnpm build                   # Build all packages (respects dependency order)
pnpm test                    # Test all packages
pnpm lint                    # Lint all packages
pnpm typecheck               # Type-check all packages
pnpm dev                     # Dev mode for all apps

# Single package
pnpm --filter [package] [command]

# With dependencies
pnpm --filter [package]... build   # Build package and its deps

# Turbo-specific
turbo run build --filter=web       # Build web and dependencies
turbo run test --affected          # Test only affected packages
```

## Naming Conventions

- Nombres de paquete: `@[scope]/package-name` (kebab-case)
- Importaciones internas: Siempre utilice el nombre del paquete, nunca caminos relativos
- Tipos compartidos: Definer `@[scope]/core/types/`
- Ganchos compartidos: Define en `@[scope]/ui/hooks/` si la UI está relacionada, `@[scope]/core/hooks/` de otra manera

# Notas importantes

- Siempre corre `pnpm install` desde la raíz (nunca dentro de un paquete)
- Los cambios en los paquetes compartidos pueden afectar a múltiples aplicaciones — prueba en general
- Turbo caches construye; corre `turbo run build --force` a bypass cache
- Al agregar un nuevo paquete, actualizar `pnpm-workspace.yaml`
- El CI debería usar `turbo run test --affected` para construcciones más rápidas
- Nunca ponga secretos en paquetes compartidos; manténgalos en app-level `.env`
