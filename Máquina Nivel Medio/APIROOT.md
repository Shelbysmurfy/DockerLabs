# RESOLUCIÓN DE LA MÁQUINA APIROOT

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/d2e21d23-90bd-43b6-8582-0da1a616e6ff)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/3e539114-c70a-4fc8-98b7-fb914eb11f7a)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/710a90b8-5d06-4b33-8b7b-784bad8961ff)

Abrimos la web, por el puerto 5000.

![image](https://github.com/user-attachments/assets/66755974-09ad-4e2d-98b6-d499175fd17d)

Hacemos fuerza bruta con gobuster a partir de el directorio /api, que nos mencionan en la web.

![image](https://github.com/user-attachments/assets/6f72cc37-2f07-430d-a208-88704b82ea67)

Abrimos el directorio /users y nos muestra esto: 

![image](https://github.com/user-attachments/assets/47e37947-48ce-446b-954e-2248458c3d62)

En la web nos da esta pista, pero nos hace falta la "Authorization", por tanto vamos a buscar información de como poder saberla.

Github: https://github.com/Maalfer/bruteapi

![image](https://github.com/user-attachments/assets/726bbd3d-949b-480d-ad76-1b292ebbdf22)

Nos lo descargamos, lo ejecutamos y encontramos lo que buscábamos.

![image](https://github.com/user-attachments/assets/9336a43b-4373-4040-9f1d-51da848d40a9)

![image](https://github.com/user-attachments/assets/eadd70da-9ff1-482e-b1e5-520e87873435)

Ahora vamos a usar la credencial que hemos encontrado con "Bearer Token", y vemos esto: 

![image](https://github.com/user-attachments/assets/a9c70432-ae27-44a6-bc04-4fb359c274d6)

Hacemos hydra y encontramos unas credenciales válidas "bob:password1".

![image](https://github.com/user-attachments/assets/50408c27-56cc-4354-8f51-2a0eeec503f8)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/36542d37-3aab-4615-970b-d4b8b2407bce)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/f7f3c84c-0adc-4bf9-ae92-79b5a5774fe7)

Escalamos privilegios correctamente y nos convertimos en el usuario balulero.

![image](https://github.com/user-attachments/assets/5c9c35d2-d5fa-4d82-8dcb-3dcf095add75)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/8914448c-2a7b-4347-8eae-5a2b1aa4d4f4)

Nos vamos a nuestra máquina y copiamos el archivo /etc/passwd de la máquina víctima en un archivo nuevo y le quitamos la "x" al root.

![image](https://github.com/user-attachments/assets/c95d6d39-f18d-48e6-8a36-226043877d4b)

Seguidamente iniciamos un servidor de python.

![image](https://github.com/user-attachments/assets/90d66851-bfd3-456e-aa9a-2e1f8e0290d2)

Y ahora ejecutamos el permiso SUDO, con el que vamos a cambiar el /etc/passwd de la máquina víctima por el que hemos creado nosotros.

![image](https://github.com/user-attachments/assets/bf70a69c-a89f-422c-8003-d36d22e288d4)

Y si ejecutamos su, veremos que ya somos root.

![image](https://github.com/user-attachments/assets/aedbc90b-e861-4655-b6d6-5dff208007e6)


