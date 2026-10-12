## Instalación Ubuntu Server

1. Hacemos clic en Nueva y creamos una máquina virtual y hacemos la configuración básica, poniendo el nombre que queremos y seleccionando nuestra ISO, y si el check está activado lo tenemos que desactivar.
2. Ponemos 2MB de memoria, 2 CPUs y 25GB de espacio del disco y ya le damos a siguiente y finalizamos.
3. Y ya podemos iniciar la máquina.


## Configuración Ubuntu Server

1. Lo primero es elegir el idioma que queremos.
2. Luego tenemos una actualización del instalador, así que lo actualizaremos.
3. Aquí tenemos la distribución del teclado.
4. Elegiremos Ubuntu Server para el tipo de instalación.
5. Le daremos a Done es la Network configuration y más adelante la configuraremos.
6. El proxy lo dejamos en blanco y el mirror address por defecto.
7. Usaremos el disco duro que es el que le hemos puesto en VB y después le daremos a Done.
8. Ahora ponemos el nombre de usuario, el server y la contraseña.
9. En el apartado de upgrade a Ubuntu Pro nos lo saltaremos.
10. Marcaremos la casilla de Install OpenSSH Server.
11. No queremos instalar ningún snap.
12. Y cuando haya terminado la instalación le daremos a Reboot Now.


## Red host-only y configuración del 2º adaptador

1. Le damos a Achivo, luego herramientas y luego a Red, y le daremos a crear.
2. Le daremos a doble clic y deshabilitaremos a DHCP y le daremos a aplicar.
3. En la configuración de la máquina y en el apartado de red seleccionaremos el 2º adaptador.
4. Y habilitaremos y conectaremos a Adaptador Only, y le damos a aceptar e iniciamos la máquina.
5. Ahora si ponemos ls /etc/netplan veremos el archivo para editar la IP.
6. Pondremos sudo nano y el archivo con la raíz.
7. Ahora escribiremos enp0s8 a la misma altura de enp0s3 y debajo escribiremos dhcp4: false.
8. Y en la misma altura de dhcp4 pondremos addresses.
9. Y debajo escribimos la IP.
10. Y ya podremos salir del archivo y escribir sudo netplan try y le damos al enter.


## Conectarse desde la máquina real

1. Lo primero es ver si hay conectividad haciendo ping a la IP que ya hemos configurado.
2. Cuando ya lo hayamos comprobado pondremos en la terminal ssh Usuario@IP del servidor.
3. Escribiremos la contraseña de la MV y estaremos dentro.


## Instalación Apache2

1. Lo primero es poner el comando sudo apt-get install apache2.
2. Y seguidamente systemctl status apache2, así comprobamos el estado del servicio.
3. Aora ponemos a cd /etc/apache2.
4. Y entramos en la carpeta de sites-available y entramos en el archivo 000-default y vamos a la ruta donde indica donde está nuestra página.
5. Cuando entramos al archivo de la ruta lo que escribimos en HTML es lo que va a aparecer en la página.


## Deshabilitar la antigua página y crear una nueva página

1. En el sites-available tenemos el archivo 000 lo duplicamos y lo llamamos smr.conf
2. Editaremos el archivo duplicado y donde está la ruta añadimos /smr.
3. Ahora vamos a la ruta /var/www/html y con mkdir creamos la carpeta smr.
4. dentro de esa carpeta creamos con el comando nano un fichero llamado index.html y añadiremos lo que queramos que se vea en la web.
5. Volvemos donde está instalado apache y entramos a sites-available y desactivamos el dichero antiguo con a2dissite 00.
6. Ahora ponemos un systmenctl reload apache2 y seguidamente un status.
7. Seguidamente ponemos a2ensite smr.conf para habilitar la nueva página y pondremos otra vez reload y status.
8. Y entramos en el archivo smr.conf y cambiamos el Virtual Host a 7654 y volvemos a poner reload.
9. Y ahora ponemos el archivo ports de apache2 y añadimos Listen 7654 y volvemos a hacer reload.


## 2 páginas en la misma URL pero distinto puerto

1. Lo primero es crear las carpetas con sudo mkdir -p /var/www/sm/web /var/www/smr/intranet y añadiremos un fichero index.html e intranet.html y luego añadimos el contenido a nuestras páginas.
2. Luego creamos el usuario con el que accederemos a la intranet con sudo htpasswd -c /etc/apache2/htpasswd admin y pedirá que pongamos una contraseña 2 veces, que será con la que accederemos a la página.
3. Ahora vamos a la carpeta de puertos que está en apache y le diremos que escuche el 9999.
4. Y copiamos el archivo 00 de la carpeta sites-available y lo llamamos SMR.conf.
5. Así tendría que quedar:

<VirtualHost *:80>
        ServerName www.smr.com
        DocumentRoot /var/www/smr/web
</VirtualHost>

<VirtualHost *:9999>
        ServerName www.smr.com
        DocumentRoot /var/www/smr/intranet
        DirectoryIndex intranet.html


        <Directory /var/www/smr/intranet>
                AuthType Basic
                AuthName "Intranet SMR"
                AuthUserFile /etc/apache2/.htpasswd
                Require valid-user
        </Directory>
</VirtualHost>

6. Y ahora habilitamos y deshabilitamos con los comandos sudo a2ensite smr.conf sudo a2dissite 000-default.conf sudo apachectl configtest sudo systemctl restart apache2
7. Y ahora ya podríamos acceder por IP.
8. Pero para acceder por URL tenemos que modifica el archivo que está en System32 srivers etc hosts, pero si es linux sudo nano /etc/hosts
9. Y ya dentro añadimos en otra linea nueva 192.168.56.10 que es la IP del server (www.smr.com).
