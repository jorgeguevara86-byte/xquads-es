# CLAUDE.md — Proyecto de microservicios

## Project Overview

- No me digas.
- **Descripción:** [Descripción del sistema]
- **Tipo:** Arquitectura de microservicios
- **Deployment:** [Docker / Kubernetes / Cloud Run / ECS]
- **Estatus:** [Desarrollo / Estadio / Producción]

## Service Architecture

```
services/
  api-gateway/ # Punto de entrada, enrutamiento, validación de auth
  user-service/ # Gestión y autenticación del usuario
  order-service/ # Procesamiento y gestión de pedidos
  payment-service/ # Tratamiento de pagos
  notification-service/ # Correo electrónico, SMS, notificaciones de empuje
  shared/
    proto/ # Protocolo definiciones de amortiguación (si GRPC)
    tipos/ # Tipos de script compartidos
    eventos / # Definiciones de esquemas de eventos
infrastructure/
  docker / # Docker Compose archivos
  k8s/ # Kubernetes manifiesta
  terraform/ # Infraestructura como código
```

## Tech Stack

Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|-------|-----------|-------|
TENCIÓN Idioma TENIDO TipoScript / Node.js Silencio Todos los servicios Silencio
Silencio Silencio Silencio Express / Acelerar Silencioso HTTP manipuladores Silencio
Silencio Comunicación Silencio REST + Evento impulsado por Silencio sincronización + asinc Silencio
Silencio Mensaje Broker Silencio RabbitMQ / Kafka Silencio eventos de Async Silencio
Silenciosos Base de Datos Silencio PostgreSQL Silencio Per-service DB Silencio
Silencio Cache Silencio Redis Silencioso sesión, tarifa limitante 
Silencio Container Silencio Docker Silencio Todos los servicios containerizzate Silencio
Silencioso Orquestación Silencio Docker Compuesto / K8s Silencio Local / Producción Silencioso
TEN API Docs TEN OpenAPI 3.0 TEN Por-servicio spec TEN

## Service Boundaries

### Normas de propiedad
- Cada servicio posee sus datos (base de datos, caché, archivos)
- No hay acceso directo a bases de datos entre servicios
- Toda la comunicación a través de APIs o eventos definidos
- Cada servicio tiene su propio depósito o paquete de espacio de trabajo

#### Service Template
Cada servicio sigue esta estructura:
```
service-name/
  src/
    rutas / # HTTP route handlers
    servicios / # lógica empresarial
    repositorios/ # capa de acceso a datos
    events/
      editores/ # Publicación de eventos
      suscriptores/ # Consumo de eventos
    middleware/ # Auth, validation, logging
    tipos/ # Tipos de servicio específicos
  tests/
    unidad / # pruebas de unidad
    integración/ # Pruebas de integración (con BD)
  Dockerfile # Definición de contenedor
  openapi.yaml            # Especificación de API
  package.json
  tsconfig.json
```

## API Contracts

### REST Conventions
- URL de base: `/{service-name}/api/v{version}/`
- Usa sustantivos plurales: `/users`, `/orders`, `/payments`
- Métodos HTTP: GET (read), POST (create), PUT (actual actualización), PATCH (partial), DELETE
- Respuesta al desarrollo: `{ "data": ..., "error": null, "meta": { "page": 1, "total": 100 } }`
- Formato de error: `{ "error": { "code": "USER_NOT_FOUND", "message": "...", "details": [] } }`

### API Versioning
- Versión basada en URL: `/api/v1/`, `/api/v2/`
- Soporte N-1 versiones (actual + anterior)
- Cabeceras de deprecación: `Sunset: <date>`, `Deprecation: true`

### OpenAPI Specification
- Cada servicio debe tener un `openapi.yaml` en la raíz
- Tipos de tipoScript autogenerados de OpenAPI spec
- Validar las solicitudes contra el esquema en el middleware

## Inter-Service Communication

### Synchronous (HTTP/gRPC)
- Usado para: consultas en tiempo real, user-facing Solicitudes
- Interruptor de circuito: Requiere en todas las llamadas externas (3 fallos = abiertos)
- Tiempo de salida: 5 segundos por defecto, 30 segundos para operaciones largas
- Retrocede: 3 intentos con retroceso exponencial (100ms, 200ms, 400ms)

## Asincrónico (Eventos)
- Se utiliza para: cambios estatales, notificaciones, sincronización de datos
- Nombramiento de eventos: `{service}.{entity}.{action}` (por ejemplo, `order.payment.completed`)
- Esquema de eventos: JSON Schema con campo de versión
- Idempotencia: Todos los manipuladores del evento deben ser idempotentes
- Carácter de carta muerta: Requerido para todos los consumidores

### Event Schema
```typescript
interface DomainEvent<T> {
  id: string;              // UUID v4
  type: string;            // order.payment.completed
  source: string;          // payment-service
  version: string;         // 1.0.0
  timestamp: string;       // ISO 8601
  correlationId: string;   // Request trace ID
  data: T;                 // Event-specific payload
}
```

## Deployment Patterns

### Local Development
```bash
docker-compose up -d       # Start all services
docker-compose up api      # Start specific service
docker-compose logs -f     # Follow logs
docker-compose down        # Stop all
```

### Environment Configuration
- `.env.local` por servicio para el desarrollo local
- Variables de medio ambiente inyectadas en tiempo de ejecución (nunca hornadas en imágenes)
- Los vars obligatorios definidos en cada servicio `.env.example`

### Health Checks
Cada servicio expone:
- `GET /health` — Viviencia básica (retornos 200)
- `GET /health/ready` — Lectura (comprueba DB, cache, dependencias)
- `GET /health/detailed` - Estado completo con salud de dependencia

## Testing Strategy

```bash
# Per-service commands
npm test                    # Unit tests
npm run test:integration    # Integration (requires Docker)
npm run test:contract       # Consumer-driven contract tests
npm run test:e2e            # End-to-end (full system)
```

### Niveles de prueba
Silencio Silencio Silencio Silencioso Silencio Silencio
|-------|-------|-------------|
Silencio , Unidad Silencioso function/class Silencio Todo mocked Silencio
tención Integración Silencioso Servicio + DB ANTE DB Real, servicios simulados
Silencioso Contrato Silencioso Servicio API forma Silencioso Pact o similar 
Silencio E2E Silencio Flujo de petición completa Silencio Todos los servicios que se ejecutan Silencio

## Comandos comunes

```bash
# Development
docker-compose up -d                    # Start infrastructure
npm run dev --workspace=user-service    # Dev mode for one service

# Testing
npm test --workspaces                   # Test all services
npm run test:integration --workspace=order-service

# Building
docker build -t user-service:latest ./services/user-service

# Database
npm run migrate --workspace=user-service     # Run migrations
npm run seed --workspace=user-service        # Seed data
```

# Notas importantes

- Nunca comparta bases de datos entre servicios, cada servicio posee sus datos
- Use IDs de correlación para el rastreo distribuido en los servicios
- Iniciar sesión en formato JSON estructurado para la agregación (ELK/Datadog)
- Mantener los servicios pequeños y enfocados - si un servicio crece demasiado grande, dividirlo
- Usar banderas de características para la implantación gradual en los servicios
- Prueba siempre la compatibilidad al revés cuando cambia el esquema de eventos
