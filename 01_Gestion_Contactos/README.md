# Testing manual — Gestión de Contactos

En este proyecto diseñé y ejecuté casos de prueba sobre el alta, listado, ordenamiento, edición y baja de contactos de Proyecto Nahual.

## Aplicación y referencia

- [Aplicación Contactos](https://nahual.github.io/qc-contactos/contactos.html)
- [Narrativa funcional y Anexo A](https://nahual.github.io/qc-contactos/especificaciones.html)
- [Matriz original — pestaña Franco](https://docs.google.com/spreadsheets/d/16vzz7vlb0N53IwxZ0GK0c6siKPZIVVfcrb-nMsV1Fc0/edit?gid=365926205)
- [Reportes originales — pestaña Franco](https://docs.google.com/spreadsheets/d/1dJMQ2Kac_XiT1YDOooBzaSx6ROWlI70WLwWR3MN-zlc/edit?gid=1050203018)

Usé el **Anexo A de la narrativa** como criterio para validar los mails.

## Documentación

- [Casos de prueba](Test%20case%20-%20Contactos%20-%20Franco.csv): 168 registros, 42 por versión (v1, v2, v3 y Versión Final), con resultado obtenido.
- [Reportes de bugs](Bugs%20-%20Contactos%20-%20Franco.csv): 62 reportes reales de las cuatro versiones; incluye reportes cerrados y su explicación. Excluí del archivo publicado el ejemplo BUG 0 de la plantilla.

Publiqué la documentación en CSV para poder consultarla desde Excel o Google Sheets. Uso `OK` cuando el resultado coincide con el esperado y describo las diferencias en Resultado Obtenido. Conservo el estado de gestión `Abierto` de la plantilla por separado del resultado de ejecución.

## Revisión del 11/11/2026

Revisé los casos de **Versión Final** usando Chrome y `contactos.html`. Conservé los resultados históricos de v1, v2 y v3; esta revisión corresponde a Versión Final.

- Corregí los esperados de orden descendente y las validaciones de campos obligatorios según la narrativa.
- Corregí los datos de mail y volví a ejecutar los TC143, TC144 y TC145 para tener exactamente 35, 34 y 36 caracteres.
- Completé el dato de mail del TC133 y verifiqué el rechazo del nombre repetido con un mail diferente.
- Descarté los reportes 122, 126 y 127 de Versión Final por criterios que la narrativa no exige. Conservé sus filas como historial, con estado Cerrado y el motivo en Observaciones.
- Agregué el reporte **143 de Versión Final** al comprobar que la aplicación rechaza un mail válido de 35 caracteres.
- Verifiqué el mensaje de borrado y ambas decisiones: confirmar elimina el contacto y cancelar lo conserva. Registré los TC161–163 como OK.

Registré **35 resultados OK y 7 con diferencias documentadas** en la matriz de Versión Final. Los reportes activos asociados son 129, 133, 143, 153, 157, 158 y 160. Esta cifra describe los registros de la matriz; no implica siete causas independientes.

## Trazabilidad histórica

Los IDs 65–69 están repetidos en filas diferentes de v2 en la planilla original. Los conservé para mantener las referencias históricas y los identifico combinando **versión, ID y descripción del caso**, además de la fila de origen cuando sea necesario. Los trato como casos distintos y mantengo sus resultados separados de Versión Final.

## Responsable

Franco Montalbano
