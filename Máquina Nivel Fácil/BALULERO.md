# RESOLUCIÓN DE LA MÁQUINA BALULERO

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/5c1a683c-07f1-472f-99f2-e35a52d14633)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/52219793-205a-4fc2-b623-71f9d836cbbf)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3417498c-fbc6-4201-9a1b-e26768b27e29)

Abrimos la web.

![image](https://github.com/user-attachments/assets/fa5b3821-1d72-4412-bae0-49f83d7eb40a)

En el código fuente encontramos un script.

![image](https://github.com/user-attachments/assets/75081d66-e7ff-4372-91b3-d836c1bdde8a)

Revisando la información de este script vemos esto:

![image](https://github.com/user-attachments/assets/c41ece51-795a-40d5-a028-0c76dadfc013)

Así que vamos a intentar descargar el archivo.

En el encontramos unas credenciales.

![image](https://github.com/user-attachments/assets/57025982-2693-408b-adc3-fed4a9a2f71b)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/e20dea20-c545-4050-a3ec-5499cd66a58e)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/aeca5923-557e-4b69-8aa0-56bfd533e203)

Nos convertimos a usuario chocolate.

![image](https://github.com/user-attachments/assets/202f41bb-8dcb-4e77-a6bf-f9defaf7cc12)

En el directorio /opt nos encontramos el archivo script.php

![image](https://github.com/user-attachments/assets/2ec8bb06-e996-462a-9262-7d90fab5bc67)

Si hacemos ls -l /opt/script.php vemos que chocolate es el propietario del archivo y tiene permisos de escritura.

![image](https://github.com/user-attachments/assets/8d659667-6cfb-4642-8b82-0c43b2272efe)

Así que cambiamos el contenido del archivo para que cada vez que se ejecute se intente darle privilegios SUID a la bash.

![image](https://github.com/user-attachments/assets/0ed46cff-5ab1-4d43-b64f-04cc8259e9e5)

Y ya somos root.

![image](https://github.com/user-attachments/assets/8c466928-a765-4841-aeff-968a94a7abf4)


