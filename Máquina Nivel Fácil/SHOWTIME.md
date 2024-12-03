# RESOLUCIÓN DE LA MÁQUINA SHOWTIME

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/69d73383-a2c4-4f39-b8af-2548cb3335c6)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/a8f5cfce-6db5-462c-8a62-d88709cd9868)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/9b064748-c131-4d66-88a1-8222ff0e5447)

Abrimos la web.

![image](https://github.com/user-attachments/assets/6e04c831-3e41-462e-a1c6-58b67b4acbf6)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/ee57075b-c73d-4e2d-b8f7-14ae3c57a0bc)

Entramos al login.

![image](https://github.com/user-attachments/assets/60865822-348a-4af2-a5a5-5b59a53bc1e7)

Intentamos ver si es vulnerable a inyección sql con un comando básico.

![image](https://github.com/user-attachments/assets/1b8d51e7-f2de-4307-bf33-48e032366812)

Y nos muestra esto: 

![image](https://github.com/user-attachments/assets/9873d045-e05a-461d-9f08-52f2aeff64c5)

Procedemos a usar sqlmap para ver las bases de datos.

![image](https://github.com/user-attachments/assets/7b30b255-b8fb-4ddf-8512-1623c7c2e0a8)

![image](https://github.com/user-attachments/assets/31336b2d-8a1a-4539-b7ac-ed6f40e04995)

Ahora usamos sqlmap para ver las tablas dentro uses.

![image](https://github.com/user-attachments/assets/d7c0ddde-1c30-481d-9de0-825a5ed8a8c9)

![image](https://github.com/user-attachments/assets/1ee4dcfe-8f8c-42cb-b03f-9207e9b5f16b)

Ahora lo usamos para ver las columnas dentro de la tabla usuarios.

![image](https://github.com/user-attachments/assets/dbcd7154-a6e0-475a-8170-a454ae796dc6)

![image](https://github.com/user-attachments/assets/e0e88ba6-1cf4-4e54-b76d-43045a5d964e)

Finalmente lo usamos para ver el id, usuarios y contraseñas.

![image](https://github.com/user-attachments/assets/9a35d65a-115e-4b4b-838f-75f62d94823d)

Tenemos 3 posibles usuarios. 

![image](https://github.com/user-attachments/assets/173dc692-8101-4e3a-9e7b-289ef54c9c1f)

Nos vamos al login y vemos que el usuario correcto el el joe.

![image](https://github.com/user-attachments/assets/38a128e1-84ea-4565-aed4-36d496afd22b)

Este nos muestra un panel de administración donde podemos inyectar comandos en lenguaje python.

![image](https://github.com/user-attachments/assets/c010ec18-e6ed-46b2-a08c-f58840eb358a)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/db40abcf-6bdd-4caa-80e6-30fb4df9595b)

![image](https://github.com/user-attachments/assets/b79ae5ad-fcdc-41b0-9a07-df7515df2ccc)

Y ganamos acceso.

![image](https://github.com/user-attachments/assets/5544a3f3-4d45-440c-b01d-71838496a38c)

En el directorio /tmp encontramos un archivo oculto.

![image](https://github.com/user-attachments/assets/f0b203a3-f9b3-4ac5-9c3b-a4197feb135f)

![image](https://github.com/user-attachments/assets/85cb3125-41ce-4b7f-87bf-6d21e125f71c)

Convertimos el contenido del archivo que está en mayúsculas a minúsculas.

![image](https://github.com/user-attachments/assets/071a6bb9-384d-4719-b983-0a8fda45d597)

Y nos importamos en la máquina víctima un repositorio de github.

https://github.com/Maalfer/Sudo_BruteForce/blob/main/Linux-Su-Force.sh

![image](https://github.com/user-attachments/assets/e34fa176-220b-4784-8f45-dab1c494bbdd)

Le damos permisos y lo ejecutamos.

Sabiendo las credenciales del usuario (joe:chittychittybangbang) nos conectamos al servicio ssh.

![image](https://github.com/user-attachments/assets/8bd37319-d450-4c6f-a64d-d40357cd036c)

Hacemos sudo -l y vemos esto:

![image](https://github.com/user-attachments/assets/c8e9a2fe-bc49-4ae1-9e8a-19fdb13e17c3)

Nos conectamos como luciano.

![image](https://github.com/user-attachments/assets/bdff6c95-e1cd-46b0-9c15-d330ecce3b8c)

Volvemos a hacer sudo -l y nos muestra esto:

![image](https://github.com/user-attachments/assets/5d812fab-1239-4953-b3be-5f84f270184a)

Seguimos estos pasos y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/c8542faf-8f95-415c-a538-4b8975f2933b)








