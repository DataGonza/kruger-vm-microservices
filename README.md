# kruger-vm-microservices
Technical test for java backend developer

Un gusto saludate estimado visitante, espero que disfrutes explorando esta API como yo haciendola.

Lastimosamente el tiempo ha sido corto, pero me siento bien de entregar un trabajo de calidad.  
A continuación todas las observaciones necesarias sobre este proyecto.

## Infraestructura:
- Servidor de autenticacion: Keycloak 20.0.1
- Base de datos: Postgres
- Backend: Java 11 + Spring Boot 2.7.9
- Docker

## Requsitos de tu sistema:
- Java 11
- maven
- docker
- Postman (Opcional, pero muy recomendado)
- Visualizador de OpenApi 3+ (Opcional, menos recomendado que postman)
- Puertos libres del host: 5432, 8180, 8080, 5050

## Pasos para ejecutar el proyecto:
- `git clone https://github.com/DataGonza/kruger-vm-microservices.git`
- `cd kruger-vm-microservices/`
- `unzip infrastructure.zip` (Son los datos para tener listo el servidor de autenticación y la base de datos)
- `mvn clean install`
- `sudo chown -R 5050:5050 ./infrastructure/pgadmin` (Es para que la interfaz de la base de datos tenga accesso a sus datos)
- `sudo chown -R dgonzalez: ./infrastructure/` (El servidor de autentcacion necesita que esa carpeta pertenezca a dgonzalez)
- `sudo docker compose up` (Levanta el servidor de autenticación y la base de datos)
- `mvn spring-boot:run` (Por favor espera un par de minutos antes de correr este comando, si puede acceder a http://localhost:8180/ es el momento adecuado)
- El perfil inicial con accesso a los enpoints de admin es: *user*: dgonzalez, *password*: admin
- La app se ejecuta sobre el puerto 8080

## Validar el funcionamiento:
- Para este propósito me he esmerado en hacer una colección de postaman lo más clara posible, la tienes a tu disposición  
Si no, siempre está el viejo camino de curl en base al .yml  
- En caso de inclinarte por postman. En el POST login puedes ir cambiando las claves, los tokens se refrescan automáticamente.  
Solo debes cambiar el user y password para ir switcheando entre perfiles.
- En el archivo entities.yml puedes encontrar la representación de las dos entidades que se ocupa con anotaciones para  
facilitar el envio de post y put.

# Happy Testing!!!

Nota: En caso de estar querer explorar los otros servidores, te dejo lo que puedes necesitar:
- pgadmin (puerto 5050): La clave para ver los datos es xX9ERnuZf9Q6aiW
- keycloak (puerto 8180): Puedes apreciar la creación y eliminación de usuarios mientras usas los endpoints, usuario y psw: admin