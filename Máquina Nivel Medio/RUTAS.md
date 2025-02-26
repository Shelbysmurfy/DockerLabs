# RESOLUCIÓN DE LA MÁQUINA RUTAS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/1683ce33-d39f-436b-9483-592d00715c99)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/ed2ef917-7620-40ed-92ad-5cd563030e5d)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/78b30c7f-3fe8-4034-9ae8-722e6b5c8812)

Abrimos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/ed1538ce-a98c-4fc2-875f-68c89dd46429)

Nos conectamos al servico ftp con el usuario anonymous.

![image](https://github.com/user-attachments/assets/965e2b04-a96a-479f-83c9-d07b97973fa7)

Vemos un archivo.zip, nos lo traemos a nuestra máquina con get.

![image](https://github.com/user-attachments/assets/3cdb87fd-8a83-4ed7-b596-b036237bf2a9)

Con zip2john vamos a obtener el hash, y con john lo vamos a romper gracias a el diccionario rockyou.

![image](https://github.com/user-attachments/assets/46a6e962-2e49-4d78-9ea8-02e817ef0bff)

Hacemos unzip de el archivo.zip con la contraseña obtenida, y conseguimos un archivo.txt.

![image](https://github.com/user-attachments/assets/ae65ada0-bae5-4f63-9847-f83b57f28f01)

![image](https://github.com/user-attachments/assets/7ed0e363-d31f-4abd-b45c-bc0dc26c71bb)

Nos vamos al link que nos dicen como pista "firstatack.github.io", encontramos una imagen y le damos a abrir el link para saber donde estan las imagenes guardadas.

![image](https://github.com/user-attachments/assets/7a72c413-b46d-43ba-98e7-cc0f2fd3e632)

![image](https://github.com/user-attachments/assets/50ca419b-a478-46ac-a01b-3c4e1363ea5e)

Aprovechamos el /assets/, y añadimos la imagen que buscamos, y la encontramos.

![image](https://github.com/user-attachments/assets/451b1a9b-f88a-43bd-9f51-29a70b588fe8)

Usamos la herreamienta setghide para extraer posibles archivos de esta imagen y encontramos unas posibles credenciales.

![image](https://github.com/user-attachments/assets/43490357-e2ba-4f8e-ba71-17c5f94995ee)

Las usamos para conectarnos al servicio ssh pero no funcionan.

Hacemos fuerza bruta con gobuster y encontramos un index.php

![image](https://github.com/user-attachments/assets/9d55ab3a-fab8-421e-a8b4-4635bcc9583e)

Entramos y vemos esta página.

![image](https://github.com/user-attachments/assets/2fc4b7f7-cbb2-46cc-83f1-0ca4c64be637)

Cuando nos ponemos encima de el "Enlace 2", vemos un posible dominio, vamos a añadirlo al /etc/hosts

![image](https://github.com/user-attachments/assets/3caa7783-6f52-4459-b15c-c3bb3437e071)

Lo abrimos y vemos un login.

![image](https://github.com/user-attachments/assets/c90df390-a21d-44f5-9b8e-f6e1dc0e33fc)

Añadimos las credenciales que habíamos conseguido antes "hackeada:denuevo" y ganamos acceso.

![image](https://github.com/user-attachments/assets/3481e164-326e-4253-ad1a-09c9814e2b27)

Volvemos a hacer gobuster, pero esta vez me devuelve un error.

![image](https://github.com/user-attachments/assets/b818a13a-1d7f-4ccd-b26d-bdb0e6f65d90)

Vamos a abrirnos burpsuite para ver que pasa.

![image](https://github.com/user-attachments/assets/1e733314-f387-41fd-8482-1f58bc4bc88b)

Vemos que contiene un apartado de "Authorization", que al parecer contiene un código cifrado en base64, lo desciframos y vemos que són las credenciales que hemos usado en el login.

![image](https://github.com/user-attachments/assets/1b204f82-0ab5-4f58-b9ab-1b02079b88bb)

Así que vamos a volver a hacer gobuster, pero esta vez añadiendo esto y volvemos a ver lo mismo que antes.

![image](https://github.com/user-attachments/assets/e2e71a6a-9d79-4299-a799-1ac9dd1564cc)

Abrimos de nuevo el index.php y vuelve a ser lo mismo.

![image](https://github.com/user-attachments/assets/7b125a35-fd17-4e48-942a-08968e264511)

Vamos a intentar a hacer fuerza bruta con wfuzz para buscar un posible parámetro con el que inyectar comandos, para ello tendremos que volver a añadir el "Authorization".

![image](https://github.com/user-attachments/assets/2958ff04-5275-4535-836d-12a5d55f7d3f)

Lo ponemos en la web y nos muestra esto: 

![image](https://github.com/user-attachments/assets/7e147c33-317b-4dc5-b823-83db60a96ddf)

Vamos a intentar hacer un RFI, a ver si de esta manera podemos ganar acceso, ya que LFI, no nos deja.

Vamos a abrirnos un servidor python desde nuestra máquina.

![image](https://github.com/user-attachments/assets/e42b11f9-d700-4491-92ef-904255ec6375)

Nos conctamos desde la web, y añadimos el archivo malicioso, con el que queremos poder ejecutar comandos.

![image](https://github.com/user-attachments/assets/f587c383-e25c-49a3-a54a-973db8b66f3b)

La conexión ha sido exitosa.

![image](https://github.com/user-attachments/assets/9c6f85f0-0784-4481-8701-7ad6b4fca5e6)

Y si añadimos un "&", y seguidamente hacemos un cmd=id, que es lo que nos permite hacer nuestro archivo malicioso que hemos creado, nos funciona correctamente.

![image](https://github.com/user-attachments/assets/c4c481a1-d96c-442c-b751-6fbfc604983b)

Como sabemos que podemos ejecutar comandos, vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/87d6b195-d175-4aa7-b4c2-c2c4f46e55c4)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/2fd02f70-e521-434c-9e44-e0730570d576)

Lo ejecutamos y nos muestra esto: 

![image](https://github.com/user-attachments/assets/4b476126-21af-4c63-a307-2d48f6e9f772)

El binario llama al comando head y lo hace usando tanto una ruta relativa como la ruta absoluta y el uso de una ruta relativa nos da paso a que podemos emplear un path hijacking

Para ello iremos al directorio /tmp y crearemos un archivo head.

![image](https://github.com/user-attachments/assets/5baded4e-1fd0-4629-9f5f-bf49e1e31a81)

Le damos permisos. lo ejecutamos y ya somos el usuario norberto.

![image](https://github.com/user-attachments/assets/1c6e3b1b-5418-4a7d-b954-6335a01cd1f4)

Nos vamos al directorio /home/norberto y nos encontramos un archivo con una pista.

![image](https://github.com/user-attachments/assets/b478e01d-b617-41f4-bfd0-621f0c2d24a5)

Lo desencriptamos y nos muestra una posible contraseña.

![image](https://github.com/user-attachments/assets/32606136-48ae-4297-8c92-b77fee34e3e4)

Intentamos conectarnos con maria por el servicio ssh pero no funciona, pero al probar con el usuario norberto si nos deja.

![image](https://github.com/user-attachments/assets/faa9e7cf-d88e-4800-a3e5-af1744602e2a)

Una vez dentro hacemos whoami para asegurarnos que somos norberto, pero nos dice que somos maria, es decir que nos hemos conectado al servicio ssh como norberto, pero una vez dentro somos maria.

![image](https://github.com/user-attachments/assets/8bc19153-9ab8-4865-9f33-67c29aedc87f)

Hacemos ls -la y vemos una posible contraseña.

![image](https://github.com/user-attachments/assets/11833b7a-d83c-4726-be6a-d539327846b1)

Intentamos conectarnos de nuevo por el servicio ssh, pero esta vez con las credenciales "maria:asientiendesmejor", y conseguimos acceso.

![image](https://github.com/user-attachments/assets/c1357bfa-0447-41c4-b6b6-d250902bb411)

No encontramos nada, por tanto vamos a usar linpeas para ver si encontramos información valiosa.

![image](https://github.com/user-attachments/assets/36a1156a-677a-48ef-8862-0c4fa82c146b)

El archivo 00-header, como vemos esta ejecutando unos mensajes que se muetsran cuando hacemos el login de algun usuario.

![image](https://github.com/user-attachments/assets/e0d2abc7-187f-4c66-bc8b-2fe9f2be2d4d)

Vamos a ver quien tiene permisos sobre este archivo.

![image](https://github.com/user-attachments/assets/17182922-d469-49cc-875f-e8705e6e3299)

Sabiendo esto vamos a meternos en el archivo y vamos a añadir el comando "chmod u+s /bin/bash", para poder escalar privilegios a root cuando vuelva a loguearme.

![image](https://github.com/user-attachments/assets/0481388c-bebe-43a5-8495-3d1996b6693f)

Nos volvemos a conectar como maria y vemos que nos conectamos correctamente, y vuelve a aparecer el "SORPRESA Y FELIZZ HACK", que es lo que esta haciendo el 00-header.

![image](https://github.com/user-attachments/assets/f26957b8-5612-49d4-b9bd-c4084e11fd98)

Por tanto si ejecutamos bash -p deberíamos escalar privilegios y ser usuario root.

![image](https://github.com/user-attachments/assets/574fc990-dd7e-4501-8377-7bb72f6c2125)
