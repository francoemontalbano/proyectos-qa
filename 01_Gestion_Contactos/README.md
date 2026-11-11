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
| [Reportes de bugs](Bugs%20-%20Contactos%20-%20Franco.csv) | 62 reportes de las cuatro versiones, incluidos los cerrados con su explicación. |

Publiqué los archivos en CSV para consultarlos desde Excel o Google Sheets.

## Trabajo realizado

- Diseñé los casos con precondiciones, pasos y resultados esperados, y documenté los resultados obtenidos.
- Revisé los casos de Versión Final contra la narrativa y corregí los esperados de orden descendente y campos obligatorios.
- Corregí y volví a ejecutar los datos de mail de los TC143–145 para probar exactamente 35, 34 y 36 caracteres.
- Completé el mail del TC133 y verifiqué el nombre repetido usando un mail diferente.
- Descarté los reportes 122, 126 y 127 de Versión Final por criterios que la narrativa no exige; conservé sus filas y el motivo del cierre.
- Agregué el reporte 143 al comprobar que la aplicación rechaza un mail válido de 35 caracteres.
- Verifiqué el mensaje de borrado y ambas decisiones en los TC161–163.

## Resultados

Registré **35 resultados OK y 7 con diferencias documentadas en Versión Final**. Los reportes activos asociados son 129, 133, 143, 153, 157, 158 y 160.

Uso `OK` cuando el resultado coincide con el esperado y describo las diferencias en Resultado Obtenido. Conservo el estado de gestión del test case por separado del resultado de ejecución.

Actualicé la documentación el **11/11/2026**. La revisión de esa fecha corresponde a Versión Final; conservé los resultados anteriores de v1, v2 y v3. Excluí del CSV de bugs el ejemplo BUG 0 de la plantilla.

## Responsable

Franco Montalbano
