# QA Test Repository - Buscador Provinciano

## Descripción
Repositorio de documentación de testing, diseño de casos de prueba y reporte de defectos para la aplicación web de búsqueda de datos provinciales de Argentina.

## Aplicación bajo prueba
Sistema de filtros avanzados (Región y Nombre) con renderizado dinámico de grilla de resultados (Región, Nombre, Capital, Habitantes, Km²) y opciones de ordenamiento alfabético y numérico.

## Alcance del Testing
- **Módulo de Listado e Interfaz:** Verificación de títulos, campos por defecto ("Todas" y vacío) y alineación ortográfica respecto a las especificaciones.
- **Módulo de Filtrado:** Validación sintáctica de búsquedas por subcadenas ("San", "La"), distinción de tildes/mayúsculas y comportamientos lógicos de la región "Ninguna".
- **Módulo de Ordenamiento:** Comprobación del orden alfabético y numérico (ascendente/descendente) en cada columna y control de errores de codificación en encabezados.
- **Estabilidad del Sistema:** Pruebas de estrés ante búsquedas simultáneas o consecutivas y validación de tiempos de respuesta de la interfaz.

## Trabajo colaborativo y revisión cruzada
La práctica se realizó en pareja entre Franco Montalbano y Grego Lopez. Cada integrante diseñaba sus propios casos de prueba (TC) y revisaba los del compañero: Franco revisaba los casos de Grego y Grego revisaba los de Franco. A partir de este trabajo de revisión y de las pruebas realizadas, se identificaban y documentaban los defectos.

Los campos **Autor** y **Revisor** de los reportes permiten distinguir la participación de cada integrante. Los reportes elaborados por Grego y revisados por Franco forman parte de esta dinámica de trabajo colaborativo.

## Archivos Incluidos
- `Test Case - Provinciano - Franco.csv` : Matriz completa de diseño de casos de prueba.
- `Bugs - Provinciano - Franco.csv` : Reporte detallado de defectos detectados durante los ciclos de ejecución.

## Responsable
Franco Montalbano

## Documentación de Referencia
- **Especificaciones del Proyecto:** [Proyecto Nahual - Especificaciones Provinciano](https://nahual.github.io/qc-provinciano/especificaciones.html)
- **Estándar de Validación:** [Wikipedia - Provincias de Argentina (Regiones Existentes)](https://es.wikipedia.org/wiki/Provincias_de_Argentina#Regiones_existentes)
- **Aplicación en Producción (App Under Test):** [Sitio de Pruebas - Buscador Provinciano](https://nahual.github.io/qc-provinciano/provinciano_1.html?)
