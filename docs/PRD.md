# PRD: Hábitos (v1)

## Problema
Quiero construir hábitos diarios (leer, hacer ejercicio, tomar agua) y me cuesta ser constante.
Necesito una forma rápida de marcar lo que hice hoy y ver mi constancia.

## Usuario
Una sola persona, en su iPhone. Sin cuentas ni sincronización.

## Objetivo de la v1
Registrar un hábito en menos de 10 segundos y marcarlo como hecho con un solo toque.

## Funcionalidades

### F1: Mis hábitos
- Ver la lista de hábitos.
- Crear un hábito con nombre (obligatorio), emoji y color.
- Editar y borrar hábitos (borrar pide confirmación).
- Si no hay hábitos, mostrar un estado vacío que invite a crear el primero.

### F2: Marcar hoy y rachas
- Marcar o desmarcar un hábito como hecho **hoy**, con un toque desde la lista.
- Cada hábito muestra su **racha actual**: días seguidos cumplidos hasta hoy.
  Si hoy todavía no se marca, la racha cuenta hasta ayer (no se "rompe" a medio día).
- En el detalle se ve también la **mejor racha** histórica.

### F3: Estadísticas
- Pantalla con una gráfica (Swift Charts) de los últimos 30 días: cuántos hábitos se cumplieron cada día.
- Porcentaje de cumplimiento de cada hábito en los últimos 30 días.

## Fuera de alcance (v1)
- Notificaciones o recordatorios
- Sincronización con iCloud y cuentas
- Widgets, Apple Watch, iPad, Mac y visionOS
- Frecuencias distintas a "diario" (por ejemplo, 3 veces por semana)
- Editar días pasados

## Criterios de terminado (para toda la v1)
- Funciona en el simulador de iPhone sin crashes.
- Los datos persisten al cerrar y abrir la app.
- La lógica de rachas y porcentajes tiene tests que pasan.
- Soporta modo oscuro y Dynamic Type.
