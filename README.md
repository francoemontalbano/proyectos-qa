# Portfolio de QA Manual — Franco Montalbano

Busco mi primera posición como QA manual (trainee/junior) y en este repo comparto mis prácticas de testing manual sobre aplicaciones de Proyecto Nahual. Diseñé casos de prueba, documenté resultados y reporté defectos. En Provinciano también trabajé en revisión cruzada con un compañero.

Proyecto Nahual es mi entorno de práctica y capacitación; estos proyectos no son experiencia laboral.

## Proyectos

| Proyecto | Alcance | Documentación |
| :--- | :--- | :--- |
| [Gestión de Contactos](01_Gestion_Contactos/) | Alta, listado, ordenamiento, edición y baja de contactos. | [Casos, bugs y resultados](01_Gestion_Contactos/README.md) |
| [Buscador Provinciano](02_Provinciano/) | Búsquedas, filtros, ordenamiento y revisión cruzada. | [Casos, bugs y resultados](02_Provinciano/README.md) |
| [Juego Lumbricina](03_Lumbricina/) | Movimientos, colisiones, pastillas, niveles, Highscore y Debug. | [Casos, bugs y resultados](03_Lumbricina/README.md) |

## Métricas globales

| Proyecto | Registros de casos | OK | Con diferencias u otro resultado descriptivo | Reportes de bugs |
| :--- | ---: | ---: | ---: | ---: |
| [Gestión de Contactos](01_Gestion_Contactos/README.md#métricas) | 168 | 107 | 61 | 62 |
| [Buscador Provinciano](02_Provinciano/README.md#métricas) | 347 | 32 | 315 | 276 |
| [Juego Lumbricina](03_Lumbricina/README.md#métricas) | 100 | 53 | 47 | 45 |

Conté registros por versión, no casos ni defectos únicos entre versiones.<br>
`OK` es la marca literal del resultado; los demás incluyen diferencias y pruebas que no pude completar.

## Cómo leer este repo

Para ver cómo trabajo sin abrir los CSV, dejé un caso completo y reportes de bugs en cada proyecto:

| Proyecto | Caso de prueba | Bugs de ejemplo |
| :--- | :--- | :--- |
| Gestión de Contactos | [Ver TC37](01_Gestion_Contactos/README.md#caso-de-prueba-de-ejemplo) | [Ver reportes](01_Gestion_Contactos/README.md#bugs-de-ejemplo) |
| Buscador Provinciano | [Ver TC149](02_Provinciano/README.md#caso-de-prueba-de-ejemplo) | [Ver reportes](02_Provinciano/README.md#bugs-de-ejemplo) |
| Juego Lumbricina | [Ver TC94](03_Lumbricina/README.md#caso-de-prueba-de-ejemplo) | [Ver reportes](03_Lumbricina/README.md#bugs-de-ejemplo) |

## Documentación

En cada carpeta están los casos de prueba y los reportes de bugs en CSV. Los README incluyen los enlaces a las aplicaciones y sus narrativas.

## Qué probé en cada proyecto

| Proyecto | Qué probé |
| :--- | :--- |
| [Contactos](01_Gestion_Contactos/README.md) | Campos obligatorios, formatos de mail, límites de caracteres y comparación entre versiones. |
| [Provinciano](02_Provinciano/README.md) | Combinaciones de Región y Nombre. También revisé los casos de Grego y él revisó los míos. |
| [Lumbricina](03_Lumbricina/README.md) | Límites del nombre en Highscore, combinaciones de pastillas, cambios de nivel y Game Over. |

## Contacto

- [LinkedIn](https://www.linkedin.com/in/francomontalbano/)
- Mail: [francoemontalbano@gmail.com](mailto:francoemontalbano@gmail.com)
- Ciudad: Rosario, Santa Fe, Argentina
