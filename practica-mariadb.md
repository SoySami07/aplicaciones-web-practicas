# Práctica: MariaDB y PHP en Ubuntu 24.04 (LAMP)

**Nombre:** [tu nombre] · **Curso:** [curso] · **Fecha:** [fecha]

## 1. Preparación
```bash
sudo apt update
systemctl is-active apache2
```
![Apache activo](img/01-apache-active.png)

Actualizo los paquetes y compruebo que Apache funciona (`active`).

## 2. Instalación de MariaDB
```bash
sudo apt install mariadb-server -y
mariadb --version
```
![Versión de MariaDB](img/02-mariadb-version.png)

Instalo el gestor de la base de datos. La versión es MariaDB 10.11.

**Pregunta:** `mariadb-server` es el programa que guarda y gestiona los datos. `mariadb-client` es la herramienta para conectarse a él. He instalado `mariadb-server`, que incluye el cliente.

## 3. Comprobación del funcionamiento
```bash
sudo systemctl status mariadb
systemctl is-enabled mariadb
sudo mariadb
```
![Estado de MariaDB](img/03-mariadb-estado.png)

El servicio está `active (running)` y `enabled`. Con `sudo mariadb` entro en la consola y salgo con `exit`.

**Pregunta:** `active (running)` significa que funciona ahora mismo. `enabled` significa que arranca solo al encender el equipo. Si estuviera active pero no enabled y se reiniciara el servidor, MariaDB no arrancaría y WordPress daría error de conexión con la base de datos.

