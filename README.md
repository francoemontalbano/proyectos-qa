# QA Test Repository - Gestión de Contactos

## Descripción
Repositorio de documentación de testing, diseño de casos de prueba y reporte de defectos para la aplicación web de administración de contactos.

## Aplicación bajo prueba
Sistema CRUD (Alta, Baja, Modificación y Listado) de contactos basado en validaciones estrictas de formatos y control de registros duplicados.

## Alcance del Testing
- **Módulo de Listado:** Verificación del estado vacío por defecto ("No hay contactos guardados"), ordenamiento alfabético automático por nombre/email y renderizado dinámico de la grilla.
- **Módulo de Alta (Creación):** Validación de campos obligatorios, límite de longitud (35 caracteres) e integridad de datos en el almacenamiento.
- **Módulo de Edición:** Comprobación de persistencia, precarga de datos existentes y prevención de pérdida de cambios mediante alertas del sistema al cancelar o navegar.
- **Módulo de Baja (Eliminación):** Flujo de confirmación interactiva para eliminación definitiva o cancelación de la acción.
- **Validaciones de Reglas de Negocio (Anexo A / RFC 5322):**
  - Control de correos duplicados.
  - Validación sintáctica del formato de Email (Estructura local-part, signo @, dominio, punto y TLD de 2 a 4 caracteres alfabéticos).

## Archivos Incluidos
- `Test case - Contactos - Franco.csv`: Matriz completa de diseño de casos de prueba.
- `Bugs - Contactos - Franco.csv`: Reporte detallado de defectos detectados durante los ciclos de ejecución.

## Responsable
Franco Montalbano
