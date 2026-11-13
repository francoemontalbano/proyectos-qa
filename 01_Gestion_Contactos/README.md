# Testing manual — Gestión de Contactos

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre la aplicación de gestión de contactos de Proyecto Nahual. Documenté los resultados y los defectos encontrados en distintas versiones.

## Métricas

Conté los registros del CSV por versión: un mismo escenario repetido en otra versión cuenta otra vez. Tomé como `OK` solo los resultados escritos como `OK`. La otra columna reúne diferencias y resultados descriptivos; no equivale por sí sola a una cantidad de bugs.

| Versión | Casos | OK | Con diferencias u otro resultado descriptivo |
| :--- | ---: | ---: | ---: |
| v1 | 42 | 25 | 17 |
| v2 | 42 | 23 | 19 |
| v3 | 42 | 25 | 17 |
| Versión Final | 42 | 35 | 7 |
| **Total** | **168** | **108** | **60** |

| Severidad registrada | Reportes de bugs |
| :--- | ---: |
| Alta | 11 |
| Media | 45 |
| Baja | 6 |
| **Total** | **62** |

## Caso de prueba de ejemplo

**TC37 — Validar - Edición "Editar Contacto" "Cancelar" con "Nombre" y "Mail" modificados**

| Campo | Detalle |
| :--- | :--- |
| ID | 37 |
| Versión | v1 |
| Precondiciones | Ingresar a la página de Contactos<br>Existe al menos un contacto <br>registrado con: <br>Nombre: "Franco" <br>Mail: "franco@gmail.com" |
| Datos de entrada | Contacto inicial: Nombre «Franco», Mail «franco@gmail.com». Cambio: Nombre «Pedro»; mantengo el mismo Mail. |
| Pasos | 1- Hacer clic en "Editar" sobre el contacto<br>Franco<br>2- Modificar el campo "Nombre" por "Pedro"<br>3- Mantener el Mail "franco@gmail.com"<br>4- Hacer clic en "Cancelar". |
| Resultado esperado | El sistema emite una alerta "Se perderán los cambios sin guardar" y cierra el formulario |
| Resultado obtenido | El sistema almacena los datos modificados en la<br>tabla "Contactos" a pesar de haber cancelado la <br>petición |
| Estado registrado del caso | Abierto |

Conservo el estado del CSV. «Abierto» o «Cerrado» es el estado registrado del caso; no lo uso para decidir si el resultado fue `OK`.

Fuente: [matriz de casos](Test%20case%20-%20Contactos%20-%20Franco.csv). Los datos de entrada del ejemplo salen de sus pasos y precondiciones.

## Bugs de ejemplo

Elegí reportes con mayor severidad registrada y pasos concretos para mostrar el problema. Mantengo la severidad del archivo.

Relacioné cada reporte con el caso que tiene el mismo ID, versión, pasos y resultado; el CSV de bugs no trae un campo de caso relacionado.

### Bug 79 — Cancelar la eliminación borra el contacto

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC79 |

**Pasos para reproducir**

**Preparación:** Ingresar a la página de Contactos Existe al menos un contacto registrado con: Nombre: "Franco" Mail: "francoemontalbano@gmail.com" Hacer clic en "Borrar" sobre el contacto "Franco"

1. Hacer clic en "Cancelar eliminación"

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema no elimina el contacto "Franco" y este continúa<br>visualizándose en Contactos |
| Resultado obtenido | El sistema elimina el contacto a pesar de hacer clic en "Cancelar" |

### Bug 37 — Cancelar la edición guarda los cambios

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v1 |
| Caso relacionado | TC37 |

**Pasos para reproducir**

1. Hacer clic en "Editar" sobre el contacto Franco
2. Modificar el campo "Nombre" por "Pedro"
3. Mantener el Mail "franco@gmail.com"
4. Hacer clic en "Cancelar".

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema emite una alerta "Se perderán los cambios sin guardar"<br>y cierra el formulario |
| Resultado obtenido | El sistema almacena los datos modificados en la tabla "Contactos"<br>a pesar de haber cancelado la petición |

