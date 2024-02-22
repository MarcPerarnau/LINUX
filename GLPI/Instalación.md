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

Despues de la instalacion del apache se iniciara automáticamente, para verificar el servicio ejecutaremos el siguiente codigo.
```sh
sudo systemctl status apache2
----------------------------
sudo service apache2 status
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/97262548-1860-4f31-b705-383b2c660aa3)

En caso de que en la ejecicción no sea igual que la de la imagen utilizaremos el siguiente codigo: 
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
Despues de la instalación porcedemos a asignar una contraseña al usuario root
```sh
sudo mysql
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/227bdaa0-d1b8-437c-995f-d21706c2e7c5)
Para conocer el registro deseado necesitaremos hacer una consulta.
```sh
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/5c8902d7-4425-49af-b390-3ed5c7fba126)
Una vez identifiquemos el usuario haremos un registro alterno
```sh
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; #Password sera la contraseña deseada
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/6c366166-521c-4369-a8ee-e4e9dcca361a)

# Instalación PHP


