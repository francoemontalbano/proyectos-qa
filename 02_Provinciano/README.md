# Testing manual — Buscador Provinciano

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre el buscador de provincias de Proyecto Nahual. Trabajé con filtros, ordenamiento y visualización de datos, y participé en la revisión de casos y reportes con Grego Lopez.

## Métricas

Conté los registros del CSV por versión: un mismo escenario repetido en otra versión cuenta otra vez. Tomé como `OK` solo los resultados escritos como `OK`. La otra columna reúne diferencias y resultados descriptivos; no equivale por sí sola a una cantidad de bugs.

| Versión | Casos | OK | Con diferencias u otro resultado descriptivo |
| :--- | ---: | ---: | ---: |
| v1 | 86 | 0 | 86 |
| v2 | 87 | 16 | 71 |
| v3 | 87 | 17 | 70 |
| v4 | 87 | 0 | 87 |
| **Total** | **347** | **33** | **314** |

| Severidad registrada | Reportes de bugs |
| :--- | ---: |
| Alta | 167 |
| Media | 7 |
| Baja | 2 |
| Sin informar | 100 |
| **Total** | **276** |

## Caso de prueba de ejemplo

**TC149 — Validar - Buscar por "Región" "Región del Norte Grande Argentino" con Nombre "Chaco"**

| Campo | Detalle |
| :--- | :--- |
| ID | 149 |
| Versión | v2 |
| Precondiciones | Ingresar a la Página Provinciano |
| Datos de entrada | Región: «Región del Norte Grande Argentino». Nombre: «Chaco». |
| Pasos | 1- Seleccionar "Región del Norte Grande Argentino" en el campo<br>"Región"<br>2- Ingresar "Chaco" en el campo "Nombre"<br>3- Hacer clic en "Buscar!" |
| Resultado esperado | El sistema muestra en la grilla únicamente la provincia "Chaco", con la siguiente<br>información:<br>Región: Región del Norte Grande Argentino<br>Nombre: Chaco<br>Capital: Resistencia<br>Habitantes: 1.129.606<br>Km²: 99.633 |
| Resultado obtenido | El sistema muestra en la grilla únicamente la provincia "Chaco", con la <br>información de:<br>Región: Región del Norte Grande Argentino<br>Nombre: Chaco<br>Capital: Resistencia<br>Habitantes: 1.055.259<br>Km²: 102.602<br>Luego de clickear el botón Buscar! el sistema y la interfaz se congelan durante 13 segundos. |
| Estado registrado del caso | Cerrado |

Conservo el estado del CSV. «Abierto» o «Cerrado» es el estado registrado del caso; no lo uso para decidir si el resultado fue `OK`.

Fuente: [matriz de casos](Test%20Case%20-%20Provinciano%20-%20Franco.csv). Los datos de entrada del ejemplo salen de sus pasos y precondiciones.

## Bugs de ejemplo

Elegí reportes con mayor severidad registrada y pasos concretos para mostrar el problema. Mantengo la severidad del archivo.

En estos reportes figuro como revisor y Grego Lopez como autor. Vinculé los casos que tienen la misma versión, filtros y datos de entrada; el CSV de bugs no trae un campo de caso relacionado.

### Bug 86 — El filtro «Ninguna» incluye Ciudad Autónoma de Buenos Aires

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC93 (por coincidencia de escenario) |

**Pasos para reproducir**

**Preparación:** Ingresar al sistema

1. Clickear menú despegable del filtro región
2. Clickear "Ninguna"
3. FIltro Nombre: vacío
4. Clickear botón Buscar!"

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema muestra una grilla que contiene los registros que coincidan con el criterio de búsqueda seleccionado: Provincia de Buenos Aires<br>Columnas:<br>Región: Ninguna<br>Nombre: Buenos Aires<br>Capital: La Plata<br>Habitantes: 17 523 996<br>Km2: 307 571<br><br><br>Se encuentran disponibles opciones para ordenar por cualquiera de las columnas |
| Resultado obtenido | Al seleccionar la opción "Ninguna" y realizar la búsqueda, el sistema muestra las<br>provincias "Buenos Aires" y "Ciudad Autónoma de Buenos Aires", en lugar de mostrar<br>únicamente la provincia "Buenos Aires", según lo esperado |

