# RESOLUCIÓN DE LA MÁQUINA R00TLESS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/2f006b85-1507-4dd1-8189-521e761e83be)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/397be9d5-2f65-42a5-8684-69bb22a26ef8)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a68ab65d-44c6-4621-8797-8422f865b93d)

Abrimos la web y vemos una subida de archivos.

![image](https://github.com/user-attachments/assets/b8ad220f-8759-468b-9eb1-622f3e0f7c02)

Probamos a subir diferentes extensiones, hasta que nos deja.

![image](https://github.com/user-attachments/assets/7e5c4290-73f2-4315-bde6-4f7187de3976)

Como no sabemos donde se ha subido este archivo, vamos a hacer un gobuster en busca de posibles directorios.

![image](https://github.com/user-attachments/assets/28fc6e56-0e1c-462b-aecf-416bd98d880b)

En el readme.txt encontramos esta información: 

![image](https://github.com/user-attachments/assets/2f119324-d3f2-4485-b847-42ec6638eca7)

Por tanto lo que vamos a hacer, es crearnos un par de claves.

![image](https://github.com/user-attachments/assets/b3ba7079-88ee-43f4-9167-4d52087db1f5)

Ahora nos vamos a crear un archivo llamado "authorized_keys", donde añadiremos nuestra clave pública.

![image](https://github.com/user-attachments/assets/6282b3ff-5f1a-432f-bfec-ee4a20ae63b3)

Ahora subimos el archivo en la web.

![image](https://github.com/user-attachments/assets/c9ba7281-b659-4023-bf3a-76a9b5a30f4b)

Miramos que usuarios tenemos con enum4linux.

![image](https://github.com/user-attachments/assets/e44f0388-e618-49cd-90de-da2a8049227b)

Y ahora probamos a entrar con la clave privada que hemos creado, y alguno de los usuarios que tenemos.

Con el usuario passsamba conseguimos ganar acceso a la máquina víctima.

![image](https://github.com/user-attachments/assets/679dbdbc-ecf0-426f-b216-ee4ef85acb36)

Hacemos ls y encontramos una nota.

![image](https://github.com/user-attachments/assets/da70f9cb-61a8-4f29-b304-72f76257ada8)

Miramos los usuarios y probamos con usar la posible credencial que nos han dado con cada uno de ellos.

Ganamos acceso con las crednciales "sambauser:sambaarribasiempre".

![image](https://github.com/user-attachments/assets/3774ee92-6f55-4744-9745-1abc8befedc3)

![image](https://github.com/user-attachments/assets/c82b93af-f958-474c-b172-1151c3ee0447)

Como no encontramos nada, probamos a meternos desde smbmap con las credenciales obtenidas y vemos esto: 

![image](https://github.com/user-attachments/assets/797c6f7d-bd96-4c71-9294-da50bce8a7e0)

Nos metemos con smbclient al recurso compartido "read_only_share", y vemos un archivo.zip que nos traemos a nuestra máquina.

![image](https://github.com/user-attachments/assets/664289bb-6cb5-44dc-b1cd-9a074d0b4080)

Hacemos un zip2john para extraer el hash y luego usamos john para sacar la contraseña del zip.

![image](https://github.com/user-attachments/assets/5eec3b27-e5a4-404a-8613-e7a909b62c28)

Y sacamos unas credenciales.

![image](https://github.com/user-attachments/assets/fc409678-b651-4500-8b1c-b9406d37670f)

La contraseña está en base64 la decodeamos.

![image](https://github.com/user-attachments/assets/f833ca44-1740-4ec3-a7a2-712746be5ba8)

Nos conectamos con las credenciales obtenidas "root-false:passwordbadsecureultra".

![image](https://github.com/user-attachments/assets/1ceb06b6-b878-4e5e-b739-cc1a8473f50d)

Hacemos ls y vemos un mensaje.

![image](https://github.com/user-attachments/assets/c90ef77e-b107-47b4-ad47-9412c9a25f55)

Buscamos por el sistema y encontramos una posible segunda web.

![image](https://github.com/user-attachments/assets/b91a9e5e-e870-47db-877c-1790e0782568)

Ejecutamos un curl de la IP de la segunda web y nos muestra esto en el body: 

![image](https://github.com/user-attachments/assets/2a73adc5-747e-4658-902b-42906744f856)

![image](https://github.com/user-attachments/assets/56760e74-6388-48bb-9eb6-679b98e04503)

Por tanto vamos a indicarle las credenciales que hemos visto antes "mario:pinguinodemarioelmejor".

![image](https://github.com/user-attachments/assets/011b3472-1dc9-4cf2-a3c2-9216d6ddd8b2)

Vemos otra ruta así que vamos a ejecutarla para ver que nos muestra "super_secure_page/admin.php".

![image](https://github.com/user-attachments/assets/33a9297c-e426-4682-a5ab-e6c7c942ce7a)

En esta encontramos un posible archivo.txt

![image](https://github.com/user-attachments/assets/4db9e402-8fce-4de3-9c05-0bb97daf5f90)

Vamos a acceder al fichero para ver que contiene.

![image](https://github.com/user-attachments/assets/a2c3fff4-def6-42d6-8aa8-e7d423cb30fb)

Vemos que todo el rato nos habla de el "Cristal_de_la_Aurora" y al final nos sale que esto lo ha escrito el usuario less, así que vamos a probar estas credenciales para escalar privilegios.

![image](https://github.com/user-attachments/assets/1c3cfa91-d148-46bb-8769-648152228edd)

Hacemos ls y encontramos la primera flag la del user.

![image](https://github.com/user-attachments/assets/66de8afa-1565-474c-92f2-ed8e678caf2c)

Miramos los permisos SUDO y vemos esto: 

![image](https://github.com/user-attachments/assets/bf63d448-844e-438d-aaa9-7c8ab107f602)

Ejecutamos el permiso chown para cambiar los permisos de el archivo /etc/passwd, y que en vez de que sean de root sean del usuario less.

![image](https://github.com/user-attachments/assets/cf7d5a6c-b5ba-47d9-9254-c9578ac2f4fd)

Abrimos el archivo y le quitamos la x del usuario root, para poder escalar privilegios correctamente.

![image](https://github.com/user-attachments/assets/0b9a6d82-b9b8-4801-acf0-d23bd3d46139)

Y ya somos root.

![image](https://github.com/user-attachments/assets/847a72ea-c8a3-43bb-92c6-9944a2f46c95)

Y si hacemos ls podemos encontrar la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/8f1434af-ed3d-464f-b2d2-d9d9983427d7)




