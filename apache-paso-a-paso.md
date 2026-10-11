# Apache Paso a Paso

## Primer paso

Creo una carpeta para cada web y dentro su página, la de intranet se llama intranet.html en vez de index.html con los siguientes comandos:
sudo mkdir -p/var/www/smr/web /var/www/smr/intranet
echo "<h1>Bienvenidos a SMR</h1>" | sudo tee /var/www/smr/web/index.html
echo "<h1>Intranet de SMR</h1>" | sudo teee /var/www/smr/intranet/intranet.html

Y para comprobarlo con ls -R /var/www/smr


## Segundo paso

Creo el usuario 'alumno' con una contraseña y se gaurda en el fichero .htpasswd
sudo htpasswd -c /etc/apache2/.htpasswd alumno


## Tercer paso

Apache solo escucha el puerto 80 por defecto. Para que también escuche el 9999 edito 'ports.conf'
sudo nano /etc/apache2/ports.conf

Listen 80
Listen 9999


## Cuarto paso

He hecho un solo fichero con dos bloques 'VirtualHost', uno para cada puerto
sudo nano /etc/apache2/sites-available/smr.conf

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


## Quinto paso

Activo mi sitio, desactivo el que viene por defecto, compruebo que no hay errores y reinicio
sudo a2ensite smr.conf
sudo a2dissite 000-default.conf
sudo apachectl configtest
sudo systemctl restart apache2


## Sexto paso

Miro la IP de la VM con ip a y la pongo en el navegador del anfitrión
http://192.168.56.XX sale "Bienvenidos a SMR"
http://192.168.56.XX:9999 pide usuario y contraseña y después sale "Intranet de SMR"

### Desde una segunda VM

Poner las dos VMs en la misma red: con las dos apagadas, en VirtualBox voy a Configuración, Red, Adaptador 2, lo habilito y lo pongo en Adaptador solo-anfitrión con el mismo nombre de red en las dos

Las arranco y con ip a veo que cada una tiene una IP de la misma red: 
VM servidor: 192.168.56.XX
VM cliente: 192.168.56.XX

Comprueba que se ven con un ping desde la cliente:
ping -c 4 192.168.56.XX

En la VM cliente abro /etc/hosts y añado la IP del servidor con el nombre
sudo nano /etc/hosts
192.168.56.XX www.smr.com

Ahora desde la VM cliente pruebo http://www.smr.com y http://www.smr.com:9999 y funcionan igual que con la IP

