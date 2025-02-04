# RESOLUCIÓN DE LA MÁQUINA REPORT

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/23333077-880d-425a-8f09-b36885faf92b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/612621fe-c797-4289-9af5-9c08f21a4a25)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a41d977c-405e-42e9-bb14-50623f07b68d)

Abrimos la web.

![image](https://github.com/user-attachments/assets/5eeded46-0bdd-4d8d-a868-7d5e24ebc626)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/ba1ace8c-cd4b-4994-93c2-a71c02e20189)

Nos vamos al admin.php, y con unas credenciales básicas (admin/admin123), ganamos acceso.

![image](https://github.com/user-attachments/assets/d1a8759c-7e9d-486a-85c9-793c606cfddf)

Abrimos el burpsuite, y cambiamos el content-type.

![image](https://github.com/user-attachments/assets/a547ed3b-ff15-4c5c-bfb0-1cb6acfcdab8)

De esta manera conseguimos subir el archivo correctamente.

![image](https://github.com/user-attachments/assets/e9568c4d-ed00-4325-a7c9-7682946883df)

Nos vamos al /uploads y ya lo vemos.

![image](https://github.com/user-attachments/assets/260b995d-9090-4287-8e50-e39e01f1fee5)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/341d7bb9-a188-48a6-87d7-5e5d4881c038)

Como no vemos nada, vamos a hacer uso de la herramienta linpeas.

![image](https://github.com/user-attachments/assets/0e2299c8-ff14-46c5-994c-c4e27c795dc9)

Nos vamos a la ruta que hemos encontrado, donder hay el .git, y usamos git log en busca de el historial de commits de un repositorio git.

![image](https://github.com/user-attachments/assets/a6fff6e7-05c1-4444-b555-45678f987ee3)

Ejecutamos el comando que nos sale pero nos devuelve esto: 

![image](https://github.com/user-attachments/assets/e3aeeed7-93a6-4345-a46b-bd999167850c)

Lo arreglamos de esta manera: 

![image](https://github.com/user-attachments/assets/0485fb84-17cf-4d44-8c4d-d55ef20b7392)

Eejecutamos git log nuevamente y encontramos uno que es el adm, usuario que tenemos en la máquina víctima pero que no tenemos su contraseña.

![image](https://github.com/user-attachments/assets/6b180e4d-f9a8-4b8b-9d0c-0fb75b93de3e)

Hacemos un git show del commit que tiene este usuario y vemos unas credenciales.

![image](https://github.com/user-attachments/assets/44e897ca-761b-4910-8c94-ef8c5fb7d6d3)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/b65015d0-b020-43fd-a69b-0bcbc4dd77d9)

Una vex conectados hacemos uso del comando ls -la y vemos el archivo .bashrc

![image](https://github.com/user-attachments/assets/53e85cff-30ec-4de8-9047-6baced1424eb)

Lo abrimos y encontramos una posible contraseña.

![image](https://github.com/user-attachments/assets/2a230f6d-588a-45b2-94c6-2b26e4136e97)

Nos vamos a cyberchef y sacamos una credencial. 

![image](https://github.com/user-attachments/assets/758ee05d-d096-478e-8e32-20b2c7b8692f)

Nos intentamos conectar como root y ganamos acceso.

![image](https://github.com/user-attachments/assets/f3ea0b8b-a77e-4096-81c3-f534bbc090d2)





