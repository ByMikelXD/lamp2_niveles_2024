# lamp2_niveles_2024
### Creamos los sh de arpivisonamiento de las dos maquinas virtuales
#### Script para MySQL
![](FOTOS/15.png)
#### Script para Apache2
![](FOTOS/14.png)
### Una vez creados los scripts, configuraremos el Vagrantfile agregando ambas maquinas y aplicando el aprovisionamiento
![](FOTOS/)
### Una vez configurado todo, ponemos **vagrant up** y se empezaran a levantar ambas maquinas. Para comprobar que no han habido errores al iniciar las maquinas con el comando **vagrant status** podemos ver el estado de estas.
![](FOTOS/)

# Configuracion MySQL
### Lo primero que hay que hacer es entrar en el directorio */etc/mysql/mariadb.conf.d* y ahí modificar el fichero *50-server.cnf*.
![](FOTOS/3.png)
### En este fichero cambiaremos la *bind-address* y pondremos la ip de nuestra maquina sql.
![](FOTOS/4.png)
### Ahora entramos a mysql como root y creamos un usuario con la ip de la maquina apache y le daremos todos los permisos en la base de datos que deseemos.
![](FOTOS/1.png)
### En el home de esta maquina clonaremos el repositorio de git para poder descargar la base de datos.
![](FOTOS/2.png)
### Ahora entraremos a la carpeta creada y dentro de esta accederemos a db. Despues de esto en el fichero *database.sql* borraremos las ultimas 3 lineas y la aplicaremos a nuestro MySQL.
![](FOTOS/5.png)

# Configuracion APACHE
### Creamos una carpeta en */var/www* y le cambiamos el propietario con **chown**. Despues clonamos el repositorio de github con **git clone** y el enlace del repositorio que queremos usar.
![](FOTOS/6.png)
### Entramos en la carpeta creada y dentro de esta entramos en *src*. Ahora movemos todo lo de esta carpeta a la carpeta que hemos creado en */var/www* y comprobamos que se hayan movido correctamente.
![](FOTOS/7.png)
### Nos vamos a la carpeta de sites-available en */etc/apache2* y copiamos el fichero de configuración para modificarlo a nuestro gusto.
![](FOTOS/8.png)
### Con sudo nano a el nuevo archivo de configuración ponemos la ruta de la carpeta que hemos creado en */var/www*.
![](FOTOS/9.png)
### Ahora habilitamos el fichero de configuración con **a2ensite**. 
![](FOTOS/10.png)
### Ahora nos vamos a */etc/apache2/sites-enabled* y desactivamos el fichero de configuración anterior con **a2dissite**. Despues de esto recargamos el apache2 con **sudo systemctl reload apache2**.
![](FOTOS/11.png)
### Lo siguiente es entrar en la carpeta creada en */var/www* y editar el fichero config.php.
![](FOTOS/12.png)
### En este fichero donde pone localhost ponemos la ip de la maquina de sql y cambiamos los datos de user y password.
![](FOTOS/13.png)
### Instalamos el mysql-client con **sudo apt install -y default-mysql-client**.
### Ahora entramos a mysql con **mysql -u nombreusuario -p -h ipmysql**.
![](FOTOS/16.png)
![](FOTOS/17.png)
### Ahora si ponemos la dirección de la maquina de apache en Google saldrá la pagina del LAMP.
