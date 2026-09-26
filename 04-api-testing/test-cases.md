### Caso de Prueba: Carga exitosa 
**ID del Caso de Prueba:** TC_PET_UPLOAD_01
**Título:** Verificar la carga exitosa de una imagen asociada a un ID de mascota existente.
**Precondiciones:**
1. Debe existir una mascota registrada en el sistema con `petId = 11`.
2. Tener disponible un archivo de imagen válido en formato PNG/JPG (ej. `Aangora.png`).

#### Pasos de Ejecución:

1. Enviar una petición `POST` al endpoint `/pet/11/uploadImage`.
2. En los parámetros del cuerpo (`formData`), adjuntar:
**additionalMetadata:** `Gato Angora`
**file:** Archivo de imagen válido (`Abrelatas 5 en 1.png`).
3. Ejecutar la petición.

#### Resultado Esperado:

**Código de respuesta HTTP:** `200 OK`
**Cuerpo de la respuesta:** Un objeto de respuesta con código de éxito (ej. `code: 200`) y un mensaje indicando que la imagen se ha subido correctamente (por ejemplo, notificando la subida del archivo y/o metadatos).

### Caso de Prueba 2: Carga fallida por tipo de dato de ID inválido (Camino de Error / Negativo)

**ID del Caso de Prueba:** TC_PET_UPLOAD_02
**Título:** Validar el comportamiento del sistema al enviar un `petId` no numérico/inválido en la ruta.
**Precondiciones:** Ninguna específica.

#### Pasos de Ejecución:
1. Enviar una petición `POST` al endpoint `/pet/abc-invalid/uploadImage`.
2. Incluir opcionalmente metadatos o archivo en el `formData`.
3. Ejecutar la petición.

#### Resultado Esperado:

**Código de respuesta HTTP:** `400 Bad Request` o `404 Not Found` (dependiendo de la validación del framework, típicamente `400` por error en el formato del parámetro del path).
**Cuerpo de la respuesta:** Mensaje de error indicando que el ID especificado no cumple con el formato requerido (`int64`).{
  "id": 102,
  "name": "Pelusa"
  "status": "available"
}

**ID del Caso de Prueba:** TC_PET_PUT_02
**Título:** Verificar el rechazo al intentar actualizar una mascota enviando un ID alfanumérico en lugar de numérico.
**Precondiciones:**

1. Servidor de la API Swagger Petstore disponible.

#### Pasos de Ejecución:

1. Configurar una petición `PUT` al endpoint `/pet`.
2. Establecer el encabezado `Content-Type: application/json`.
3. En el cuerpo de la petición (`Body`), incluir un valor tipo texto en la clave `id`:
{
  "id": "ID_INVALIDO_TEXTO",
  "name": "Mascota Error",
  "photoUrls": ["https://ejemplo.com/foto.jpg"]
}


#### Resultado Esperado:

* **Código de respuesta HTTP:** `400 Bad Request` o `500 Internal Server Error`
* **Cuerpo de la respuesta:** Mensaje indicando un fallo en la validación o parseo del campo `id`.

---

### Caso de Prueba 9: Eliminación exitosa de una mascota

* **ID del Caso de Prueba:** TC_PET_DELETE_01
* **Título:** Verificar la eliminación del registro de una mascota utilizando un ID existente.
* **Precondiciones:**

1. Debe existir una mascota registrada en el sistema con `petId = 11`.

#### Pasos de Ejecución:

1. Configurar una petición `DELETE` al endpoint `/pet/11`.
2. Incluir el encabezado `api_key: special-key` si el entorno lo requiere.
3. Ejecutar la petición.

#### Resultado Esperado:

* **Código de respuesta HTTP:** `200 OK`
* **Cuerpo de la respuesta:** Objeto JSON o mensaje confirmando la eliminación del recurso (`message: "101"`). Una consulta posterior `GET /pet/101` debe retornar `404 Not Found`.

### Caso de Prueba 10: Error al intentar eliminar una mascota inexistente

* **ID del Caso de Prueba:** TC_PET_DELETE_02
* **Título:** Verificar la respuesta del sistema al intentar borrar una mascota con un ID que no existe.
* **Precondiciones:**

1. El identificador `petId = 888888` no debe existir en el registro.

#### Pasos de Ejecución:

1. Configurar una petición `DELETE` al endpoint `/pet/888888`.
2. Ejecutar la petición.

#### Resultado Esperado:

* **Código de respuesta HTTP:** `404 Not Found`
* **Cuerpo de la respuesta:** Mensaje notificando que el recurso solicitado para eliminación no existe en la base de datos.