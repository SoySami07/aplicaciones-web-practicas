## Crear 2 paginas distintas en mismo URL pero en distinto puerto

1. Creamos las carpetas con el comando sudo mkdir -p /var/www/smr/web /var/www/smr/intranet y añadiremos un fichero index.html e intranet.html y le añadimos el contenido que queremos a nuestras páginas
2. Seguidamente creamos el usuario con el que vamos a acceder a la intranet con el comando sudo htpasswd -c /etc/apache2/.htpasswd admin, y pedirá una contraseña 2 veces con la que accederemos cuando entremos a la página
3. Ahora vamos a la carpeta de puertos que hay en apache y le decimos que escuche el 9999
4. Copiamos ahora el archivo 00 de la carpeta sites-available y le ponemos SMR.conf

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

5. Ahora tenemos que habilitarlo y deshabilitarlo con los comandos sudo a2ensite smr.conf sudo a2dissite 000-default.conf sudo apachectl configtest sudo systemctl restart apache2
6. Y ahora ya si que podríamos acceder a nuestra página por la IP
7. Pero si queremos acceder por URL tenemos que, modificar el archivo que está en System32 drivers etc hosts, si tenemos windows y si tenemos linux sudo nano /etc/hosts
8. Ahora añadimos en una nueva linea 192.168.56.10 que es la ip del server
