# RESOLUCIÓN DE LA MÁQUINA CANDY

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/2384d2d4-1deb-470c-b52f-0442ce8610b2)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/a2a45f09-a7b6-48f6-bb4b-b6b6fd438e74)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/8aab8ff0-7c59-4f88-9948-c262c7117b13)

Abrimos la página.

![image](https://github.com/user-attachments/assets/c73b21e3-bbc1-49dc-a09a-79db2dd083d7)

Abrimos el robots.txt, que haciendo nmap hemos visto que estaba abierto. 

![image](https://github.com/user-attachments/assets/cc410f8d-6698-4a8c-8ad5-f9b00acdd638)

Vamos al directorio /un_caramelo

![image](https://github.com/user-attachments/assets/2891f824-218d-4cb5-b43d-76a0a1cc030e)

Dentro de esta página encontramos las mismas credenciales que en el robots.

![image](https://github.com/user-attachments/assets/b1ebdb86-6e92-4b76-bb3a-f4c404e8e6fc)

Vamos a decodear la credencial para ver si nos devuelve información útil.

![image](https://github.com/user-attachments/assets/4e38f509-fdb8-434d-ba68-9754875bcc9f)

Vamos al login de joomla que hemos encontrado.

![image](https://github.com/user-attachments/assets/1b6847c4-1392-4a4d-b02e-0a6c56ddc9c8)

Introducimos las credenciales y nos logueamos.

![image](https://github.com/user-attachments/assets/03dc2da7-df86-447c-bf66-1a812eed3023)

Después de buscar un rato encontramos un archivo index.php, en el que añadimos un comando malicioso.

Este archivo esta en la ruta: system / site templates / cassiopeia / index.php

![image](https://github.com/user-attachments/assets/28518075-38ba-4aa5-a261-9fdc15b46465)

Inyectamos código en la ruta principal y funciona.

![image](https://github.com/user-attachments/assets/1f00b775-078f-42cd-a8bb-53d53cf6419f)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/2495d646-8a28-42a2-8c21-116156404b3f)

Nos encontramos un archivo en el directorio var.

![image](https://github.com/user-attachments/assets/9b4fc058-1679-4091-a55e-fad3faab0771)

![image](https://github.com/user-attachments/assets/3b193ec6-921a-44ee-ac09-1b9c048056c5)

Nos conectamos como usuario luisillo con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/87c7a2c9-8a0f-48c0-a8c8-e799b904d325)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/0110bde3-d27c-46e8-99ee-4acecd165374)

Esta vulnerabilidad me permite escribir en cualquier archivo cualquier cosa asi que se me a ocurrido darme a luisillo permisos para ejecutar cualquier cosa como root sin contraseña.

Y de esta manera conseguimos ser root.

![image](https://github.com/user-attachments/assets/6fcdb2a6-9296-4858-8483-53f5bc3ffd72)











