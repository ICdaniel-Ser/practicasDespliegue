# Práctica 2. DNS

Servicio de DNS

## Objetivos

- Conocer el funcionamiento del servicio DNS
- Conocer los distintos registros asocidados a un dominio DNS.
- Conocer cómo suplantar el DNS de forma local.

## Qué entregar

- Toma el fichero markdown del repositorio del profesor y añádelo a tu repositorio de prácticas
- Añade los comentarios y fotos que expliquen y justifiquen tu trabajo.
- Vamos aprovechar esta práctica para aprender a añadir etiquetas en git:
  - https://git-scm.com/book/es/v2/Fundamentos-de-Git-Etiquetado
  - Definie una etiqueta P1 asocida al commit con el que terminas tu trabajo. Puedes hacerlo de una de estas maneras:
    - `git tag -a P2 <hash del commit>`
    - `git tag -a P2 -m 'Práctica 2 acabada'`
  - Sube tu trabajo y la etiqueta:
    - `git push origin P2`  //para subir la etiqueta
    - `git push origin --tags` //para subir todas las etiquetas
- Respeta la fecha de entrega.

### Herramientas de diagnóstico

- Toma un dominio público de acuerdo a tu número de alumno:
  1. gitlab.com
  2. bitbucket.com
  3. android.com
  4. trello.com
  5. atlassian.com
  6. ibercaja.es
  7. facebook.com
  8. twiter.com
  9. bbva.es
  10. instagram.com
  11. wikipedia.com
  12. elpais.com
  13. marca.com
  14. heraldo.es
  15. apple.com

- Intenta resolver las siguientes preguntas con con las 3 herramientas presentadas: host,nslookup y dig.
  - Busca la IP asignada

    ![Captura de pantalla IP host](ImagenesPractica2/cap1IpHost.png)

    ![Captura de pantalla nslookup](ImagenesPractica2/cap2nslookup.png)

    ![Captura de pantalla dig](ImagenesPractica2/cap3dig.png)

  - Quien resuelve su DNS

    ![Captura de pantalla dig 2](ImagenesPractica2/Cap4digNS.png)

  - Cuál es el servidor de correo electrónico. Si hay varios, determina cual es primero por su prioridad.

    ![Captura de pantalla host 2](ImagenesPractica2/Cap5Host.png)

    ![Captura de pantalla nslookup 2](ImagenesPractica2/Cap6nslookup.png)

    ![Captura de pantalla dig 3](ImagenesPractica2/Cap7dig.png)

  - Haz la búsqueda de forma autorizada, es decir, que el servidor que contesta sea uno de los registos NS del dominio.

    ![Captura de pantalla dig ](ImagenesPractica2/Cap8Dig.png)

    ![Captura de pantalla dig ](ImagenesPractica2/Cap9Dig.png)

    ![Captura de pantalla dig ](ImagenesPractica2/Cap10Dig.png)

### Suplantar servicio DNS localmente.

- Edita el fichero `/etc/hosts` para que resuelva un nombre de dominio falso con el siguiente esquema: 

  ![Captura de pantalla  ](ImagenesPractica2/Cap12.5.png)

  ![Captura de pantalla  ](ImagenesPractica2/Cap12.png)
  
  - `miapellido.local` asociado a la dirección 127.0.0.1
  - `miapellido.es` asociado a una dirección pública inventada.
  - `miapellido.com` asociado a la dirección del dominio de la primera parte de la práctica. Si eres el nº 1 sería `github.com`

  ![Captura de pantalla  ](ImagenesPractica2/Cap11.png)

- Comprueba la resolución de los tres registros con alguna de las herramientas de diagnóstico.

  ![Captura de pantalla  ](ImagenesPractica2/Cap13.png)

- Comprueba la misma resolución pero haciendo que el servidor consultado sea el 8.8.8.8

  ![Captura de pantalla  ](ImagenesPractica2/Cap14.png)

  ![Captura de pantalla  ](ImagenesPractica2/Cap15es.png)

  ![Captura de pantalla  ](ImagenesPractica2/Cap16com.png)

### Configuración del servidor  DNS con BIND9

- Configura el dominio `miapellido.edu` en bind9. Debes hacerlo:
  - En el servidor linux
  - Conectándote al mismo mediante SSH
  - Utiliza las direcciones IP de tu red privada (192.168.1xx.0/24)

  ![Captura de pantalla ](ImagenesPractica2/conectarServidor.png)

  - Deberás usar un fichero con un nombre similar a este: *db.miapellido.edu*
- Debes definir:
  - Número de versión 1
  - Un correo de administrador dentro del dominio.
  - Dos registros MX.
  - Dos registros NS con máquinas del propio dominio (por ejemplo *dns1* y *dns2*).
  - Varios registros A, al menos: *www, dns1, dns2*
  - Un registro CNAME asociado a la misma dirección que *www*

  ![Captura de pantalla ](ImagenesPractica2/Cap17.png)

- Para comprobar que tu configuración es correcta debes:
  - Usar el comando de verificación sintáctica.
  - Reiniciar el servicio
  - Probar la resolución usando nslookup y dig. Ojo, la resolución de nombres debe correr a cargo del servidor Ubuntu.
- Trabajo extra. Para mejorar tu calificación se te propone:
  - Añadir una zona de resolución inversa
  - Instalar Bind9 en el cliente Ubuntu y definirlo como DNS esclavo del primero.