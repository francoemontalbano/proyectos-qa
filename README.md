# Portfolio de QA Manual — Franco Montalbano

En este repositorio reúno mis prácticas de testing manual sobre aplicaciones de Proyecto Nahual. Diseñé casos de prueba, documenté resultados y reporté defectos. En Provinciano también trabajé en revisión cruzada con un compañero.

Proyecto Nahual es mi entorno de práctica y capacitación; estos proyectos no son experiencia laboral.

## Proyectos

| Proyecto | Alcance | Documentación |
| :--- | :--- | :--- |
| [Gestión de Contactos](01_Gestion_Contactos/) | Alta, listado, ordenamiento, edición y baja de contactos. | [Casos, bugs y resultados](01_Gestion_Contactos/README.md) |
| [Buscador Provinciano](02_Provinciano/) | Búsquedas, filtros, ordenamiento y revisión cruzada. | [Casos, bugs y resultados](02_Provinciano/README.md) |
| [Juego Lumbricina](03_Lumbricina/) | Movimientos, colisiones, pastillas, niveles, Highscore y Debug. | [Casos, bugs y resultados](03_Lumbricina/README.md) |

## Métricas globales

| Proyecto | Registros de casos | OK | Con diferencias u otro resultado descriptivo | Reportes de bugs | Severidades registradas |
| :--- | ---: | ---: | ---: | ---: | :--- |
| [Gestión de Contactos](01_Gestion_Contactos/README.md#métricas) | 168 | 108 | 60 | 62 | Baja: 6; Media: 45; Alta: 11 |
| [Buscador Provinciano](02_Provinciano/README.md#métricas) | 347 | 33 | 314 | 276 | Media: 7; Alta: 167; Sin informar: 100; Baja: 2 |
| [Juego Lumbricina](03_Lumbricina/README.md#métricas) | 100 | 54 | 46 | 45 | mayor: 38; menor: 3; bloqueo: 4 |
| **Total** | **615** | **195** | **420** | **383** | Escalas conservadas por proyecto |

Conté todos los registros de las versiones disponibles, no escenarios únicos ni defectos únicos entre versiones. `OK` es una marca literal del resultado obtenido. Los otros 420 registros incluyen diferencias y pruebas que no se pudieron completar. No sumé `Alta` con `mayor`: son los valores de las escalas originales.

## Cómo leer este repo

Para ver cómo trabajo sin abrir los CSV, dejé un caso completo y reportes de bugs en cada proyecto:

| Proyecto | Caso de prueba | Bugs de ejemplo |
| :--- | :--- | :--- |
| Gestión de Contactos | [Ver TC37](01_Gestion_Contactos/README.md#caso-de-prueba-de-ejemplo) | [Ver reportes](01_Gestion_Contactos/README.md#bugs-de-ejemplo) |
| Buscador Provinciano | [Ver TC149](02_Provinciano/README.md#caso-de-prueba-de-ejemplo) | [Ver reportes](02_Provinciano/README.md#bugs-de-ejemplo) |
| Juego Lumbricina | [Ver TC94](03_Lumbricina/README.md#caso-de-prueba-de-ejemplo) | [Ver reportes](03_Lumbricina/README.md#bugs-de-ejemplo) |

## Documentación

En cada carpeta están los casos de prueba y los reportes de bugs del proyecto. Los archivos están en CSV y se pueden abrir con Excel o Google Sheets. En los README dejé los enlaces a las aplicaciones y sus narrativas.

## Prácticas que apliqué

- Diseño de casos con precondiciones, datos de entrada, pasos y resultados esperados.
- Pruebas de campos obligatorios, formatos, límites de longitud y flujos de alta, edición y baja.
- Comparación entre resultado esperado y obtenido para documentar diferencias.
- Reporte de defectos con pasos de reproducción y comparación entre el resultado esperado y el obtenido.
- Revisión cruzada de casos y reportes en Provinciano.
- Organización y actualización de la documentación en GitHub.

## Responsable

Franco Montalbano

## Acceso a las referencias

Revisé los 57 enlaces externos de los README y CSV el 13/11/2026, sin iniciar sesión. No encontré enlaces rotos.

| Referencia | Acceso comprobado |
| :--- | :--- |
| Aplicaciones y narrativas de Contactos, Provinciano y Lumbricina | Las seis páginas respondieron correctamente. |
| Google Sheets: casos y bugs de Contactos, bugs de Provinciano y casos de Lumbricina | Las cuatro planillas permitieron leer la pestaña enlazada sin iniciar sesión. |
| Wikipedia: provincias y regiones | La página respondió correctamente. |
| [Mantis: listado de incidencias](https://mantis.pakova.org/view_all_bug_page.php) y los 45 enlaces de incidencias del CSV de Lumbricina | Requieren iniciar sesión. Los reportes de ejemplo se pueden leer acá, sin entrar a Mantis. |

## Pendiente

- Plan de ejecución: el repo contiene casos, resultados y reportes de bugs, pero todavía no incluye un plan de ejecución separado.
