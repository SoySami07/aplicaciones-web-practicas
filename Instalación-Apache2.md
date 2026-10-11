## Instalación apache2

1. Lo primero es escribir sudo apt-get install apache2 y ponemos systemctl status apache2 para comprobrar el estado del servicio
2. Ahora vamos a cd /etc/apache2 y entramos a la carpeta sites-available y luego entramos en el archivo 000-default y vamos a la ruta donde está nuestra página
3. Y cuando estamos dentro del archivo de la ruta y lo que escribimos en el HTML se verá en la página

## Deshabilitar pagina y crear otra

1. El archivo 000 que se encuentra en sites-available lo duplicamos y lo llamamos smr.conf
2. Luego tenemos que editar el archivo duplicado y donde está la ruta añadimos /smr
3. Ahora vamos a la ruta /var/www/html y con mkdir creamos otra carpeta smr
4. Dentro de esa carpeta creamos con el comando nano un ficheo llamado index.html y escribimos lo que queremos que sea vea en la web
5. Volvemos donde tenemos instalado apache y entramos en sites-available y desactivamos el fichero antiguo con el comando a2dissite 00
6. Ahora escribimos systemctl reload apache 2 y luego status para que se aplique y luego comprobar que va bien
7. Ahora ponemos a2ensite smr.conf para habilitar nuestra nueva página y ahora otra vez un reload y status
8. Entramos en el archvio smr.conf y cambiaremos el virtual host a 7654 y hacemos reload
9. Y ahora modificamos el archivo ports de apache2 y luego añadimos Listen 7654 y hacemos otra vez reload
