# ClaudeTest

App de práctica en SwiftUI para aprender a desarrollar con agentes de IA.
Producto: tracker de hábitos diarios. Lee `docs/PRD.md` (qué construimos) y
`docs/ARCHITECTURE.md` (cómo) antes de planear cualquier feature.
Las specs de cada feature están en `docs/features/`.

## Proyecto
- Xcode 27.2, proyecto en formato nuevo (`project.xcproj`, JSON).
- Proyecto: `testClaude/testClaude.xcodeproj` · Target y scheme: `MyApp`
- Código fuente: `testClaude/MyApp/`
- Plataforma de la v1: **solo iPhone**, iOS 27.2 o superior.
- Swift en modo 5 con aislamiento por defecto en `MainActor` y concurrencia accesible.
  Todo corre en el main actor salvo que se marque lo contrario (`nonisolated`, `@concurrent`).
- Aún no hay target de tests.

## Cómo compilar y probar
- Si las herramientas MCP de Xcode están disponibles, úsalas para compilar, correr tests y ver Previews.
- Si no, desde la terminal:
  `xcodebuild -project testClaude/testClaude.xcodeproj -scheme MyApp -destination 'generic/platform=iOS Simulator' build`
- Una tarea no está terminada hasta que compila sin errores ni warnings nuevos.

## Convenciones de código
- SwiftUI + `@Observable`. Nada de `ObservableObject` ni Combine.
- Las vistas no tienen lógica de negocio. La lógica va en tipos que se puedan probar sin UI.
- Cada vista nueva lleva su `#Preview` con datos de ejemplo.
- Nada de force unwrap (`!`) ni `try!` fuera de Previews y tests.
- Archivos pequeños: una vista o un tipo principal por archivo.
- No edites `project.xcproj` a mano salvo que se pida. Los archivos nuevos dentro de `MyApp/` se agregan solos al target.

## Git
- No hagas commit ni push sin que te lo pida.
- Mensajes de commit en español, en imperativo y descriptivos ("Agrega lista de hábitos", no "fix").
- Antes de dar algo por terminado, muestra un resumen de los archivos que cambiaste.

## Forma de trabajar
- Para tareas de más de un archivo, primero propón un plan y espera mi visto bueno.
- Si algo no está claro, pregunta antes de suponer.
- Estoy aprendiendo: explica brevemente las decisiones que no sean obvias.
