# Testing manual — Gestión de Contactos

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre la aplicación de gestión de contactos de Proyecto Nahual. Documenté los resultados y los defectos encontrados en distintas versiones.

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

Publiqué los archivos en CSV para consultarlos desde Excel o Google Sheets.

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
