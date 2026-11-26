# Arquitectura

## Principios
1. **Simple primero.** No agregar capas "por si acaso".
2. **La lógica que importa se prueba sin UI.** Las reglas de rachas y estadísticas son funciones puras.
3. **Cada feature en su carpeta.** Lo que cambia junto vive junto.

## Tecnologías
| Necesidad | Elección | Por qué |
|---|---|---|
| UI | SwiftUI | Nativo y declarativo, con Previews |
| Estado | `@Observable` | Reemplazo moderno de `ObservableObject` |
| Persistencia | SwiftData | Integrado con SwiftUI (`@Query`) y sin dependencias |
| Gráficas | Swift Charts | Nativo |
| Tests | Swift Testing (`@Test`, `#expect`) | Framework moderno de Apple |

Sin dependencias externas en la v1.

## Estructura de carpetas
```
testClaude/MyApp/
├── MyApp.swift            ← punto de entrada; configura el ModelContainer
├── Models/                ← modelos SwiftData (@Model)
│   ├── Habit.swift
│   └── Completion.swift
├── Domain/                ← lógica pura, sin SwiftUI ni SwiftData
│   ├── StreakCalculator.swift
│   └── StatsCalculator.swift
├── Features/
│   ├── HabitList/         ← F1 y F2
│   ├── HabitForm/         ← crear y editar (F1)
│   ├── HabitDetail/       ← rachas (F2)
│   └── Stats/             ← gráfica (F3)
└── Shared/                ← componentes y helpers reutilizables
```

## Modelo de datos
- `Habit`: `name`, `emoji`, `colorName`, `createdAt`, `completions` (relación 1:N, borrado en cascada).
- `Completion`: `day` (el **inicio del día** en el calendario del usuario) y `habit`.
  Un hábito tiene como máximo una `Completion` por día.

## Reglas de diseño
- **Las vistas** leen datos con `@Query` y escriben con `modelContext`. Si una vista acumula lógica, esa lógica se mueve a `Domain/` o a un `@Observable`.
- **`Domain/` no importa SwiftUI ni SwiftData.** Recibe valores simples (por ejemplo `[Date]`) y regresa resultados.
- **Fechas:** toda función que dependa de "hoy" recibe `today: Date` y `calendar: Calendar` como parámetros, para que los tests controlen el tiempo. Nunca llamar `Date()` dentro de `Domain/`.
- **Previews:** usan un `ModelContainer` en memoria con datos de ejemplo (helper en `Shared/`).

## Tests
- Target `MyAppTests` (se crea en el Paso 5).
- Prioridad: `Domain/` al 100%, sobre todo los casos borde de fechas (cambio de mes, días saltados, hoy sin marcar).

## Decisiones
| # | Decisión | Motivo |
|---|---|---|
| 1 | Solo iPhone en la v1 | Reducir variables mientras se aprende el flujo |
| 2 | SwiftData en lugar de Core Data | Menos código, integración directa con SwiftUI |
| 3 | Sin MVVM obligatorio | `@Query` ya resuelve la lectura; un ViewModel solo si hay lógica real |
