# Errores

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>


Código de Error | Significado
---------- | -------
400 | Bad Request -- El request está mal formado. La información para crear el recurso no existe o es inválida.
401 | Unauthorized -- Credenciales no válidas.
404 | Not Found -- El objeto que buscas no existe.
405 | Method Not Allowed -- Operación no permitida. Ocurre cuando el método del request es inválido para el endpoint requerido.
429 | Too Many Requests -- Has hecho muchas peticiones por lo que debes bajar el intervalo de solicitudes.
500 | Internal Server Error -- Ocurrió un error en la aplicación.
503 | Service Unavailable -- La applicación se encuentra en mantenimiento.
