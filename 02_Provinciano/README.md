# Testing manual — Buscador Provinciano

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre el buscador de provincias de Proyecto Nahual. Trabajé con filtros, ordenamiento y visualización de datos, y participé en la revisión de casos y reportes con Grego.

## Métricas

| Versión | Casos | OK | Con diferencias u otro resultado descriptivo |
| :--- | ---: | ---: | ---: |
| v1 | 86 | 0 | 86 |
| v2 | 87 | 15 | 72 |
| v3 | 87 | 17 | 70 |
| v4 | 87 | 0 | 87 |
| **Total** | **347** | **32** | **315** |


En v1 y v4 no marqué resultados como `OK`: los 86 y 87 casos tienen el resultado escrito como descripción. El cero no significa que no haya probado esos casos.

| Severidad registrada | Reportes de bugs |
| :--- | ---: |
| Alta | 166 |
| Media | 100 |
| Baja | 10 |
| **Total** | **276** |

Entre los problemas reportados están la inclusión de Ciudad Autónoma de Buenos Aires al filtrar por «Ninguna» y los valores de habitantes y superficie de Chaco distintos de los esperados.

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
| Resultado obtenido | El sistema muestra en la grilla únicamente la provincia "Chaco", con la <br>información de:<br>Región: Región del Norte Grande Argentino<br>Nombre: Chaco<br>Capital: Resistencia<br>Habitantes: 1.055.259<br>Km²: 102.602<br>Luego de hacer clic en el botón Buscar! el sistema y la interfaz se congelan durante 13 segundos. |
| Estado registrado del caso | Cerrado |

Fuente: [casos de prueba](Test%20Case%20-%20Provinciano%20-%20Franco.csv).

## Bugs de ejemplo

Trabajé en revisión cruzada con Grego: revisé sus casos de prueba y él revisó los míos. En este repo comparto los reportes que revisé; Grego comparte los míos.

### Bug 86 — El filtro «Ninguna» incluye Ciudad Autónoma de Buenos Aires

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC93 (por coincidencia de escenario) |

**Pasos para reproducir**

1. Ingresar a Provinciano.
2. Abrir el desplegable "Región".
3. Seleccionar "Ninguna".
4. Dejar el campo "Nombre" vacío.
5. Hacer clic en "Buscar!".

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

1. Ingresar a Provinciano.
2. Abrir el desplegable "Región".
3. Seleccionar "Región del Norte Grande Argentino".
4. Ingresar "chaco" en el campo "Nombre".
5. Hacer clic en "Buscar!".

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema muestra una grilla que contiene los registros que coincidan con el criterio de búsqueda seleccionado: Provincia de Chaco<br>Columnas:<br>Región: Norte Grande Argentino<br>Nombre: Chaco<br>Capital: Resistencia<br>Habitantes: 1 129 606<br>Km2: 99 633<br><br>Se encuentran disponibles opciones para ordenar por cualquiera de las columnas |
| Resultado obtenido | Al seleccionar la opción "Región del Norte Grande Argentino", ingresar "chaco" en el filtro <br>"Nombre" y realizar la búsqueda, el sistema muestra correctamente la provincia "Chaco",<br> sin embargo, la columna "Habitantes" muestra el valor 1.055.259 en lugar de 1.129.606, <br>y la columna "Km²" muestra el valor 102.602 en lugar de 99.633, según lo especificado <br>en el caso de prueba |

Fuente: [archivo de bugs](Bugs%20-%20Provinciano%20-%20Franco.csv).

## Técnicas aplicadas

- **Combinación de filtros:** probé Región junto con Nombre; por ejemplo, Norte Grande Argentino + Chaco (TC149, v2) y Norte Grande Argentino + Córdoba, sin provincias que coincidan (TC156, v2).
- **Variaciones de entrada:** probé búsquedas con mayúsculas, minúsculas y sin tildes (TC125–126, v2), además de subcadenas de los casos.
- **Regresión entre versiones:** repetí búsquedas por región, nombre y ordenamientos entre v1 y v4. Los resultados quedan separados por versión en el CSV.

## Alcance de las pruebas

- Revisé los títulos, los campos por defecto y la información de la grilla.
- Probé las búsquedas por nombre y región, las subcadenas y las variaciones de mayúsculas y tildes.
- Verifiqué el ordenamiento ascendente y descendente de las columnas de texto y datos numéricos.
- Probé combinaciones de filtros y búsquedas consecutivas.
- Diseñé los casos y documenté los resultados de cada versión.

## Aplicación y referencias

- [Aplicación Provinciano](https://nahual.github.io/qc-provinciano/provinciano_1.html)
- [Narrativa funcional](https://nahual.github.io/qc-provinciano/especificaciones.html)
- [Referencia de provincias y regiones](https://es.wikipedia.org/wiki/Provincias_de_Argentina#Regiones_existentes)

## Documentación

| Archivo | Contenido |
| :--- | :--- |
| [Casos de prueba](Test%20Case%20-%20Provinciano%20-%20Franco.csv) | 347 registros de casos de prueba, distribuidos entre v1, v2, v3 y v4. |
| [Reportes de bugs](Bugs%20-%20Provinciano%20-%20Franco.csv) | 276 registros de reportes con los campos Autor y Revisor. |
