# Forum Hub

Este es nuestro desafío, llamado ForoHub: en él, vamos a replicar este proceso a nivel de back end y, para eso, crearemos una API REST usando Spring.

Nuestra API se centrará específicamente en los tópicos, y debe permitir a los usuarios:

Crear un nuevo tópico;
Mostrar todos los tópicos creados;
Mostrar un tópico específico;
Actualizar un tópico;
Eliminar un tópico.
Es lo que normalmente conocemos como CRUD* (CREATE, READ, UPDATE, DELETE) y es muy similar a lo que desarrollamos en LiterAlura, pero ahora de forma completa, agregando las operaciones de UPDATE y DELETE, y usando un framework que facilitará mucho nuestro trabajo.


## Ejecución del Proyecto

1. **Compila y ejecuta la aplicación con Maven**:

    ```bash
    mvn clean install
    mvn spring-boot:run
    ```

2. **Accede a la aplicación**:

   La aplicación estará disponible en `http://localhost:8080`.


## Documentación de la API

La documentación generada por Swagger está disponible en `http://localhost:8080/swagger-ui.html`, permitiendo la visualización y prueba interactiva de los endpoints.


# La autenticación stateless
Es un tipo de autenticación donde el servidor no guarda ninguna información sobre el estado del usuario entre las solicitudes. En lugar de mantener sesiones en el servidor, la autenticación stateless se basa en el uso de tokens para validar la identidad del usuario en cada solicitud.

## Breve Descripción del Proceso
- **Inicio de Sesión:**
  El usuario envía sus credenciales (usuario y contraseña) al servidor.
- **Generación de Token:**
  Si las credenciales son correctas, el servidor genera un token (generalmente un JWT - JSON Web Token) que incluye información sobre el usuario y una firma que garantiza su integridad.
- **Envío del Token:**
  El token se envía al usuario, generalmente en la respuesta HTTP.
- **Uso del Token:**
  El usuario almacena este token en el lado del cliente, típicamente en el almacenamiento local o en cookies.
- **Solicitudes Autenticadas:**
  Para cada solicitud posterior, el usuario envía el token en el encabezado de la solicitud HTTP (por ejemplo, Authorization: Bearer <token>).
- **Validación del Token:**
  El servidor valida el token en cada solicitud sin necesidad de mantener una sesión activa. La validación se realiza comprobando la firma del token y su fecha de expiración.
  Acceso a Recursos: Si el token es válido, el servidor permite el acceso a los recursos solicitados.
  Ventajas
### Escalabilidad:
Dado que no se almacenan sesiones en el servidor, es más fácil escalar horizontalmente la aplicación.
Simplificación del servidor: No es necesario manejar estados de sesión, lo que simplifica la lógica del servidor.
### Seguridad:
Los tokens pueden expirar automáticamente y pueden ser revocados si es necesario.
Desventajas
Complejidad en el cliente: El cliente debe manejar el almacenamiento y la transmisión del token.
Limitaciones de token: Si un token es comprometido, puede ser utilizado hasta que expire o sea revocado.
Para más información sobre la autenticación stateless, puedes consultar fuentes adicionales como Auth0 o JWT.io.