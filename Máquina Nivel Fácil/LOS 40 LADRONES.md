# RESOLUCIÓN DE LA MÁQUINA LOS 40 LADRONES

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a8c82b33-79ac-4477-8cdc-9d17e1da434b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/aca6b559-4497-4720-b628-f142abe269e4)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a6b97029-4fac-4517-b323-3258661ce360)

Abrimos la página web, puerto 80 y no hay nada.

![image](https://github.com/user-attachments/assets/36c186fb-3fff-4da0-9c41-04050d18c67c)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/8011c247-7a87-43db-82dd-f84cb65ff6ae)

Abrimos el archivo txt que hemos encontrado.

![image](https://github.com/user-attachments/assets/a70b6d27-802f-41f8-99c1-e00aa9d21309)

Después de buscar información en internet: 

El port knocking es una técnica de seguridad que permite abrir puertos en un firewall solo después de que se haya enviado una secuencia específica de intentos de conexión a otros puertos cerrados previamente especificados.

Esta técnica se usa para ocultar servicios sensibles detrás de un firewall, haciéndolos accesibles solo después de realizar la secuencia correcta de "golpes".

En nuestro caso tendremos que "golpear", los puertos 7000, 8000 y 9000, en el orden dado.


Instalamos el knockd.

![image](https://github.com/user-attachments/assets/432e4653-a477-4a1e-a952-ffecc20d8b53)

Realizamos el port knocking con el orden que nos han dicho previamente.

![image](https://github.com/user-attachments/assets/8ab682fc-ecd3-41f1-9dbc-b5ac92386b7e)

Volvemos a escanear los puertos y nos encontramos con el servicio ssh disponible.

![image](https://github.com/user-attachments/assets/4dd19bfa-725d-4e4c-91fc-6ffb0d014f35)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/0044bbb6-6c57-4752-82a9-5f72e1862f1e)

En el archivo txt, nos daba una pista sobre un posible, haremos hydra para ver si es así y nos devuelve una contraseña.

![image](https://github.com/user-attachments/assets/c5a95b53-57e5-4fac-8c04-6c4e6a82de95)

Entramos al servico ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/09c8d181-8fac-4c04-a95b-c4e42778c45b)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/2ff59862-9adf-46f2-945b-6315efb53f06)

Y ya somos root.

![image](https://github.com/user-attachments/assets/9ad56f5d-dc5a-497c-bfed-4768378b6bfa)




