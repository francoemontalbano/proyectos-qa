# Testing manual — Juego Lumbricina

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre Lumbricina, el juego de Proyecto Nahual. Revisé sus movimientos, colisiones, pastillas, niveles y paneles de información, y documenté los defectos en Mantis.

## Métricas

Conté los registros del CSV por versión: un mismo escenario repetido en otra versión cuenta otra vez. Tomé como `OK` solo los resultados escritos como `OK`. La otra columna reúne diferencias y resultados descriptivos; no equivale por sí sola a una cantidad de bugs.

| Versión | Casos | OK | Con diferencias u otro resultado descriptivo |
| :--- | ---: | ---: | ---: |
| v1 | 100 | 54 | 46 |
| **Total** | **100** | **54** | **46** |

| Severidad registrada | Reportes de bugs |
| :--- | ---: |
| bloqueo | 4 |
| mayor | 38 |
| menor | 3 |
| **Total** | **45** |

Entre los 46 resultados descriptivos están TC49–52: la ausencia de la pastilla naranja impidió comprobar esos escenarios. En los reportes correspondientes figura la gravedad `bloqueo`.

## Caso de prueba de ejemplo

**TC94 — Validar consumir 2 veces pastilla verde**

| Campo | Detalle |
| :--- | :--- |
| ID | 94 |
| Versión | v1 |
| Precondiciones | Ingresar al juego<br>Visualizar Lumbricina en el medio de la pantalla |
| Datos de entrada | Dos pastillas verdes, consumidas una después de la otra. |
| Pasos | 1- Consumir una pastilla verde<br>2- Jugar hasta que aparezca otra pastilla verde<br>3- Consumir otra pastilla verde |
| Resultado esperado | Al consumir la primera pastilla verde, la tecla izquierda mueve a Lumbricina hacia la derecha y <br>la tecla derecha la mueve hacia la izquierda. Las teclas arriba y abajo mantienen su funcionamiento<br>normal. Al consumir la segunda pastilla verde, se elimina la inversión y las teclas izquierda/derecha<br> vuelven a funcionar normalmente. |
| Resultado obtenido | Al consumir la primera pastilla verde, la tecla arriba mueve a Lumbricina hacia abajo y la tecla abajo la mueve hacia arriba. Luego de consumir la segunda pastilla verde, Lumbricina vuelve a moverse hacia arriba al presionar la tecla arriba. |
| Estado registrado del caso | Abierto |

Conservo el estado del CSV. «Abierto» o «Cerrado» es el estado registrado del caso; no lo uso para decidir si el resultado fue `OK`.

Fuente: [matriz de casos](Test%20Case%20-%20Lumbricina%20-%20Franco.csv). Los datos de entrada del ejemplo salen de sus pasos y precondiciones.

## Bugs de ejemplo

Elegí reportes con mayor severidad registrada y pasos concretos para mostrar el problema. Mantengo la severidad del archivo.

### Bug 0000083 — La pastilla naranja no aparece en v1

| Campo | Detalle |
| :--- | :--- |
| Severidad | bloqueo |
| Versión | v1 |
| Caso relacionado | TC49 |

**Precondiciones:** Ingresar al juego Visualizar Lumbricina en el medio de la pantalla

**Pasos para reproducir**

1. Visualizar pastilla naranja en el mapa

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El juego muestra una pastilla naranja en cualquier lugar del mapa |
| Resultado obtenido | No se visualiza la pastilla naranja en el mapa, ya que no existe en esta versión |

[Ver incidencia en Mantis](https://mantis.pakova.org/view.php?id=83)

### Bug 0000072 — Consumir una pastilla negra no termina la partida

| Campo | Detalle |
| :--- | :--- |
| Severidad | mayor |
| Versión | v1 |
| Caso relacionado | TC42 |

**Precondiciones:** Ingresar al juego Visualizar Lumbricina en el medio de la pantalla

**Pasos para reproducir**

1. Visualizar pastilla negra en la pantalla
2. Moverse hacia la pastilla negra
3. Consumir pastilla negra
4. Verificar estado del juego

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El juego finaliza mostrando Game Over |
| Resultado obtenido | El juego no finaliza, al consumir la pastilla negra permite seguir jugando como si no hubiese consumido ninguna pastilla. |

[Ver incidencia en Mantis](https://mantis.pakova.org/view.php?id=72)

### Bug 0000209 — La pastilla verde invierte arriba/abajo en lugar de izquierda/derecha

| Campo | Detalle |
| :--- | :--- |
| Severidad | mayor |
| Versión | v1 |
| Caso relacionado | TC94 |

**Precondiciones:** Ingresar al juego Visualizar Lumbricina en el medio de la pantalla

**Pasos para reproducir**

1. Consumir una pastilla verde
2. Jugar hasta que aparezca otra pastilla verde
3. Consumir otra pastilla verde

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | Al consumir la primera pastilla verde, la tecla izquierda mueve a Lumbricina hacia la derecha y la tecla derecha la mueve hacia la izquierda. Las teclas arriba y abajo mantienen su funcionamiento normal. Al consumir la segunda pastilla verde, se elimina la inversión y las teclas izquierda/derecha vuelven a funcionar normalmente. |
| Resultado obtenido | Al consumir la primera pastilla verde, la tecla arriba mueve a Lumbricina hacia abajo y la tecla abajo la mueve hacia arriba. Luego de consumir la segunda pastilla verde, Lumbricina vuelve a moverse hacia arriba al presionar la tecla arriba. |

[Ver incidencia en Mantis](https://mantis.pakova.org/view.php?id=209)

Fuente: [archivo de bugs](Bugs%20-%20Lumbricina%20-%20Franco.csv).

## Técnicas aplicadas

- **Partición de equivalencia:** probé nombres del Highscore con números, caracteres especiales, mayúsculas, minúsculas, espacios, tildes y ñ (TC77–86, v1).
- **Análisis de valores límite:** probé nombres de 30 y 31 caracteres frente al máximo de 30 del Highscore (TC74–75, v1).
- **Validación de entrada vacía:** dejé el nombre del Highscore vacío y comprobé el nombre por defecto «Alguien» (TC76, v1).
- **Transiciones de estado:** probé cambios de nivel (TC53–70 y TC87, v1) y Game Over al consumir una pastilla negra (TC42, v1).
- **Secuencias de acciones:** probé combinaciones de pastillas y el consumo de dos verdes consecutivas (TC91–100, v1).

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
