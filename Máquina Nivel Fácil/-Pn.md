# RESOLUCIÓN DE LA MÁQUINA -Pn

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/f6bf7bde-c793-465c-9647-89d5900911d6)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/efd3e852-018c-4207-ae02-490cb83426ad)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/b035b7f7-7eaa-4750-9e46-aecdea9f88ff)

Abrimos la web, puerto 8080.

![image](https://github.com/user-attachments/assets/953da2ab-8a9d-4643-8163-fd7d83fd226a)

Entro al servicio ftp y me encuentro un archivo con este mensaje.

![image](https://github.com/user-attachments/assets/e3c94b0e-5746-434f-8a1b-7f5ab14cbf97)

Hacemos fuerza bruta con hydra.

![image](https://github.com/user-attachments/assets/4ccf4d6e-ee4c-4b42-be26-214ad0183c47)

Nos encontramos un login desplegable en el directorio /manager.

![image](https://github.com/user-attachments/assets/ce7d44fc-5065-42ba-8a8e-677453da6802)

Vamos a buscarlo en HackTricks y encontramos una serie de contraseñas default, esta funciona (tomcat:s3cr3t)

![image](https://github.com/user-attachments/assets/64dca66e-3685-4809-836e-e2cd37beb6f4)

![image](https://github.com/user-attachments/assets/4b9a9160-734d-40c7-9ff0-61a432dab63d)

Conseguimos acceso y vemos esto: 

![image](https://github.com/user-attachments/assets/f11ea096-bb35-481c-9f67-7a9f229d69b6)

Para explotar tomcat usaremos un archivo war que nos devolverá una reverse shell.

![image](https://github.com/user-attachments/assets/b0a65fd7-7d54-43cc-a277-02074954f51a)

Para ello antes tendremos que crearlo.

![image](https://github.com/user-attachments/assets/8ad557fe-f43a-4bad-8567-7b7e5f3dfdca)

Una vez creado lo subiremos a la subida de archivos war que hay en la web donde nos hemos logueado.

![image](https://github.com/user-attachments/assets/743584b1-cb21-43ed-90e1-ebbf8b06b583)

Como ya lo tenemos subido ahora solo tendremos que darle click mientras estamos escuchando con netcat.

![image](https://github.com/user-attachments/assets/57846214-a40e-4fb1-95c5-0ba721fea58a)

Y ya somos root.

![image](https://github.com/user-attachments/assets/d190b1c3-698d-4bf4-8263-1183b4d9dab2)





