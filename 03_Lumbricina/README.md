# QA Test Repository - Juego Lumbricina

## Descripción
Repositorio de documentación de testing, diseño de casos de prueba y reporte de defectos para la aplicación web interactiva del juego "Lumbricina" de Proyecto Nahual.

## Aplicación bajo prueba
Videojuego basado en ciclos de movimiento por niveles, mecánicas de colisión, remapeo dinámico de controles y un sistema aleatorio de aparición de pastillas con efectos sobre la velocidad, puntaje e integridad del personaje.

## Alcance del Testing
- **Módulo de Movimiento y Colisiones:** Validación de inicio de nivel, colisiones físicas (paredes, cuerpo, obstáculos) y la excepción de inmunidad temporal (pastilla blanca).
- **Módulo de Pastillas (Mecánicas de Juego):** Verificación de lógica de puntajes, alteración de velocidad (azul, dorada), inversión de controles (verde), decremento de longitud (violeta), multiplicadores (naranja) y estados de Game Over (negra).
- **Módulo de Progresión y Niveles:** Transición automática de mapa cada 500 puntos, reinicio de ciclos tras el nivel 5 y cambios estructurales de obstáculos.
- **Módulo de Highscore y Debug:** Validación de ordenamiento top 5, control de strings (límite de 30 caracteres), manejo de valores por defecto ("Alguien") e integridad de los paneles de debug (Largo, Velocidad, Tiempo de bonus).

## Archivos Incluidos
- `Test Case - Lumbricina - Franco.csv` : Matriz de 100 casos de prueba de v1, con precondiciones, pasos, resultado esperado y resultado obtenido.
- `Bugs - Lumbricina - Franco.csv` : Exportación actualizada de 45 incidencias asignadas a `francoemontalbano` en Mantis, con pasos, resultados, TC relacionado y enlace al reporte original.

## Ejecución y trazabilidad
- Actualización de la documentación: **11/11/2026**.
- En **Resultado Obtenido**, `OK` indica que el resultado coincide con el esperado. Cuando hay una diferencia o una ejecución bloqueada, se describe lo observado.
- **Estado del test case** conserva el estado de gestión de la plantilla (`Abierto`); no representa el resultado de la ejecución.
- La matriz incluye los resultados actualizados de los TC91–100 y el esperado corregido del TC94 según la especificación de la pastilla verde.
- Se volvió a ejecutar el **TC88** en v1: el Debug mostró largo 3 antes y después de consumir una pastilla roja. Se corrigió el `OK` anterior; el comportamiento coincide con el defecto de longitud del [reporte #31](https://mantis.pakova.org/view.php?id=31).
- Los CSV reemplazan las versiones anteriores y mantienen sus nombres para conservar los enlaces del repositorio. Pueden abrirse con Excel o Google Sheets.

## Responsable
Franco Montalbano

## Documentación de Referencia
- **Especificaciones del Proyecto:** [Proyecto Nahual - Especificaciones Lumbricina](https://nahual.github.io/qc-lumbricina/especificaciones.html)
- **Aplicación en Producción (App Under Test):** [Sitio de Pruebas - Juego Lumbricina](https://nahual.github.io/qc-lumbricina/?v=1)
