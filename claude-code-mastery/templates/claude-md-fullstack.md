# CLAUDE.md — Proyecto de personal completo (Next.js + Reaccionar)

## Project Overview

- No me digas.
- **Descripción:** [Descripción de la solicitud]
- **Tipo:** Aplicación web de Fullstack
- ¿Qué? Next.js (App Router)
- **Estatus:** [Desarrollo / Estadio / Producción]

## Tech Stack

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|-------|-----------|---------|
TEN ANTERIOR FORMULARIO Next.js Silencios tóxicos
Silencioso Biblioteca de la UI
Silencio Idioma Silencio TipoScript Silencio 5.x Silencio
Silencioso Silencioso Silencioso Tailwind CSS Silencio 4.x Silencio
Silencio UI Componentes Silencio shadcn/ui Silencio , más reciente ,
Silencioso Estado (cliente) Silencio Zustand Silencio 5.x Silencio
← Datos sobre el secuestro Silencioso TanStack Query ←
Silencioso Base de Datos Silencio PostgreSQL Silencio via Supabase Silencio
Silencio Silencio Silencio Supabase Auth Silencio — Silencio
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio .
Silencio Testing ← Jest + React Testing Library ←
← Silencioso Silencio ESLint + Más alto Silencio — Silencio

## Directory Structure

```
src/
  app/ Next.js Páginas de la página
    (auth)/ # Auth route group (login, register)
    (dashboard)/ # Grupo de ruta de panel
    api/ # API route handlers
    layout.tsx #
    página.tsx # landing page
  components/
    ui/ shadcn/ui componentes básicos
    compartidos / # Componentes compuestos compartidos
    características / # Componentes específicos de la alimentación
  lib/
    supabase/ # Supabase customer settings
    utils.ts # funciones de Utilidad
    constantes.ts # constantes de aplicación
  ganchos / # ganchos de reacción personalizada
  tiendas / tiendas de Zustand
  tipos/ # TipoScript tipo definiciones
  estilos / # Estilos globales, Tailwind config
```

## Code Standards

### Components
- Utilizar componentes de función con interfaces TipoScript para propulsores
- Preferencias de exportación: `export function Button() {}` no `export default`
- Pruebas de componentes de colocate: `Button.tsx` + `Button.test.tsx`
- Componentes separados del servidor (por defecto) de componentes del cliente (`'use client'`)
- Mantener componentes bajo 200 líneas; extraer lógica en ganchos

#### Naming Conventions
- Componentes: PascalCase (`UserProfile.tsx`)
- Ganchos: camelloCaso con `use` prefijo (prefijo)`useAuth.ts`)
- Utilidades: camelloCase (`formatDate.ts`)
- Tipos: PascalCase con sufijos descriptivos (`UserProfileProps`, `AuthState`)
- Rutas de API: maletín con hyphens (`/api/user-profile/route.ts`)
- Constantes: SNAKE_CASE (SNAKE_CASE)`MAX_RETRY_COUNT`)

### Servidor vs Componentes de Cliente
- ** Componentes de servidor** (por defecto): búsqueda de datos, acceso a bases de datos, lógica sensible
- ** Componentes de localización** (`'use client'`): Interactividad, navegador API, estado, efectos
- Nunca importa server-only módulos en componentes cliente
- Pase accesorios serializable desde componentes servidor a cliente

### API Patterns
- Rutas de API en `src/app/api/` utilizando los Handlers de la Ruta
- Validar todas las entradas con los esquemas de Zod
- Formas de respuesta consistentes de retorno: `{ data, error, meta }`
- Use códigos de estado de propiedad HTTP (200, 201, 400, 401, 404, 500)
- Errores de mango con try/catch, nunca exponer errores internos

## State Management
**Estado de servidor:** Consulta de TanStack para todos los datos de API (caching, revalidation)
**Estado de cliente:** Zustand for UI state (modals, sidebars, preferences)
- ** Estado del formo:** Reactar formulario de gancho + validación de Zod
- Nunca duplicar el estado del servidor en las tiendas de clientes

## Testing requirements

- Ejecute todas las pruebas: `npm test`
- Corre con cobertura: `npm test -- --coverage`
- Cobertura mínima: 80% para lógica empresarial, 60% para componentes
- Archivo de prueba: `*.test.ts` o `*.test.tsx` co-located con fuente
- Uso `@testing-library/react` para los ensayos de componentes
- Mock Supabase cliente en pruebas, nunca golpeó la base de datos real

## Git Conventions

- **Comités:**`feat:`, `fix:`, `docs:`, `chore:`, `test:`, `refactor:`)
- **Branches:** `feat/description`, `fix/description`, `chore/description`
- ** Títulos de la RPDC:** Lo mismo que los compromisos convencionales
- Reference issue/story: `feat: add user profile page [STORY-1.2]`

## Comandos comunes

```bash
npm run dev          # Start development server (localhost:3000)
npm run build        # Production build
npm run start        # Start production server
npm test             # Run Jest tests
npm run lint         # ESLint check
npm run lint:fix     # ESLint auto-fix
npm run typecheck    # TypeScript type checking
npm run format       # Prettier formatting
```

## Environment Variables

- `.env.local` para el desarrollo local (gitignored)
- `.env.example` como plantilla (compromiso)
- Required: `NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- Solo servidor: `SUPABASE_SERVICE_ROLE_KEY` (nunca prefijo con `NEXT_PUBLIC_`)

## Error Handling

```typescript
// API route pattern
export async function GET(request: Request) {
  try {
    const data = await fetchData();
    return NextResponse.json({ data });
  } catch (error) {
    console.error('GET /api/resource failed:', error);
    return NextResponse.json(
      { error: 'Failed to fetch resource' },
      { status: 500 }
    );
  }
}
```

# Notas importantes

- Siempre chequeo `npm run typecheck` antes de comprometerse
- Nunca guardes secretos en client-side código o `NEXT_PUBLIC_` variables
- Uso `loading.tsx` y `error.tsx` para route-level loading/error estados
- Preferir acciones para mutaciones sobre las rutas de API cuando sea posible
