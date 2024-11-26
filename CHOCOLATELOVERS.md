# RESOLUCIÓN DE LA MÁQUINA CHOCOLATELOVERS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/135a3a1a-bba9-48fc-ab07-2fe9320d4b2f)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/3536848a-390e-4aee-b3b7-a89793aaa253)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/260213c9-f427-4d6c-88ad-3a2993dd0772)

Entramos en el código fuente de la web y encontramos un directorio como comentario.

![image](https://github.com/user-attachments/assets/286ea98e-c4a3-48bb-84b2-b16f03e1a477)

Entramos en el y vemos otro directorio, admin.php

![image](https://github.com/user-attachments/assets/affcef9a-1808-4b48-a9fb-c28e416f04df)

Entramos en admin.php

![image](https://github.com/user-attachments/assets/30b2c507-8cc3-4c8c-8cc7-4247ba01f39a)

Probamos unas credenciales por defecto, usuario: admin y contraseña: admin

![image](https://github.com/user-attachments/assets/e89a1a61-a3b3-4514-87c4-c40d10d5777c)

Y conseguimos acceso.

![image](https://github.com/user-attachments/assets/e9f662c8-45fe-4e75-ade4-c35b778c22a9)

Nos vamos a los ajustes de la web y vemos la versión exacta del Nibbleblog.

![image](https://github.com/user-attachments/assets/f1f6e0ed-d8a2-4781-899a-c56695cb0146)

Hacemos un searchsploit.

![image](https://github.com/user-attachments/assets/942fde70-20ff-4548-950c-259aab835e6c)

Abrimos el metasploit con msfconsole y buscamos por Nibbleblog.

![image](https://github.com/user-attachments/assets/190707b5-c220-4b97-90b5-dec87f8d2bd9)

Lo seleccionamos con el comando use 0.

![image](https://github.com/user-attachments/assets/82320241-e571-4af1-86d7-19be6e43d083)

Ahora haremos un "set RHOSTS" para seleccionar la máquina víctima y un "set LHOST" para la nuestra.

![image](https://github.com/user-attachments/assets/2fd727cf-96c7-49fb-aeef-1a9681c30ef0)

También haremos un "set USERNAME", un "SET password" y un "set TARGETURI" para indicar el dominio.

![image](https://github.com/user-attachments/assets/0d5496c1-d366-495a-9957-4c71c11d43d9)

Revisando el código del script que estamos explotando, está abusando de un plugin llamado My Image. Vemos en la sección de plugins del panel que no está instalado. Lo instalamos.

![image](https://github.com/user-attachments/assets/ca805f00-5fb7-4e6d-8980-40dfc7902c94)

Y con esto obtenemos una sesión de meterpreter finalmente.

![image](https://github.com/user-attachments/assets/bb23fb6e-767b-433c-9510-6b4f36d79de7)

Nos ponemos en escucha y nos enviamos una reverse shell para trabajar de forma más cómoda.

![image](https://github.com/user-attachments/assets/4465e101-de5a-4565-97af-f0d428fc1897)

![image](https://github.com/user-attachments/assets/58dd8a86-466b-40c0-8d56-70f2ab69a9e3)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/0b8835b1-d657-4b21-a4c2-a51ed7992c95)

Vamos al GTFObins y seguimos los pasos que nos dice.

![image](https://github.com/user-attachments/assets/ca2510ce-7264-4ad3-8dd0-b949d5d97a1e)

Si listamos los procesos que están corriendo en el sistema. Podemos ver que root está ejecutando un script sospechoso.

![image](https://github.com/user-attachments/assets/38c321d5-4d2e-422c-a67a-f83ee462d285)

Listamos los permisos de este archivo y vemos que pertenece al usuario chocolate.

![image](https://github.com/user-attachments/assets/bda57c8b-de77-4565-9e08-a434ebbaab51)

Esto nos permite poder cambiarlo como queramos para poder ejecutar algo como usuario root.

![image](https://github.com/user-attachments/assets/29cd71d7-d988-4ade-8cbc-2c8aff7e6dd3)

Hacemos bash -p y ya somos root.

![image](https://github.com/user-attachments/assets/00a515fa-3784-4f63-aa94-4a10f6dbda5d)








