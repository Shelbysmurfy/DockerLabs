# RESOLUCIÓN DE LA MÁQUINA DOMAIN

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/fead9606-7f58-442b-abe0-5afaa025c710)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/8a866e8b-0cd2-4aae-8f74-9272fc0ea77b)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/63b37de6-b9e3-4400-9817-3de9de5366b6)

Abrimos la web (puerto 80) y no vemos nada importante.

![image](https://github.com/user-attachments/assets/6843584a-75da-4f9c-97cd-929d58ce581b)

Sabiendo que estamos tratando con sistemas SMB, usaremos enum4linux para recopilar información sobre estos.

![image](https://github.com/user-attachments/assets/19d45951-d2da-4351-9d08-2e86fa9d582e)

Nos encontramos tanto directorios como usuarios.

![image](https://github.com/user-attachments/assets/361c6f66-0f5a-4c5f-beba-03e11a7ac846)

![image](https://github.com/user-attachments/assets/724c9989-6354-4d12-90f6-466a9258d8bc)

Hacemos uso de la herramienta crackmapexec para ver si podemos sacar credenciales válidas (bob / star)

![image](https://github.com/user-attachments/assets/b495c403-8701-48be-bfc2-9ab66d7a1c5c)

Haciendo uso de la herramienta smbmap vemos que tenemos permisos de escritura en el directorio html.

![image](https://github.com/user-attachments/assets/3961098c-9209-4ce4-bdaa-d99b8044c90a)

Nos conectamos al directorio con smbclient y las credenciales obtenidas y subimos un archivo malicioso.

![image](https://github.com/user-attachments/assets/3e8d663c-8eed-49c7-ba2f-d63266712be5)

![image](https://github.com/user-attachments/assets/f7625b7c-ac90-480e-a460-10cd59510a39)

Nos vamos a la web y vemos que podemos inyectar código.

![image](https://github.com/user-attachments/assets/94c131c9-864c-403c-a4c5-b02278f19045)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/196886fc-4572-4a90-927d-c5f0372736a3)

Nos conectamos como bob.

![image](https://github.com/user-attachments/assets/e96fbfe0-819f-4a01-bd7e-f424d8f79d0f)

Vemos los permisos SUID, tenemos activo el nano.

![image](https://github.com/user-attachments/assets/6f725601-71f9-4788-8477-b893c56da9da)

Para escalar privilegios vamos a modificar el archivo passwd con el binario nano.

![image](https://github.com/user-attachments/assets/15dbaa1f-ec58-42f9-952e-51b9af42db3c)

Le quitamos la x, y una vez guardado podemos hacer su root, y ya somos root.

![image](https://github.com/user-attachments/assets/38a25035-46a0-4240-b3ef-1aa2fb7d1b51)

