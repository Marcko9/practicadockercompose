# Código base para práctica Docker

![](https://emmer.dev/static/img/blog/publishing-docker-images-with-github-actions.jpg)

### Pasos a seguir para poder ejecutar


1. Clonar repositorio
2. Configurar variables de entorno
3. Docker compose
4. Validación de conexión
5. Registro de ejemplo
6. Rutas adicionales
7. Observaciones finales

####1. Clonar repositorio
Para poder iniciar la revisión de la funcionalidad del proyecto, es necesario clonar el repositorio.

`<link>` : <https://github.com/Marcko9/practicadockercompose>

####2. Configurar las variables de entorno
El repositorio contiene un archivo *.env *donde se localizan 3 variables de entorno, las cuáles pueden ser configuradas para brindar mayor seguridad

| Variable      | Valor |
| --------- | -----:|
| MONGO_USERNAME  | marcko |
| MONGO_PASSWORD     |   1234567 |
| MONGO_DB_NAME      |    usuarioDB |

####3. Docker compose
Para poder continuar se requiere ingresar mediante la consola a la carpeta donde hospeda el proyecto y ejecutar el siguiente comando:

`docker compose up`

####4. Validación de conexión
La aplicación trabaja sobre el puerto 8082 del equipo local; por lo cual se recomienda utilizar una herramienta como Postman para poder validar la conexión.

`http://127.0.0.1:8082/`


El resultado esperado es una cadena vacía.

####5. Registro de ejemplo
Para poder realizar la primera inserción se requiere utilizar el método POST con la siguiente estructura de la colección.

{
  
  "nombre":"Lionel",
  "apellido":"Messi",
  "username":"Leo10"
  
}

Al insertar el registro se devolverá los siguientes valores:

| Variable      | Valor |
| --------- | -----:|
| status  | 201 |
| message     |   Usuario creado |
| user     |    { objeto user }|

####6. Rutas adicionales
Se pueden realizar las siguientes actividades según el método y parámetros recibidos.


| Método  | Parámetro o body  | Resultado |
| :------------ |:---------------:| -----:|
| GET      | -- | Devuelve la colección de usuarios registrados. |
| GET     | id        |   Devuelve el usuario con el id igual al valor enviado. |
| zebra stripes | are neat        |    $1 |


| Método  | Parámetro o body  | Descripción | Posibles códigos de status |
| :------------ |:---------------:| :----- | :----- |
| GET      | -- | Devuelve la colección de usuarios registrados. | 200: OK |
| GET     | id        |   Devuelve el usuario con el id igual al valor enviado. |   200. Usuario encontrado; 404: Usuario no encontrado. |
| POST | {  "nombre":"valor",   "apellido":"valor",  "username":"valor" }        |    Inserta un nuevo usuario en la base de datos. | 201: Usuario creado |
| PUT | id | Permite actualizar los datos de un usuario en caso de encontrarse el id; en caso contrario, se dará de alta. | 200: Usuario encontrado y actualizado; 201: Usuario creado |
| DELETE | id | Permite eliminar un usuario con el id especificado. | 200: Usuario encontrado y eliminado; 204: Usuario no encontrado |


####7. Observaciones finales
El proyecto tiene muchas área de mejora, es la primera ocasión que trabajo con Docker, Github, Git, Node.js, Express.

Buscaré la forma que la siguiente versión del proyecto cubra con mayor alcance al actual.