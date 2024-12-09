# RESOLUCIÓN DE LA MÁQUINA PSYCHO

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/0421420c-3500-42eb-bd01-75d15a2a36c6)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/74ec559f-c91f-4a11-9902-f93b8206f293)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/44101dba-9e9b-445c-a74a-92b82cc3f92e)

Abrimos la web.

![image](https://github.com/user-attachments/assets/991b7824-8bd3-4577-8bbb-df441653fba6)

Vemos que hay un mensaje de error al inspeccionar el código fuente de esta.

![image](https://github.com/user-attachments/assets/f25c71b2-7a13-4b08-8747-f96a8b2e687d)

Hacemos fuerza bruta con dirsearch.

![image](https://github.com/user-attachments/assets/5c93255f-de8b-4229-9d8e-ff0cf9c0a160)

Entramos en el directorio encontrado, y vemos que hay una imagen pero que no contiene contenido.

![image](https://github.com/user-attachments/assets/094d25ab-a023-4e40-8d98-66d59cf9194c)

En la web encontramos un "error", como también tenemos un index.php, probamos a fuzzear en la busca de un posible parámetro.

![image](https://github.com/user-attachments/assets/b72750c1-5c30-4095-b48b-905ad41937e0)

Lo usamos en la url y nos devuelve lo que buscábamos.

![image](https://github.com/user-attachments/assets/9b9eefb8-ba65-435c-80f2-0873780e0616)

En el /etc/passwd, encontramos dos posibles usuarios: luisillo y vaxei.

Encontramos la clave id_rsa del usuario vaxei.

![image](https://github.com/user-attachments/assets/5903d4c7-366a-48ec-9f87-47f77d9c4bbf)

Nos creamos un archivo id_rsa con este contenido dentro, le damos permisos y ejecutamos el servicio ssh.

![image](https://github.com/user-attachments/assets/aa598f25-4427-4e2f-b4dd-94540d7b1997)

Hacemos sudo -l y vemos esto:

![image](https://github.com/user-attachments/assets/8a080cb2-cb48-4136-83cc-15b32a79bcc7)

Nos convertimos en luisillo.

![image](https://github.com/user-attachments/assets/ac06d3ed-f488-4417-a42f-854d9dbf6dd0)

Volvemos a hacer sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b34b26e7-8cb1-4bbc-817f-cdc3f3da914a)

Vamos al directorio /opt, borramos el archivo paw.py y lo volvemos a crear con un nuevo contenido dentro que nos permitirá escalar privilegios.

![image](https://github.com/user-attachments/assets/9e78bb9b-5fc2-4e5d-9b40-9847595f803c)

Y ya somos root.

![image](https://github.com/user-attachments/assets/b39a311c-2afe-4ae6-8d8c-42c5384e0805)




