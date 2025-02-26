- Máquina:Escritorio Pr. Combinada Serv. Ap.
	- Instalado php
	- Instalado nginx
	- Instalado node
	- Instalado mysql
	- PENDIENTE php y complementos
    ![install PHP](img/installPHP.png)
	- Opcional phpmyadmin
    ![install phpmyadmin](img/installPHPMYADMIN.png)

- Despliegue 1:
	- Apache puerto 8080
	- http://localhost:8080
	- Aplicación demo de otros días.
    ![conf APACHE](img/configurarAPACHE.png)
	![conf APACHE](img/configurarAPACHE2.png)
    ![conf BBDD](img/configBBDD.png)
    ![conf DEMO](img/configuracion%20de%20DEMO.png)
    ![conf APACHE](img/listaUsuario.png)
- Despliegue 2
	- Node puerto 3000
	- http://localhost:3000
	- Aplicación demo de otros días
    ![conf NODE1](img/configNODE.png)
    ![conf NODE2](img/configNODE2.png)
    ![conf NODE3](img/configNODE3.png)
- Configuración proxy inverso
	- Sitio1: http://php.local	
	- Sitio1: http://node.local
	- Puerto 80
	- Recuerda que debes configurar el fichero hosts
    ![conf proxy](img/configPROXY.png)
    ![conf proxy](img/configPROXY2.png)
    
