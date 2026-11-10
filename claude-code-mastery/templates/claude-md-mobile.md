# CLAUDE.md — Proyecto móvil (React Native)

## Project Overview

- No me digas.
- **Descripción:** [Lo que la aplicación hace]
- **Tipo:** Aplicación móvil
- **Framework:** Reactúa Native / Expo
- **Platforms: ** iOS + Android
- **Estatus:** [Desarrollo / Beta / Producción]

## Tech Stack

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|-------|-----------|---------|
Silencio Silencioso React Native tención 0.76.x Silencio
Silencioso Silencioso Expo SDK Silencio
Silencio Idioma Silencio TipoScript Silencio 5.x Silencio
Silencio Silencio Silencio React Navigation Silencio Silencio Silencio
Silencioso Estado (cliente) Silencio Zustand Silencio 5.x Silencio
← Datos sobre el secuestro Silencioso TanStack Query ←
Silencioso Silencioso NativeWind / StyleSheet Silencio — Silencio
Silencio Formas Silencio React Hook Form + Zod Silencio — Silencio
Silencio Silencio Silencio Supabase Auth Silencio — Silencio
← Testing ← Jest + React Native Testing Library ←


## Directory Structure

```
src/
  app/ # Expo Router screens (file-based routing)
    (tabs)/ # Tab navigator group
    (auth)/ # Pantallas de flujo Auth
    _layout.tsx # Diseño de raíz
  components/
    ui/ # Base UI components (Button, Input, Card)
    compartidos / # Componentes compuestos compartidos
    características / # Componentes específicos de la alimentación
  ganchos / # ganchos personalizados
  tiendas / tiendas de Zustand
  servicios/ # API servicios e integraciones externas
  lib/ # Bibliotecas de la Utilidad
  tipos/ # TipoScript tipo definiciones
  constantes/ # constantes de aplicación (colores, espaciamiento, config)
  activos/ # Imágenes, fuentes, animaciones
    images/
    fonts/
    animaciones/ # archivos Lottie
ios/ # Proyecto nativo de iOS
android/ # Android proyecto nativo
```

## Consideraciones de plataformas y específicas

### iOS
- Objetivo mínimo de despliegue: iOS 15.0
- Prueba tanto en iPhone como iPad si universal
- Manejar los conjuntos de zona segura con `SafeAreaView` o `useSafeAreaInsets()`
- Solicitar permisos con gracia (camera, ubicación, notificaciones)
- Evitación del teclado de manija para formas

### Android
- SDK mínimo: 24 (Android 7.0)
- Manejar el comportamiento del botón de la espalda con la navegación
- Prueba en varias densidades de pantalla (mdpi, hdpi, xhdpi, xxhdpi)
- Maneja permisos específicos para Android en `AndroidManifest.xml`
- Prueba de navegación de gestos vs botón de navegación

## Archivos de plataforma-específicos
```
Componente.tsx # Shared (default)
Componente.ios.tsx # IOS-sólo anular
Componente.android.tsx # Android-sólo anular
```

Uso `Platform.select()` para las diferencias menores:
```typescript
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  shadow: Platform.select({
    ios: { shadowColor: '#000', shadowOffset: { width: 0, height: 2 } },
    android: { elevation: 4 },
  }),
});
```

## Patrones de navegación

#### Stack Navigation
```typescript
// Use typed navigation
type RootStackParamList = {
  Home: undefined;
  Profile: { userId: string };
  Settings: undefined;
};
```

#### Tab Navigation
- Máximo 5 fichas
- Use iconos + etiquetas para la accesibilidad
- Insignia para los conteos de notificación

## Deep Linking
- Configurar el esquema URL: `myapp://`
- Manejo de enlaces universales (iOS) y enlaces de aplicaciones (Android)
- Prueba con `npx uri-scheme open myapp://profile/123`

## State Management

### Local State
- `useState` para component-scoped estado
- `useReducer` para la lógica compleja de componente

## Global State (Zustand)
- Persiste con `zustand/middleware` + AsyncStorage
- Esperar la hidratación antes de renderizar las pantallas protegidas
- Tiendas separadas por dominio (auth, preferencias, carrito)

### Server State (TanStack Query)
- Configurar soporte sin conexión con `onlineManager`
- Utilice actualizaciones optimistas para UX receptivo
- Set `staleTime` apropiadamente (más lento para el móvil para reducir el uso de datos)

## Comandos comunes

```bash
# Development
npx expo start             # Start Expo dev server
npx expo start --ios       # Open in iOS Simulator
npx expo start --android   # Open in Android Emulator
npx expo start --web       # Open in web browser

# Building
eas build --platform ios                 # iOS build
eas build --platform android             # Android build
eas build --platform all                 # Both platforms

# Testing
npm test                   # Run Jest tests
npm run test:e2e:ios       # E2E tests on iOS
npm run test:e2e:android   # E2E tests on Android

# Code Quality
npm run lint               # ESLint check
npm run typecheck          # TypeScript check
npm run format             # Prettier formatting

# Native
npx pod-install            # Install iOS CocoaPods
npx react-native link      # Link native modules (legacy)
```

## Build and Deploy

#### EAS Build
```bash
eas build:configure                      # Initial setup
eas build --profile development          # Development build
eas build --profile preview              # Internal testing
eas build --profile production           # Store submission
```

### Over-the-Air Updates
```bash
eas update --branch production           # Push OTA update
eas update --branch preview              # Preview update
```

## Testing Strategy

Silencio Silencio Silencio Silencio Silencio Silencio Silencio
|-------|------|--------|
Silenciosidad vivir Jest vivieron Hooks, servicios públicos, tiendas viv
Silencio Componente Silencio RNTL Silencio Componentes UI (render, interacción) Silencio
tención integración ← Jest + RNTL Silencio
Silencio E2E Silencio Detox/Maestro Silencio Viajes completos de usuario Silencio
Silencio Visual Silencio Storybook RN Silencio Componente catálogo Silencio

### Testing Tips
- Uso `@testing-library/react-native` sobre Enzyme
- Mock `react-native` módulos: `Animated`, `Platform`, etc.
- Prueba ambas plataformas al usar `Platform.select()`
- Uso `jest.useFakeTimers()` para las pruebas de animación
- Mock `AsyncStorage` para pruebas de la tienda

# Notas importantes

- Siempre prueba en dispositivos reales antes de la liberación (los indicadores pierden problemas de rendimiento)
- Mantenga el tamaño del paquete pequeño: lazy-load pantallas, optimización de imágenes
- Manejar el estado fuera de línea con gracia - acciones de cola para sincronización
- Siga las directrices de Apple HIG y Diseño de Materiales
- Nunca Dimensiones de código duro — use diseños sensibles con Dimensions/useWindowDimensions
- Prueba la accesibilidad con lectores de pantalla (VoiceOver en iOS, TalkBack en Android)
- Uso `react-native-reanimated` para animaciones de 60 fps (evitar API Animada para casos complejos)
- Manejar cambios de estado (en primer plano, primer plano) para la actualización de datos
