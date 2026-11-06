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
- `Test Case - Lumbricina - Franco.csv` : Matriz completa de diseño de casos de prueba.
- `Bugs - Lumbricina - Franco.csv` : Reporte detallado de defectos detectados durante los ciclos de ejecución.

## Responsable
Franco Montalbano

## Documentación de Referencia
- **Especificaciones del Proyecto:** [Proyecto Nahual - Especificaciones Lumbricina](https://nahual.github.io/qc-lumbricina/especificaciones.html)
- **Aplicación en Producción (App Under Test):** [Sitio de Pruebas - Juego Lumbricina](https://nahual.github.io/qc-lumbricina/?v=1)
