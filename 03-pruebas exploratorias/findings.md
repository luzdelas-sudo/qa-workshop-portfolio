# Risk Matrix

## Nombre del Producto 
JpetStore Demo

## Hallazgos
Respuestas incoherentes en códigos HTTP: Se observa que la API retorna un código 500 Internal Server Error ante entradas de datos no válidas o malformadas en lugar de emplear códigos de estado correctos como 400 Bad Request o 404 Not Found.
Inconsistencias en el filtrado por estado: Tras eliminar o modificar el estado de una mascota mediante DELETE o PUT,

## Mejoras
Estandarización del manejo de errores: Implementar un middleware global que capture excepciones de formato y devuelva un esquema JSON uniforme con mensajes claros y códigos de estado HTTP apropiados (400, 401, 404, 409).
Clarificar el ciclo de vida y tiempos de caducidad de la clave API (special-key), así como las reglas de negocio vinculadas a los cambios de estado en los pedidos.