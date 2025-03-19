- Máquina:Escritorio Pr. Combinada Serv. Ap.
	- Instalado php
	- Instalado nginx
	- Instalado node
	- Instalado mysql
	- PENDIENTE php y complementos
	- Opcional phpmyadmin
	![Creacion Base De Datos](img/creacionBBDD.png)
	![Tabla Deseos](img/tablaDeseos.png)
	![Tabla Usuarios](img/tablaUsuarios.png)

- Despliegue 1:
	- Apache puerto 8080
	- http://localhost:8080
	- Aplicación demo de otros días.
	![clonamos la api de php](img/clonacionApiphp.png)
	![Configuramos los puertos](img/demoapphpConf.png)
	![Ports](img/portsApache.png)
	![Ajustes](img/ajustesApache.png)
	![Ajustes](img/ajustesApache2.png)
	![Final](img/capturaFinal2.png)
	
- Despliegue 2
	- Node puerto 3000
	- http://localhost:3000
	- Aplicación demo de otros días
	![Copiamos Api node](img/clonacionApinode.png)
	![Instalamos npm](img/npmInstall.png)
	![Npm Start](img/npmStart.png)
	![Server corriendo en localhost 3000](img/serverCorriendo.png)
	![Final](img/capturaFinal1.png)
- Configuración proxy inverso
	- Sitio1: http://php.local	
	- Sitio1: http://node.local
	- Puerto 80
	![Configuramos Proxy inverso](img/nanoProxy.png)
	![Configuramos Proxy inverso](img/proxy2.png)
	- Recuerda que debes configurar el fichero hosts
	![Configuramos host](img/host.png)
	
	
	
	