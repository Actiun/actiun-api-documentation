# Errores

El API de Actiun utiliza los siguientes codigos de error:


Código de Error | Significado
---------- | -------
400 | Bad Request -- El request está mal formado. La información para crear el recurso no existe o es inválida.
401 | Unauthorized -- Credenciales no válidas.
404 | Not Found -- El objeto que buscas no existe.
405 | Method Not Allowed -- Operación no permitida. Ocurre cuando el método del request es inválido para el endpoint requerido.
429 | Too Many Requests -- Has hecho muchas peticiones por lo que debes bajar el intervalo de solicitudes.
500 | Internal Server Error -- Ocurrió un error en la aplicación.
503 | Service Unavailable -- La applicación se encuentra en mantenimiento.