### Bug 92 — La búsqueda de Chaco devuelve habitantes y superficie distintos de los esperados

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC149 (por coincidencia de escenario) |

**Pasos para reproducir**

**Preparación:** Ingresar al sistema

1. Clickear menú despegable del filtro región
2. Clickear "Región del Norte Grande Argentino"
3. Completar Filtro Nombre con "chaco".
4. Clickear botón Buscar!"

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema muestra una grilla que contiene los registros que coincidan con el criterio de búsqueda seleccionado: Provincia de Chaco<br>Columnas:<br>Región: Norte Grande Argentino<br>Nombre: Chaco<br>Capital: Resistencia<br>Habitantes: 1 129 606<br>Km2: 99 633<br><br>Se encuentran disponibles opciones para ordenar por cualquiera de las columnas |
| Resultado obtenido | Al seleccionar la opción "Región del Norte Grande Argentino", ingresar "chaco" en el filtro <br>"Nombre" y realizar la búsqueda, el sistema muestra correctamente la provincia "Chaco",<br> sin embargo, la columna "Habitantes" muestra el valor 1.055.259 en lugar de 1.129.606, <br>y la columna "Km²" muestra el valor 102.602 en lugar de 99.633, según lo especificado <br>en el caso de prueba |

Fuente: [archivo de bugs](Bugs%20-%20Provinciano%20-%20Franco.csv).

## Técnicas aplicadas

- **Combinación de filtros:** probé Región junto con Nombre; por ejemplo, Norte Grande Argentino + Chaco (TC149, v2) y Norte Grande Argentino + Córdoba, sin coincidencias esperadas (TC156, v2).
- **Variaciones de entrada:** probé búsquedas con mayúsculas, minúsculas y sin tildes (TC125–126, v2), además de subcadenas presentes en la matriz.
- **Regresión entre versiones:** repetí búsquedas por región, nombre y ordenamientos entre v1 y v4. Los resultados quedan separados por versión en el CSV.

## Alcance de las pruebas

- Revisé los títulos, los campos por defecto y la información de la grilla.
- Probé las búsquedas por nombre y región, las subcadenas y las variaciones de mayúsculas y tildes.
- Verifiqué el ordenamiento ascendente y descendente de las columnas de texto y datos numéricos.
- Probé combinaciones de filtros y búsquedas consecutivas.

## Aplicación y referencias

- [Aplicación Provinciano](https://nahual.github.io/qc-provinciano/provinciano_1.html)
- [Narrativa funcional](https://nahual.github.io/qc-provinciano/especificaciones.html)
- [Referencia de provincias y regiones](https://es.wikipedia.org/wiki/Provincias_de_Argentina#Regiones_existentes)

## Documentación

| Archivo | Contenido |
| :--- | :--- |
| [Casos de prueba](Test%20Case%20-%20Provinciano%20-%20Franco.csv) | 347 registros de casos de prueba, distribuidos entre v1, v2, v3 y v4. |
| [Reportes de bugs](Bugs%20-%20Provinciano%20-%20Franco.csv) | 276 registros de reportes con los campos Autor y Revisor. |

## Trabajo realizado

- Diseñé mis casos de prueba con precondiciones, pasos y resultados esperados.
- Documenté los resultados obtenidos y los defectos encontrados durante las pruebas.
- Trabajé en pareja con Grego Lopez: yo revisaba sus casos y él revisaba los míos. A partir de esa revisión y de las pruebas realizadas, identificábamos y documentábamos los defectos.
- Participé como revisor en reportes elaborados por Grego. Los campos Autor y Revisor permiten distinguir mi participación en cada reporte.

## Resultados

La matriz reúne los resultados de v1 a v4. Los reportes conservan los campos Autor y Revisor del trabajo en pareja.

## Responsable

Franco Montalbano
