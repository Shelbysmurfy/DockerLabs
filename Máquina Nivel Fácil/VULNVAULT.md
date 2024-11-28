# RESOLUCIÓN DE LA MÁQUINA VULNVAULT

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/38bf0cee-c06c-497c-aa99-be38af25201f)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/888da2d1-afaa-4c79-9048-3965d6b3eea9)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/b31b4561-9434-472f-aa4e-b19b3dd70375)

Hacemos fuerza bruta con dirsearch y encontramos el directorio upload.php, que se supone que recibe los archivos que se suben en la página.

![image](https://github.com/user-attachments/assets/a51b63a4-ca8d-4f35-b2b0-9675c063c0e4)

En la página se pueden subir archivos, pero no podemos verlos en el upload.php

![image](https://github.com/user-attachments/assets/697acc5a-414a-4116-ac74-867691ef60cc)

En el apartado de genera tu reporte,ponemos ";cat /etc/passwd"

![image](https://github.com/user-attachments/assets/e13a573d-26c2-4362-a11b-6bc752b406b2)

Y nos devuelve lo que le pedíamos.

![image](https://github.com/user-attachments/assets/6fad1700-ac75-431a-80b5-034e917a3d61)

Hacemos hydra y no nos funciana, así que vamos a cargar el archivo de clave privado con LFI.

Tendremos que poner ";cat /home/samara/.ssh/id_rsa", para que nos lo muestre.

![image](https://github.com/user-attachments/assets/4319260b-59b0-40c1-b5e3-ade02204521a)

Nos creamos un archivo id_rsa con este contenido dentro, le damos permisos y ejecutamos el servicio ssh.

![image](https://github.com/user-attachments/assets/09f03d7d-c450-4e25-9a9d-2f051d32bb5c)

Hacemos ps -aux para buscar procesos del sistema.

![image](https://github.com/user-attachments/assets/a5c019b4-4564-4547-958f-40a0a1b5d8f2)

Nos vamos a la ruta del archivo que hemos visto que estaba en /usr/local/bin, en el encontramos un contenidp que ya habíamos visto antes dentro del usuario samara pero que no nos daba información.

![image](https://github.com/user-attachments/assets/8d2b5312-5700-4f1e-afa6-a389e1096153)

Vemos los permisos de ese archivo para ver que podemos hacer.

![image](https://github.com/user-attachments/assets/d501af02-b3c5-416e-9bef-a143ed060843)

Al ver los permisos, nos metemos en el archivo y lo editamos para poder acceder como root.

![image](https://github.com/user-attachments/assets/64a7fe2c-6e81-4cc4-bf5a-b13cb5ec51c7)

Con esto onseguimos que el binariode bash tenga el bit SUID establecido, lo que nos permitirá ejecutar comandos con privilegios de root.

Y ahorta si ejecutamos el comando bash -p iniciaremos una instancio como usuario root.

![image](https://github.com/user-attachments/assets/287029fd-a0cf-418e-8c35-50cf627f53e9)




