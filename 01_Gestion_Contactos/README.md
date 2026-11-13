# Testing manual — Gestión de Contactos

## Descripción

En este proyecto diseñé y ejecuté casos de prueba sobre la aplicación de gestión de contactos de Proyecto Nahual. Documenté los resultados y los defectos encontrados en distintas versiones.

## Métricas

| Versión | Casos | OK | Con diferencias u otro resultado descriptivo |
| :--- | ---: | ---: | ---: |
| v1 | 42 | 24 | 18 |
| v2 | 42 | 23 | 19 |
| v3 | 42 | 25 | 17 |
| Versión Final | 42 | 35 | 7 |
| **Total** | **168** | **107** | **61** |

Los registros con diferencias pasan de 18 a 19, bajan a 17 y luego a 7.<br>
La Versión Final tiene 11 menos que v1, 12 menos que v2 y 10 menos que v3.

| Severidad registrada | Reportes de bugs |
| :--- | ---: |
| Alta | 10 |
| Media | 45 |
| Baja | 7 |
| **Total** | **62** |

En Versión Final reporté rechazo de nombres y mails de 35 caracteres, restricciones de nombres repetidos y falta de advertencias al cancelar cambios.

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

Fuente: [matriz de casos](Test%20case%20-%20Contactos%20-%20Franco.csv).

## Bugs de ejemplo

### Bug 79 — Cancelar la eliminación borra el contacto

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC79 |

**Pasos para reproducir**

1. Ingresar a Contactos con un contacto "Franco" / "francoemontalbano@gmail.com" existente.
2. Clic en "Borrar" sobre "Franco".
3. Clic en "Cancelar eliminación".

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema no elimina el contacto "Franco" y este continúa<br>visualizándose en Contactos |
| Resultado obtenido | El sistema elimina el contacto a pesar de hacer clic en "Cancelar" |

### Bug 129 — Rechazo de un nombre de 35 caracteres

| Campo | Detalle |
| :--- | :--- |
| Severidad | Media |
| Versión | Versión Final |
| Caso relacionado | TC129 |

**Pasos para reproducir**

1. Ingresar a Contactos.
2. Clic en "Nuevo contacto".
3. Clic en el campo "Nombre".
4. Ingresar "ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHI" (35 caracteres).
5. Clic en el campo "Mail".
6. Ingresar "franco@gmail.com".
7. Clic en "Guardar".

| Campo | Detalle |
| :--- | :--- |
| Resultado esperado | El sistema permite ingresar un nombre de hasta 35 caracteres en el campo "Nombre". |
| Resultado obtenido | El sistema no permite ingresar un "Nombre" de 35 caracteres. |

### Bug 71 — Editar un contacto impide guardar los nuevos datos

| Campo | Detalle |
| :--- | :--- |
| Severidad | Alta |
| Versión | v2 |
| Caso relacionado | TC71 |

**Pasos para reproducir**

1. Ingresar a Contactos con un contacto "Franco" / "franco@gmail.com" existente.
2. Clic en "Editar".
3. Modificar el campo "Nombre" por "Pedro".
4. Modificar el campo "Mail" por "francoemontalbano@gmail.com".
5. Clic en "Guardar".

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
- Diseñé los casos para v1, v2, v3 y Versión Final, y documenté los resultados y las diferencias con la narrativa.

## Aplicación y referencias

- [Aplicación Contactos](https://nahual.github.io/qc-contactos/contactos.html)
- [Narrativa funcional y Anexo A](https://nahual.github.io/qc-contactos/especificaciones.html)

Usé el Anexo A de la narrativa como criterio para validar los mails.

## Documentación

| Archivo | Contenido |
| :--- | :--- |
| [Casos de prueba](Test%20case%20-%20Contactos%20-%20Franco.csv) | 168 registros: 42 por versión, distribuidos entre v1, v2, v3 y Versión Final. |
| [Reportes de bugs](Bugs%20-%20Contactos%20-%20Franco.csv) | 62 reportes de las cuatro versiones, con sus estados y severidades. |

## Responsable

Franco Montalbano
