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

## Trabajo realizado

- Armé los casos de prueba para v1 a partir de la narrativa del juego.
- Probé los efectos de las pastillas por separado y en distintas combinaciones.
- Comparé los valores del Debug con el comportamiento de Lumbricina.
- Registré los resultados en la matriz y reporté los defectos en Mantis.

## Resultados

En la matriz registré **54 casos OK y 46 con resultados descriptivos**. En estos últimos detallé las diferencias observadas y los casos que no pude completar por el comportamiento del juego.

Los reportes incluyen problemas de longitud, velocidad, controles, puntaje y duración de las pastillas. Dejé los enlaces a Mantis en el archivo de bugs para poder consultar cada incidencia.

## Responsable

Franco Montalbano
