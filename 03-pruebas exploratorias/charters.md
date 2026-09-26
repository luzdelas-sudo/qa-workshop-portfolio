# Charters 
## Charter 1 
**Título:** Validación de Entradas y Manejo de Errores en Recursos de Mascota
**Misión:** Explorar los endpoints /mascota (POST, PUT, GET /mascota/{petId}) utilizando payloads con campos incompletos, tipos de datos inválidos y caracteres especiales, para identificar fallos en las validaciones de entrada y verificar que la API retorne códigos de estado HTTP adecuados (400/404) en lugar de errores internos del servidor (500).
______ 
**Área principal explorada:**   API REST Swagger ( https://petstore.swagger.io/v2/swagger.json ) 
______ 
## Charter 2 
**Título:** Consistencia de Estado y Persistencia en Operaciones DELETE 
**Misión:** Explorar la eliminación de registros mediante DELETE /mascota/{petId} en combinación con búsquedas por filtro (GET /mascota/buscarPorEstado), para asegurar la integridad de datos y verificar que los recursos eliminados no sigan apareciendo en las respuestas del sistema.
______ 
**Área principal explorada:** API REST — Integridad de Datos y Persistencia de Estado. ( https://petstore.octoperf.com/actions/Catalog.action ).

*TESTER:** Luz Pedrozo/ QA Engineer