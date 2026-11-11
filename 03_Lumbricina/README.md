# Testing manual — Juego Lumbricina

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre Lumbricina, el juego de Proyecto Nahual. Revisé sus movimientos, colisiones, pastillas, niveles y paneles de información, y documenté los defectos en Mantis.

## Alcance de las pruebas

- Probé los movimientos y las colisiones contra paredes, obstáculos y el cuerpo de Lumbricina.
- Revisé los efectos de las pastillas sobre el largo, la velocidad, los controles y el puntaje.
- Probé la progresión de niveles y los cambios de estructura del mapa.
- Verifiqué el Highscore y los valores de largo, velocidad y duración de bonus en el Debug.

## Aplicación y referencias

- [Aplicación Lumbricina — v1](https://nahual.github.io/qc-lumbricina/?v=1)
- [Narrativa funcional](https://nahual.github.io/qc-lumbricina/especificaciones.html)
- [Casos de prueba originales — pestaña Franco](https://docs.google.com/spreadsheets/d/1utoftOwrg87gTWulDcDeu4qQMQgKW6SER25Uh3zIe3Q/edit?gid=1533384392)
- [Mantis — listado de incidencias](https://mantis.pakova.org/view_all_bug_page.php)

## Documentación

| Archivo | Contenido |
| :--- | :--- |
| [Casos de prueba](Test%20Case%20-%20Lumbricina%20-%20Franco.csv) | 100 casos de prueba de v1, con precondiciones, pasos y resultados. |
| [Reportes de bugs](Bugs%20-%20Lumbricina%20-%20Franco.csv) | 45 incidencias asignadas a francoemontalbano, con pasos, resultados y enlace a Mantis. |

Publiqué los archivos en CSV para consultarlos desde Excel o Google Sheets.

## Trabajo realizado

- Diseñé los casos de prueba y documenté los resultados obtenidos en v1.
- Actualicé los resultados de los TC91–100 y los reportes correspondientes en Mantis.
- Corregí el esperado del TC94 según la inversión de izquierda y derecha indicada en la narrativa de la pastilla verde.
- Volví a ejecutar el TC88: el Debug mostró largo 3 antes y después de consumir una pastilla roja. Corregí su OK anterior; el comportamiento coincide con el [reporte 31](https://mantis.pakova.org/view.php?id=31).
- Exporté las incidencias con sus IDs y enlaces para consultar los reportes originales.

## Resultados

Registré **54 resultados OK y 46 resultados descriptivos** en la matriz. En los resultados descriptivos detallo las diferencias observadas y las ejecuciones condicionadas o bloqueadas.

Uso `OK` cuando el resultado coincide con el esperado y describo lo observado en los demás casos. Conservo el estado de gestión del test case por separado del resultado de ejecución.

Actualicé la documentación el **11/11/2026**. En esa actualización revisé los TC91–100 y el TC88, y exporté las 45 incidencias de Mantis.

## Responsable

Franco Montalbano
