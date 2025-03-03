# Práctica de despliegue con Docker

## Punto de partida

- Usa la máquina: "Practicas Docker Ubuntu"
- Borra todos los contenedores e imágenes:

  ```bash
  docker rm -f $(docker ps -aq)
  docker rmi -f $(docker images -aq)
  ```
  docker rm -f $(docker ps -aq)
  ![Imagen punto de partida 1](img/imgInicio1.png)
  docker rmi -f $(docker images -aq)
  ![Imagen punto de partida 2](img/imgInicio2.png)
## Objetivo

- Debes desplegar las siguientes aplicaciones:
  - https://github.com/rafacabeza/demoapinode
  - https://github.com/rafacabeza/demoappphp
- Debes usar un contenedor con un proxy.
- Debes usar un contenedor por cada aplicación y dos contenedores de bases de datos.
- Opcionalmente puedes usar contenedores para phpmyadmin
- Las aplicaciones serán app1.local y app2.local.

## Desarrollo de la práctica

- Para hacerlo debes usar un único fichero docker-compose.yml teniendo en cuenta lo siguiente:
  - Inicia el proceso clonando el repositorio entornods(https://github.com/rafacabeza/entornods)
  ![Clonamos el repositorio](img/clonacionEntorn.png)
  - Elimina el servicio web1
  ![Eliminacion del servicio web1 1](img/comandoWeb1.png)
  ![Eliminacion del servicio web1 1](img/mostrandoWeb1.png)
  ![Eliminacion del servicio web1 1](img/eliminadoWeb1.png)
  - Comprueba que funciona correnctamente el sitio web2.com (deberas editar el fichero hosts)
  ![Comprobando el sitio web2](img/ConfiguracionWeb2.png)
  ![Comprobando el sitio web2](img/ConfiguracionWeb2_2.png)
  ![Comprobando el sitio web2](img/docker1.png)
  ![Comprobando el sitio web2](img/docker2.png)
  ![Comprobando el sitio web2](img/web2Furrula.png)
  - Deja una única red (network) en todos los contenedores. Llámale como consideres.
  ![Una unica red](img/proxyMired.png)
  ![Una unica red](img/dbMired.png)
  ![Una unica red](img/web2Mired.png)
  ![Una unica red](img/phpMired.png)
  ![Una unica red](img/network.png)
  ![Una unica red](img/downDocker.png)
  ![Una unica red](img/downDocker2.png)
  ![Una unica red](img/dockerNetwork.png)
  ![Una unica red](img/newCompose.png)
  ![Una unica red](img/newCompose2.png)

### Sitio app1.local

- Añade un servicio db1 (puedes renombrar el servicio db como db1)
  - El volumen de datos debe llamarse volumen1 y debe gestionarlo docker
  - Debes usar una base de datos llamda dbapp1 
  - Debes usar un usuario user1 y contraseña secret
  ![ BBDD](img/configBBDDapp1.jpg)
  ![Servicio db1](img/creacionDB1.png)
  ![Servicio db1](img/db1Corriendo.png)
  - Carga el sql correspondiente. Puedes hacerlo con phpmyadmin o mediante consola (docker exec -it <contenedor> mysql ....).
  ![Cargar datos de la BBDD](img/datosBBDD.png)
- Añade un servicio app1 para que sirva la aplicación "demoapinode". 
  - Descarga la aplicación en "entornods/demoapinode".
  ![Demoapinode](img/entornoDemoapi.jpg)
  - Fíjate en el docker-compose.yml que hay en el repositiro, te ayudará a definir el servicio en tu docker-compose pero deberás modificar algunas cosas.
  - Deberás añadir en variable de entorno "VIRTUAL_HOST", fíjate en web2
  - Revisa el resto de parámetros
  ![Configuracion App1 ](img/configApp1.jpg)
- Comprueba que funciona la ruta: http://app1.
  ![app1](img/app1Local.jpg)

### Sitio app2.local

- Añade un servicio db2 para la base de datos de "demoappphp"
  - El volumen de datos debe llamarse volumen2 y debe gestionarlo docker
  ![Configuracion app2](img/configApp2.jpg)
  ![Configurar app2](img/buildApp2.jpg)
  ![Configurar app2](img/buildApp2_2.jpg)
  - Debes usar una base de datos llamda dbapp2 
  - Debes usar un usuario user2 y contraseña secret
  ![Configurar BBDD](img/ajustesBBDD.jpg)
  - Carga el sql correspondiente. De nuevo, puedes usar phpmyadmin o la consola.
  ![Configurar BBDD](img/bbddApp2.jpg)
- Añade un servicio app2 que sirva la aplicación "demoappphp"
  - Descarga la aplicación en "entornods/demoappphp".
  ![Demoappphp](img/entornoDemoApiPhph+.jpg)
  - Fíjate en el docker-compose.yml que ha en repositorio, te ayudará a definir el servicio en tu docker-compose pero deberás modificar algunas cosas.
  - Deberás añadir en variable de entorno "VIRTUAL_HOST", fíjate en 
  ![Configuracion app2](img/configApp2.jpg)
- Comprueba que funciona la ruta: http://app2.local/api/deseos
  ![app2](img/app2Local.jpg)

### Un poco más de documentación. 

- Si te da tiempo, como tarea extra:
  - Muestra una lista de todos las redes y volúmenes  

    ```
    docker volume ls
    docker network ls
    ```

- Identifica la red y volúmenes utilizados y captura los datos de los mismos:

    ```
    docker inspect <nombre-volumen>
    docker inspect <nombre-red>
    ```# Práctica de despliegue con Docker

