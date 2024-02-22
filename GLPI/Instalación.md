Lo primero que haremos sera instalar y actualizar el ubuntu.
```sh
sudo apt update && sudo apt upgrade -y #Utilizamos el -y para que automaticamente diga que si a la instalación
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/e2dfd448-32e2-4789-b114-e4e5eddc4c91)
# Instalación Apache2
Despues instalamos apache2.
```sh
sudo apt install apache2 -y
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/2638127a-741f-43c6-9523-de202d1b5797)

<br>Despues de la instalacion del apache se iniciara automáticamente, para verificar el servicio ejecutaremos el siguiente codigo.
```sh
sudo systemctl status apache2
----------------------------
sudo service apache2 status
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/97262548-1860-4f31-b705-383b2c660aa3)

<br>En caso de que en la ejecicción no sea igual que la de la imagen utilizaremos el siguiente codigo: 
```sh
sudo systemctl start apache2
----------------------------
sudo service apache2 start
```
# Instalación MySQL
Instalamos MySQL
```sh
sudo apt install mysql-server
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/c9656d9f-348d-43d2-8558-53300f9791fd)
<br>Despues de la instalación porcedemos a asignar una contraseña al usuario root
```sh
sudo mysql
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/227bdaa0-d1b8-437c-995f-d21706c2e7c5)
<br>Para conocer el registro deseado necesitaremos hacer una consulta.
```sh
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/5c8902d7-4425-49af-b390-3ed5c7fba126)
<br>Una vez identifiquemos el usuario haremos un registro alterno
```sh
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; #Password sera la contraseña deseada
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/6c366166-521c-4369-a8ee-e4e9dcca361a)

# Instalación PHP
Instalamos PHP y las extensiones necesarias con el siguiente comando:
```sh
sudo apt install php libapache2-mod-php
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/e566bfa3-65e1-410f-ab2a-fb3f4c55ddc8)
# Preparación archivos GLPI
Lo primero sera descargar GLPI en la versión 10.0.7
```sh
wget https://github.com/glpi-project/glpi/releases/download/10.0.7/glpi-10.0.7.tgz
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/c6a8244f-6bd4-4bc4-b268-420f5889d8f4)
<br>Extraemos el archivo glpi-10.0.7.tgz
```sh
tar -xzf glpi-10.0.7.tgz
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/942b2219-02be-4dbb-a61b-d38d1b602e50)
<br>Ahora movemos la carpeta glpi a la carpeta del servicio web
```sh
sudo mv glpi /var/www/html/
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/6eb832fc-39c9-4aaa-9bbf-1349c543f23a)

# Iniciamos la Instalación
Lo primero sera seleccionar el idioma, para la practica usamo el Español (España).<br>
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/f57e1f93-5b64-4e9f-9e06-66c860b854f2)
<br>Ahora tocara aceptar la licencia.<br>
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/2c537249-7a93-4cf9-8668-f0cf465fd9a8)
<br>Ahora tendremos que seleccionar la opción Instalar.<br>
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/07d6aa1f-58da-49a5-8807-c20babe59b45)
<br>Ahora verificaremos la compatibilidad, normalmente nos dara diferentes errores.
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/3e8e93ea-d91a-4610-a992-1c5556d89416)
<br>Para solventar los errores tendremos que configurar la seguridad de Apache: 
```sh
sudo shown -R www-data:www-data /var/www/html/glpi/
```
Para mysql extensión
```sh
sudo apt install php8.1-mysql
```
PHP core extensions
```sh
sudo apt install php8.1-xml
```
curl extensión
```sh
sudo apt install php8.1-curl
```
gd extensión
```sh
sudo apt install php8.1-gd
```
intl extensión
```sh
sudo apt install php8.1-intl
```
ldap extensión
```sh
sudo apt install php8.1-ldap
```
PHP extendions for marketplace
```sh
sudo apt install php8.1-bz2 php8.1-zip
```
PHP emulated extensions
```sh
sudo apt install php8.1-mbstring
```
Tambien podemos instalar-lo en una sola linea
```sh
sudo apt install php8.1-{mysql,xml,curl,gd,intl,ldap,bz2,zip,mbstring} php-cas
```
Ahora tendremos que reiniciar el sistema
```sh
sudo systemctl restart apache2
------------------------------
sudo service apache2 restart
```
Una vez le daremos al boton de reiniciar, esperaremos y despues le daremos a continuar. <br>
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/2c28436b-9f90-46c0-bba9-1e8ef6248333)<br>
Ahora nos connectaremos a GLPI agregando los siguientes campos: <br>
Réplicas SQL (MariaDB o MySQL): localhost. <br>
Usuario SQL: root <br>
Password SQL: La contraseña que hemos configurado anteriormente.
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/a086cbfc-f31f-4918-a95f-87ef0cc64248) <br>









