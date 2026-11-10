# CLAUDE.md — Proyecto de biblioteca / paquete

## Project Overview

- No me digas.
- **Descripción:** [Lo que hace esta biblioteca]
- **Tipo:** Reutilizable biblioteca / paquete npm
- **Registro:** npm (público / privado)
- **Estatus:** [Alpha / Beta / Stable]
- Versión actual:

## Tech Stack

Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|-------|-----------|-------|
Silencio Idioma Silencio TipoScript Silencio Modo de sistema habilitado Silencio
Silencio Bundler Silencio tsup / Rollup / Vite ← Doble ESM + salida CJS
Silencio Testing ← Vitest / Jest Silencioso Unidad + integración
← ← ESLint + Más alto Silencio reglas estrictas para el código de biblioteca ←
← Docs ← TipoDoc / TSDoc ← Docs de API generados por autos TEN

## API Surface

## Public Exports (src/index.ts)

Toda API pública se exporta desde el punto de entrada del paquete. Cada exportación es parte del
contrato público y sujeto a garantías de semver.

```typescript
// src/index.ts — the single source of truth for public API
export { createClient } from './client';
export { validate } from './validators';
export type { ClientOptions, ValidationResult } from './types';
```

# Interna vs Public #

Silencioso Directorio Silencio Visibilidad Silencio Semver Contrato
|-----------|-----------|----------------|
| `src/index.ts` Silencio PUBLIC Silencio Cambios de ruptura = gran golpe Silencio
| `src/` (non-exported) Silencio Silencio Silencio Puede cambiar libremente Silencio
| `src/internal/` Silencio Silencio nunca importa desde fuera
| `src/__tests__/` TEN ENTRE INTERNAL TENIDO Servicios de prueba, no enviados TEN

### Rules
- Nunca exportar directamente desde subdirectorios; siempre re-export a través de `src/index.ts`
- Prefijo de servicios internos con `_` o lugar en `src/internal/`
- Cada función pública debe tener comentarios TSDoc `@example` bloques
- Todos los tipos públicos deben exportarse explícitamente (sin exportaciones implícitas por inferencia)

## Backward Compatibility

#### Semver Rules
**MAJOR (X.0.0):** Removing exports, changing function signatures, renaming types
**MINOR (0.X.0):** Añadiendo nuevas exportaciones, añadiendo parámetros opcionales, nuevas características
**PATCH (0.0.X):** Fijaciones de errores, mejoras de rendimiento, documentación

## Lista de verificación de cambios de ruptura
Antes de cualquier golpe de versión principal:
- [ ] Documentar todos los cambios de ruptura en CHANGELOG.md
- Proporcione guía de migración
- [ ] Actualizar todos los ejemplos y documentación
[ ] Considerar el período de deprecación (marca deprecatada en menor, retirar en el próximo mayor)

#### Deprecation Pattern
```typescript
/**
 * @deprecated Use `createClientV2()` instead. Will be removed in v3.0.0.
 */
export function createClient(options: OldOptions): Client {
  console.warn('createClient is deprecated. Use createClientV2 instead.');
  return createClientV2(migrateOptions(options));
}
```

## Versioning

- Seguir [Versión Semántica 2.0.0](https://semver.org/)
- Uso `npm version patch|minor|major` para chocar
- Etiqueta: `git tag v1.2.3`
- Mantener CHANGELOG.md con [Mantenga un cambio](https://keepachangelog.com/) formato

## Testing Strategy

### Test Categories
* Pruebas de unidad*: Cada función pública, casos de borde, condiciones de error
- ** Pruebas de inversión:** Interacciones de módulos, real-world patrones de uso
** Pruebas de tipo:** Verificar tipos de tipoScript con `tsd` o `expect-type`
** Pruebas de captura:** Para salidas serializables (opcional)

### Coverage requirements
- API pública: cobertura de ramas 100%
- Servicios internos: 80% de cobertura mínima
- Inferencia tipo: probado con `expectTypeOf` afirmaciones

### Commands
```bash
npm test                  # Run all tests
npm test -- --coverage    # With coverage report
npm test -- --watch       # Watch mode during development
npm run test:types        # Type-level tests
```

## Documentation requirements

#### TSDoc on Every Public Export
```typescript
/**
 * Creates a new client instance with the given options.
 *
 * @param options - Configuration options for the client
 * @returns A configured client instance
 * @throws {ValidationError} If options are invalid
 *
 * @example
 * ```typescript
 * const client = createClient({ apiKey: 'xxx', timeout: 5000 });
 * const result = await client.query('hello');
 * ```
 */
export function createClient(options: ClientOptions): Client {
  // ...
}
```

### README Sections
- Instrucciones de instalación
- Ejemplo de inicio rápido
- Referencia de API (enlace a los docs generados)
- Tabla de opciones de configuración
- Guía de manejo de errores
- Guías de migración (para versiones importantes)

## Build Commands

```bash
npm run build             # Build for distribution (ESM + CJS)
npm run dev               # Watch mode for development
npm run lint              # Lint source code
npm run lint:fix          # Auto-fix lint issues
npm run typecheck         # TypeScript type checking
npm run docs              # Generate API documentation
npm run prepublishOnly    # Pre-publish checks (lint + test + build)
```

## Package.json Fields

```jsonc
{
  "name": "@scope/package-name",
  "version": "1.0.0",
  "type": "module",
  "main": "./dist/index.cjs",
  "module": "./dist/index.js",
  "types": "./dist/index.d.ts",
  "exports": {
    ".": {
      "import": "./dist/index.js",
      "require": "./dist/index.cjs",
      "types": "./dist/index.d.ts"
    }
  },
  "files": ["dist", "README.md", "CHANGELOG.md"],
  "sideEffects": false
}
```

# Notas importantes

- Siempre ejecute la suite de pruebas completa antes de publicar
- Nunca publicar con `--force` o `--no-git-checks`
- Quédate. `files` sobre el terreno en package.json mínimo (sólo buque dist/)
- Prueba el paquete localmente con `npm link` antes de publicar
- Las dependencias de los propios usuarios deben utilizar amplios rangos de versiones (`>=17.0.0`)
- Cuestiones de tamaño de la aglomeración: uso `bundlephobia` para comprobar antes de la liberación