### Bug 71 — Editar un contacto impide guardar los nuevos datos

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC71 |

**Pasos para reproducir**

**Preparación:** Ingresar a la página de Contactos Existe al menos un contacto registrado con: Nombre: "Franco" Mail: "franco@gmail.com"

1. Hacer clic en Editar
2. Modificar el campo "Nombre" por "Pedro"
3. Modificar el campo "Mail" por francoemontalbano@gmail.com
4. Hacer clic en "Guardar"

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema guarda los cambios realizados y muestra en la tabla de <br>Contactos el registro actualizado con el Nombre "Pedro" y el Mail <br>"francoemontalbano@gmail.com" |
| Resultado obtenido | El sistema no permite guardar el contacto actualizado y emite el siguiente<br>mensaje: "Ya existe un contacto con este mail" |

Fuente: [archivo de bugs](Bugs%20-%20Contactos%20-%20Franco.csv).

## Técnicas aplicadas

- **Partición de equivalencia:** probé nombres con letras, números, caracteres especiales y espacios (TC3–7, v1); mails sin arroba, sin dominio y con formato válido (TC18–26, v1).
- **Análisis de valores límite:** probé 34, 35 y 36 caracteres en Nombre (TC129–131, Versión Final) y Mail (TC143–145, Versión Final).
- **Validación de campos obligatorios:** dejé Nombre o Mail vacíos y probé Guardar (TC11, TC20 y TC27–29, v1).
- **Regresión entre versiones:** repetí escenarios de alta, edición, baja y ordenamiento en v1, v2, v3 y Versión Final; por ejemplo, la cancelación de una eliminación en TC42 (v1), TC79 (v2), TC121 (v3) y TC163 (Versión Final).

## Alcance de las pruebas

- Probé el listado inicial y el ordenamiento por nombre y mail.
- Revisé el alta de contactos, los campos obligatorios, las longitudes y el formato del mail.
- Probé la edición, las validaciones de duplicados y la cancelación de cambios.
- Verifiqué la confirmación y cancelación de la eliminación de contactos.

## Aplicación y referencias

- [Aplicación Contactos](https://nahual.github.io/qc-contactos/contactos.html)
- [Narrativa funcional y Anexo A](https://nahual.github.io/qc-contactos/especificaciones.html)
- [Casos de prueba originales — pestaña Franco](https://docs.google.com/spreadsheets/d/16vzz7vlb0N53IwxZ0GK0c6siKPZIVVfcrb-nMsV1Fc0/edit?gid=365926205)
- [Reportes de bugs originales — pestaña Franco](https://docs.google.com/spreadsheets/d/1dJMQ2Kac_XiT1YDOooBzaSx6ROWlI70WLwWR3MN-zlc/edit?gid=1050203018)

Usé el Anexo A de la narrativa como criterio para validar los mails.

## Documentación

| Archivo | Contenido |
| :--- | :--- |
| [Casos de prueba](Test%20case%20-%20Contactos%20-%20Franco.csv) | 168 registros: 42 por versión, distribuidos entre v1, v2, v3 y Versión Final. |
| [Reportes de bugs](Bugs%20-%20Contactos%20-%20Franco.csv) | 62 reportes de las cuatro versiones, con sus estados y severidades. |

## Trabajo realizado

- Armé los casos de prueba para v1, v2, v3 y Versión Final.
- Probé datos válidos e inválidos en los campos Nombre y Mail, incluidos los límites de longitud.
- Verifiqué el guardado, la edición y la eliminación de contactos, además de las opciones para cancelar cada operación.
- Comparé el resultado obtenido con la narrativa y reporté las diferencias.

## Resultados

En Versión Final registré **35 casos OK y 7 con diferencias**. Entre los problemas reportados están el rechazo de nombres y mails de 35 caracteres, la restricción de nombres repetidos y la falta de advertencias al cancelar cambios.

En la matriz marqué `OK` cuando el resultado coincidió con el esperado. En los demás casos describí lo que ocurrió. Los archivos también incluyen los resultados de las versiones anteriores.

## Responsable

Franco Montalbano
