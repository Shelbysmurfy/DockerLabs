# RESOLUCIÓN DE LA MÁQUINA SITES

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/feb499c4-4c83-4955-bc13-401afbcf00b0)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/7e7e49fa-c28f-4a95-aaf9-fd5e035fecba)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/c42febe8-5a17-4c3e-a8fc-b06888d6859a)

Abrimos la web.

![image](https://github.com/user-attachments/assets/5d43e654-3776-49b3-84c9-3c3658e194de)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/7432d4d8-0b3b-4dbd-8d20-8c9fd49592f1)

Abrimos el vulnerable.php 

![image](https://github.com/user-attachments/assets/109ea372-df63-4dfa-b73a-0f1eb05c0cd1)

Y ahora hacemos uso de la herramienta wfuzz en busca de parámetros para poder hacer LFI.

![image](https://github.com/user-attachments/assets/36831c08-61ac-48e5-8d71-928d50af2d82)

Miramos el /etc/passwd, y vemos el usuario chocolate.

![image](https://github.com/user-attachments/assets/8bc5279e-e550-41e4-bc43-8ef3924f146e)

Recordamos que en la web habíamos visto esto: 

![image](https://github.com/user-attachments/assets/0cf826e5-880c-4d98-8960-ab69beb3262b)

Vamos a la ruta indicada, añadiendo delante de esta /etc/apache2.

![image](https://github.com/user-attachments/assets/45e01a98-8a3e-42de-97bb-c15858fda8e8)

Miramos dentro de /archivitotraviesito, para ver que información tiene escondida, y encontramos una password para el servicio ssh.

![image](https://github.com/user-attachments/assets/fc2d1b49-dfbb-42d0-9e88-d2cf5f9670fe)

Hacemos fuerza bruta con hydra para buscar el usuario de la contraseña que hemos encontrado.

![image](https://github.com/user-attachments/assets/9cadc5ce-f404-4462-a850-c8686451302a)

Entramos al servicio ssh con las credenciales obtenidas "chocolate:lapasswordmasmolonadelacity"

![image](https://github.com/user-attachments/assets/53a2f59f-0a67-4b91-97d2-644193fcaa31)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/c5dbe629-a7e0-4106-be69-751f1c40f3f5)

Y ya somos root.

![image](https://github.com/user-attachments/assets/c7fee0dc-8aa4-4337-830f-5fd4c5ff156f)
