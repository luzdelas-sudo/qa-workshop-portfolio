# Hoja de Sesión Exploratoria

## INFORMACIÓN DE LA SESIÓN
* **CHARTER (Misión):** Evaluar la estabilidad, seguridad e integridad de datos en los flujos críticos de la API y la aplicación web (gestión de catálogo, stock, errores en checkout y registro de usuarios)..
* **ÁREAS / AMBIENTE:** API REST (https://petstore.swagger.io/v2/swagger.json) | Navegador  Crome, Mozilla/ Thunder Client.
* **INICIO:** 2026-09-16 19:30 | **DURACIÓN:** 60 - 90 Minutos
* **TESTER:** Luz Pedrozo/ QA Engineer
## DESGLOSE DE TAREAS (%)
* Setup y Swagger: 65%
* Pruebas en API: 20%
* Documentación: 15%

## ARCHIVOS Y DATOS DE PRUEBA UTILIZADOS
* `swagger.json`
* Datasets de Entrada: Listas de emails válidos e inválidos, contraseñas débiles, datos con caracteres especiales para registro de usuarios y cantidades límite para pruebas de stock (0, valores negativos, superación de stock existente).

## NOTAS DE PRUEBA (Log de Exploración)
Se probó el registro (POST /mascota) y la actualización (PUT /mascota) enviando payloads completos e incompletos.
Se filtraron mascotas por estado (GET /mascota/buscarPorEstado) usando valores válidos (available, pending, sold) y valores no definidos.
Se probó la consulta por ID (GET /mascota/{petId}) y la eliminación (DELETE /mascota/{petId}).

## LISTA DE RIESGOS IDENTIFICADOS
Manejo de Autenticación: Dependencia de la cabecera api_key sin mecanismos de expiración o renovación explícitos visibles en la documentación.
Respuesta ante recursos inexistentes: Comportamiento inconsistente (códigos HTTP 404 vs 500) al consultar IDs que no existen en la base de datos.

## DEFECTOS (BUGS)
Error HTTP 500 al consultar IDs con formato no válido: La API responde con un error interno del servidor en lugar de un código 404 Not Found o 400 Bad Request al enviar caracteres especiales o cadenas en parámetros numéricos (petId, orderId).
Persistencia inconsistente tras eliminación: En ciertos casos, un recurso eliminado mediante DELETE /mascota/{petId} sigue apareciendo de forma implícita en las respuestas del endpoint GET /mascota/buscarPorEstado.
Respuesta exitosa (200 OK) con cuerpo vacío: Al ejecutar POST /mascota/{petId}/subirImagen sin adjuntar ningún archivo en el cuerpo de la petición, la API retorna una respuesta exitosa en lugar de validar la ausencia del adjunto.

## INCIDENTES Y PREGUNTAS (ISSUES)
Comportamiento no documentado sobre concurrencia: Existe incertidumbre sobre cómo maneja el sistema la actualización simultánea de un mismo registro (PUT /mascota) cuando dos usuarios envían modificaciones al mismo tiempo.