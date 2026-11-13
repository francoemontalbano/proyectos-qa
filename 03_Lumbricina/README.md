# Testing manual — Juego Lumbricina

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre Lumbricina, el juego de Proyecto Nahual. Revisé sus movimientos, colisiones, pastillas, niveles y paneles de información, y documenté los defectos encontrados.

## Métricas

| Versión | Casos | OK | Con diferencias u otro resultado descriptivo |
| :--- | ---: | ---: | ---: |
| v1 | 100 | 53 | 46 + 1 pendiente |
| **Total** | **100** | **53** | **46 + 1 pendiente** |

En v1 registré 53 casos OK, 46 con diferencias u otro resultado descriptivo y 1 pendiente de verificar (TC33).<br>
El CSV solo incluye v1, así que no permite comparar una tendencia entre versiones.

| Severidad registrada | Reportes de bugs |
| :--- | ---: |
| bloqueo | 4 |
| mayor | 38 |
| menor | 3 |
| **Total** | **45** |

Reporté problemas de longitud, velocidad, controles, puntaje y duración de las pastillas. Entre los 46 resultados descriptivos están TC49–52: la ausencia de la pastilla naranja impidió comprobar esos escenarios; sus reportes tienen gravedad `bloqueo`.

## Caso de prueba de ejemplo

**TC94 — Validar consumir 2 veces pastilla verde**

**Precondiciones**

- Ingresar al juego.
- Visualizar Lumbricina en el medio de la pantalla.

| Campo | Detalle |
| :--- | :--- |
| ID | 94 |
| Versión | v1 |
| Datos de entrada | Dos pastillas verdes, consumidas una después de la otra. |
| Pasos | 1- Consumir una pastilla verde<br>2- Jugar hasta que aparezca otra pastilla verde<br>3- Consumir otra pastilla verde |
| Resultado esperado | Al consumir la primera pastilla verde, la tecla izquierda mueve a Lumbricina hacia la derecha y <br>la tecla derecha la mueve hacia la izquierda. Las teclas arriba y abajo mantienen su funcionamiento<br>normal. Al consumir la segunda pastilla verde, se elimina la inversión y las teclas izquierda/derecha<br> vuelven a funcionar normalmente. |
| Resultado obtenido | Al consumir la primera pastilla verde, la tecla arriba mueve a Lumbricina hacia abajo y la tecla abajo la mueve hacia arriba. Luego de consumir la segunda pastilla verde, Lumbricina vuelve a moverse hacia arriba al presionar la tecla arriba. |

Fuente: [matriz de casos](Test%20Case%20-%20Lumbricina%20-%20Franco.csv).

## Bugs de ejemplo

### Bug 0000072 — Consumir una pastilla negra no termina la partida

| Campo | Detalle |
| :--- | :--- |
| Severidad | mayor |
| Versión | v1 |
| Caso relacionado | TC42 |

**Precondiciones**

- Ingresar al juego.
- Visualizar Lumbricina en el medio de la pantalla.

**Pasos para reproducir**

1. Visualizar pastilla negra en la pantalla
2. Moverse hacia la pastilla negra
3. Consumir pastilla negra
4. Verificar estado del juego

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El juego finaliza mostrando Game Over |
| Resultado obtenido | El juego no finaliza, al consumir la pastilla negra permite seguir jugando como si no hubiese consumido ninguna pastilla. |

### Bug 0000209 — La pastilla verde invierte arriba/abajo en lugar de izquierda/derecha

| Campo | Detalle |
| :--- | :--- |
| Severidad | mayor |
| Versión | v1 |
| Caso relacionado | TC94 |

**Precondiciones**

- Ingresar al juego.
- Visualizar Lumbricina en el medio de la pantalla.

**Pasos para reproducir**

1. Consumir una pastilla verde
2. Jugar hasta que aparezca otra pastilla verde
3. Consumir otra pastilla verde

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | Al consumir la primera pastilla verde, la tecla izquierda mueve a Lumbricina hacia la derecha y la tecla derecha la mueve hacia la izquierda. Las teclas arriba y abajo mantienen su funcionamiento normal. Al consumir la segunda pastilla verde, se elimina la inversión y las teclas izquierda/derecha vuelven a funcionar normalmente. |
| Resultado obtenido | Al consumir la primera pastilla verde, la tecla arriba mueve a Lumbricina hacia abajo y la tecla abajo la mueve hacia arriba. Luego de consumir la segunda pastilla verde, Lumbricina vuelve a moverse hacia arriba al presionar la tecla arriba. |

Este reporte muestra cómo documenté los casos bloqueados TC49–52 por la ausencia de la pastilla naranja.

### Bug 0000083 — La pastilla naranja no aparece en v1

| Campo | Detalle |
| :--- | :--- |
| Severidad | bloqueo |
| Versión | v1 |
| Caso relacionado | TC49 |

**Precondiciones**

- Ingresar al juego.
- Visualizar Lumbricina en el medio de la pantalla.

**Pasos para reproducir**

1. Visualizar pastilla naranja en el mapa

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El juego muestra una pastilla naranja en cualquier lugar del mapa |
| Resultado obtenido | No se visualiza la pastilla naranja en el mapa, ya que no existe en esta versión |

Fuente: [archivo de bugs](Bugs%20-%20Lumbricina%20-%20Franco.csv).

## Técnicas aplicadas

- **Partición de equivalencia:** probé nombres del Highscore con números, caracteres especiales, mayúsculas, minúsculas, espacios, tildes y ñ (TC77–86, v1).
- **Análisis de valores límite:** probé nombres de 30 y 31 caracteres frente al máximo de 30 del Highscore (TC74–75, v1).
- **Validación de entrada vacía:** dejé el nombre del Highscore vacío y comprobé el nombre por defecto «Alguien» (TC76, v1).
- **Transiciones de estado:** probé cambios de nivel (TC53–70 y TC87, v1) y Game Over al consumir una pastilla negra (TC42, v1).
- **Secuencias de acciones:** probé combinaciones de pastillas y el consumo de dos verdes consecutivas (TC91–100, v1).

## Alcance de las pruebas

- Probé los movimientos y las colisiones contra paredes, obstáculos y el cuerpo de Lumbricina.
- Revisé los efectos de las pastillas sobre el largo, la velocidad, los controles y el puntaje, por separado y en distintas combinaciones.
- Probé la progresión de niveles, los cambios de estructura del mapa y el Highscore.
- Comparé los valores de largo, velocidad y duración de bonus del Debug con el comportamiento durante la partida.
- Armé los casos de v1 a partir de la narrativa y documenté los resultados y los defectos.

## Aplicación y referencias

- [Aplicación Lumbricina — v1](https://nahual.github.io/qc-lumbricina/?v=1)
- [Narrativa funcional](https://nahual.github.io/qc-lumbricina/especificaciones.html)

## Documentación

| Archivo | Contenido |
| :--- | :--- |
| [Casos de prueba](Test%20Case%20-%20Lumbricina%20-%20Franco.csv) | 100 casos de prueba de v1, con precondiciones, pasos y resultados. |
| [Reportes de bugs](Bugs%20-%20Lumbricina%20-%20Franco.csv) | 45 incidencias asignadas a francoemontalbano, con pasos y resultados. |

## Responsable

Franco Montalbano
