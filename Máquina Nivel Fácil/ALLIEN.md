# RESOLUCIÓN DE LA MÁQUINA ALLIEN

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/e2381f88-86eb-470c-a4b8-399480bf1d4d)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/d1d8f1c9-a101-415b-a006-3566605058f6)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/9a4818d1-48d9-484a-88a9-071e9846d093)

Abrimos la web y vemos un login.

![image](https://github.com/user-attachments/assets/5eca84f0-81a7-442e-8ca5-ac3c0faf55f8)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/92b1f499-b304-46af-aeff-d32952735a18)

Entramos en el directorio /productos.php y encontramos esto:

![image](https://github.com/user-attachments/assets/3876fe91-7a36-4e98-9213-1ad1986af3ab)

Ahora sabiendo que estamos tratando con sistemas SMB, usaremos enum4linux para recopilar información sobre estos.

![image](https://github.com/user-attachments/assets/0af15665-a43e-4997-a310-47cf69aaa904)

Nos encontramos tanto directorios como usuarios.

![image](https://github.com/user-attachments/assets/f8c7476a-afb0-497a-a882-30a08f4cf859)

![image](https://github.com/user-attachments/assets/f9c1c62c-ab71-4401-a071-6e8ee3ea35d6)

Ahora con la herramienta crackmapexec, usando una lista de los usuarios que hemos encontrado, y el rockyu intentaremos conseguir credenciales válidas.

![image](https://github.com/user-attachments/assets/8b19db03-13a8-4951-890e-b46b09ce1e3a)

Ahora con el uso del comando smbclient, junto a las credenciales sacadas puedo ir probando todos los directorios para ver si puedo sacar información valiosa.

Dentro de /backup24/Documents/Personal/credentials.txt encontramos unas credenciales.

![image](https://github.com/user-attachments/assets/71cff743-697b-43c8-9851-3f94de4da436)

El usuario administrador, lo habíamos visto antes también al hacer uso de la herramienta enum4linux.

Así que vamos a intentar usar sus credenciales usando smbmap.

![image](https://github.com/user-attachments/assets/c7b32710-44c6-4bf0-a47f-7618e7aee8f8)

Vemos que en la carpeta home tenemos permisos de escritura, así que vamos a antrar con smbclient para ver que hay dentro.

![image](https://github.com/user-attachments/assets/71fec175-ab3d-4eaf-82c0-879f6092a403)

Podemos ver que es la ruta donde se encuentran todos los archivos de la página web, por tanto como tenemos permisos de escritura vamos a importar un archivo malicioso.

Primero lo creamos en nuestra máquina local.

![image](https://github.com/user-attachments/assets/67c8da08-b750-4518-b7cc-8477791f593e)

Y lo subimos.

![image](https://github.com/user-attachments/assets/c1a77ef5-12de-451a-a0c0-b1705c489143)

Lo abrimos y vemos que podemos ejecutar comandos correctamente.

![image](https://github.com/user-attachments/assets/4a2928ea-e865-4f5b-bbc8-e4d0ff62c1bf)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/bfb66486-a5a0-4d17-9726-d1cce4def0ad)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/225ac579-6ef6-4d3d-8ec8-c141812b91cd)

Y ya somos root.

![image](https://github.com/user-attachments/assets/90a3ceaa-a65a-4784-b309-2eb0a1ff64ef)











