Lo primero que haremos sera instalar y actualizar el ubuntu.
```sh
sudo apt update && sudo apt upgrade -y #Utilizamos el -y para que automaticamente diga que si a la instalación
```
![image](https://github.com/MarcPerarnau/LINUX/assets/151735878/e2dfd448-32e2-4789-b114-e4e5eddc4c91)

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
