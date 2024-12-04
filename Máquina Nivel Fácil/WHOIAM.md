# RESOLUCIÓN DE LA MÁQUINA WHOIAM

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/fb652a86-1b78-4e84-91bb-be5084eeeaca)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/d1514465-feb3-4631-9cfe-1c3db2347a95)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/ee2f4cc9-6629-42d3-980f-f31af175916a)

Abrimos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/b8f56e79-b095-446a-8fe5-5e71c49265a0)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/894b2fa6-c44c-4c95-96a5-ddfca411dfc2)

En el directorio /backups encontramos un archivo .zip

![image](https://github.com/user-attachments/assets/820d8746-baff-4512-9597-be12bd2c2438)

Lo descargamos, lo abrimos y encontramos unas credenciales.

![image](https://github.com/user-attachments/assets/98777fd9-3219-4309-8f6d-3310cdc041ae)

Nos conectamos al login de wordpress con las cerdenciales obtenidas.

![image](https://github.com/user-attachments/assets/f7d0bfb7-30f3-4ea5-9a96-a52f12f34afc)

Con wpscan buscamos información sobre los pluggins que hay instalados.

![image](https://github.com/user-attachments/assets/1f95ac7f-4210-46eb-b936-66752ad8e2a1)

Y encontramos que el calendar esta bastante desactualizado.

![image](https://github.com/user-attachments/assets/3e797f68-9415-4368-82ec-bf84a9c115ac)

Hacemos uso de serachsploit para buscar posibles exploits para esta versión.

![image](https://github.com/user-attachments/assets/f3f96fd1-03a4-4768-8a03-f8f66ff040f6)

Nos descargamos el de remote code execution (RCE).

![image](https://github.com/user-attachments/assets/83aa15a9-c165-4971-99d2-2df594e1d37a)

Buscamos el CVE que nos da la descarga y nos muestra que tenemos que ejecutar este comando: 

También se puede explotar el POC poniendo (poc.py ) y no el que hemos descargado (50082.py).

![image](https://github.com/user-attachments/assets/4630a4eb-c897-47f2-965f-3a05c47a166f)

Nos vamos a la ruta que nos devuelve y ya tenemos acceso a ejecución de comandos.

![image](https://github.com/user-attachments/assets/3b3f5aa7-d341-439c-8422-01fdd7a2c11c)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/fc7d2759-0df2-46c1-aef1-9c72a55680ef)

Una vez dentro hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/1c758512-b144-42f4-8342-47ff4eddddf2)

Ejecutamos lo que nos dice el GTFObins y nos convertimos en el usuario rafa.

![image](https://github.com/user-attachments/assets/c5e35791-5a1a-4a9c-a883-e0ef8e36de6c)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/2c3239f3-26ab-4b7a-b238-86af6a16ae22)

Nos convertimos en ruben.

![image](https://github.com/user-attachments/assets/2054678c-e62a-4ac2-90b4-d78b14825e8d)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/c596187a-9755-4c93-aedd-6e30239bfdcc)

Vamos a ver que hace el script.

![image](https://github.com/user-attachments/assets/35e0f147-596d-43da-8e95-e63687d277e4)

Este script solicita al usuario que introduzca un numero si es igual a 42 es correcto si no es incorrecto.

Podemos inyectar código usando esta secuencia: array[$(chmod u+s /bin/bash)]+42

Y ya somos root.

![image](https://github.com/user-attachments/assets/5586ac3c-6e94-4bbd-9a57-2a0b7b5df764)





