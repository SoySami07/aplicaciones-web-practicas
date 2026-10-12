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
2. Cuando ya lo hayamos comprobado 
