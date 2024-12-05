# RESOLUCIÓN DE LA MÁQUINA WINTERFELL

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/64e18938-d736-443d-aa92-91460d225656)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6e88892d-1f48-4890-ba7e-a2b88cba7507)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/d334b801-daf9-4d0f-9d9f-4349a9780345)

Abrimos la web (puerto 80) y no vemos nada importante.

![image](https://github.com/user-attachments/assets/0e8217d3-5fa7-49f6-8c2d-491e937495f0)

Hacemos fuerza bruta con gobuster y nos encontramos el directorio dragon.

![image](https://github.com/user-attachments/assets/95f88515-a19b-44cb-9361-16c7d8f450ce)

Ahora sabiendo que estamos tratando con sistemas SMB, usaremos enum4linux para recopilar información sobre estos.

![image](https://github.com/user-attachments/assets/69c65363-7a22-4b54-bb6b-5e170bd8eb51)

Nos encontramos tanto directorios como usuarios.

![image](https://github.com/user-attachments/assets/76b83313-d343-48cc-bb51-3e2dc80a811c)

![image](https://github.com/user-attachments/assets/6adbcc60-730f-45d7-b821-bc9d36c4f878)

Hacemos uso de la herramienta crackmapexec para ver si podemos sacar credenciales válidas (jon / seacercaelinvierno)

![image](https://github.com/user-attachments/assets/1de25962-6666-4b50-8f48-d78276f52b6e)

Ahora con el uso del comando smbclient, junto a las credenciales sacadas puedo ir probando todos los directorios para ver si puedo sacar información valiosa.

![image](https://github.com/user-attachments/assets/e66aadae-9013-4afc-9f5a-104f207f61d8)

Abrimos el archivo y encontramos información valiosa.

![image](https://github.com/user-attachments/assets/24d5cc7f-617e-47e4-9a13-b7d2643ba6ee)

Decodeamos la contraseña que nos dan.

![image](https://github.com/user-attachments/assets/c1230ad6-20b0-4f95-b58d-647b1076b9e6)

El mensaje quien lo está diciendo es el jon, por tanto intentamos entrar al servicio ssh como usuario: jon i contraseña: hijodelanister

![image](https://github.com/user-attachments/assets/916d013d-f3ae-4dd0-b3d1-2dcd4205e9d8)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/dc1f028a-e1ae-4317-bbce-078a8ea0d146)

Nos vamos al archivo .mensaje.py, lo borramos y creamos otro archivo igual, con el siguiente contenido:

![image](https://github.com/user-attachments/assets/7d0f5cb5-3e48-4e86-8210-ecbb395cc330)

Nos convertimos en aria.

![image](https://github.com/user-attachments/assets/9f377282-9bed-4bd0-8363-37a4240ddf54)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/b7bfa84a-0ce3-4282-ab3a-4091d798a8da)

Vamos intercambiando los dos permisos que tenemos para poder encontrar información relevante.

Encontramos la contraseña del usuario daenerys.

![image](https://github.com/user-attachments/assets/8e370884-ddd9-4734-83a2-6343b65d73cb)

Nos conectamos como usuario daenerys con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/32c8e02a-a78a-4c6c-ba97-64887656b7a7)

Volvemos a hacer sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/14d6fdb8-4ecf-4127-8a12-7152ba26f3d7)

Nos vamos hasta elñ archivo .shell.sh, que está oculto y le cambiamos el contenido.

![image](https://github.com/user-attachments/assets/3e53d27a-1945-4459-88a5-a2f6eac66429)

Y ya ganamos acceso como root.

![image](https://github.com/user-attachments/assets/ea30e91c-46a7-44c9-9a30-b8c210a335e5)



