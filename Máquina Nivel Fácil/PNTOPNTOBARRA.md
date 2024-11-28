# RESOLUCIÓN DE LA MÁQUINA PNTOPNTOBARRA

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/34ede5bb-fcbb-49ef-8280-9863d530bf8c)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/b3fcb952-e7b4-4446-a5b3-96f9d98bcdda)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/081b176b-f60e-4bf4-bdc0-54feb160e8da)

Hacemos fuerza bruta con gobuster y encontramos el directorio index.php (funciona solo si ponemos dos barras)

![image](https://github.com/user-attachments/assets/f6b32ad4-df1e-44bf-830a-16e8c9b24776)

Dentro de el si vamos a ejemplos de computadoras infectadas vemos esto :

![image](https://github.com/user-attachments/assets/1a2f0583-f7bc-4f2f-a9ff-aa2804806148)

Y al ver esta url, intentado inyectar código (LFI), conseguimos ver el /etc/passwd

![image](https://github.com/user-attachments/assets/5a7f6462-d86b-4e97-ae8d-91542853b58e)

Intentamos cargar el archivo de clave privada con LFI.

![image](https://github.com/user-attachments/assets/759abc63-26a3-47b0-8c33-e1c9250b9404)

Nos creamos un archivo id_rsa con este contenido dentro, le damos permisos y ejecutamos el servicio ssh.

![image](https://github.com/user-attachments/assets/8d0e98e0-c86c-42d0-8c41-3e91478d4e69)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/6a32ea01-96a3-4419-ad44-1a14d62bcc7d)

Y ya somos root.

![image](https://github.com/user-attachments/assets/029d2e11-0b12-4909-8d73-2f1bc20af856)




