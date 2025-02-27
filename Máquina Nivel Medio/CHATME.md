# RESOLUCIÓN DE LA MÁQUINA CHATME

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/aab04764-92fd-4d72-832c-563ab401dad0)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/9cddaee8-108f-4ede-8275-5eb555d41609)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/e4ca6bd4-63fe-4fef-a55c-9f65cf4c481e)

Abrimos la web.

![image](https://github.com/user-attachments/assets/cfb71f2e-6bf1-4395-a0ca-ba2543bdcf82)

Encontramos un dominio, vamos a añadirlo al /etc/hosts

![image](https://github.com/user-attachments/assets/593d1e6c-9941-4872-9759-5686518da7f1)

![image](https://github.com/user-attachments/assets/67ff42af-eb45-4f8c-8a5a-09866c809b70)

Hacemos fuerza bruta con ffuf en busca de subdominios para la ruta que indicamos.

![image](https://github.com/user-attachments/assets/440f9c0a-636d-4120-8dd1-9c424c19b355)

Añadimos la nueva ruta a nuestro /etc/hosts, y la abrimos.

![image](https://github.com/user-attachments/assets/acf735a6-f2b7-4143-9ad2-2818fb1e4063)

![image](https://github.com/user-attachments/assets/e46b0d8e-76b7-4f69-949d-341e9be7bcde)

Nos pide un nombre de usuario, lo añadimos y vemos una posible subida de archivos.

![image](https://github.com/user-attachments/assets/28f4a143-ef4b-462e-af84-ed9b729887d7)

Hacemos fuerza bruta con dirsearch para buscar posibles rutas disponibles.

![image](https://github.com/user-attachments/assets/7b89216e-dd2f-4a63-9e9c-a42f9a52eb94)

Vemos que podemos subir archivos,. pero al probar con un archivo.php malicioso no conseguimos nada.

Hay una vulnerabilidad crítica en whatsapp que permite la ejecución automática de archivos maliciosos con la extensión .pyz (python).

Vamos a hacer una reverse shell, subiendo un archivo.pyz malicioso a la subida de archivos que tenemos.

![image](https://github.com/user-attachments/assets/8b108152-267b-4d6a-8642-feb72eca31a1)

![image](https://github.com/user-attachments/assets/2f462f1e-2f32-4339-97f2-125bb6da7a72)

Esperamos un poquito y ya tenemos una shell.

![image](https://github.com/user-attachments/assets/4c9d912d-8316-410c-b29c-a0202bd35ac5)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/3195f039-628b-4627-a0f3-685ee6cf27ff)

Este código crea un archivo vacío llamado "pwned" en el directorio "/tmp" cada vez que se ejecuta.

![image](https://github.com/user-attachments/assets/00868ee2-10a9-4ad9-9f90-e26f3edede4b)

Y ahoara ejecutamos este código, donde el echo "test", refleja el mensaje que enviarías en un correo electrónico y lo otro sería el permiso SUDO, seguidom de -m para indicar el archivo que hemos creado.

Podemos ver que hemos creado un archivo llamado pwned como root.

![image](https://github.com/user-attachments/assets/adca2bee-15bb-4912-b924-1fc08faa638a)

Así que ahora vamos a entrar al archivo, le añadiremos un "chmod u+s /bin/bash", y escalaremos privilegios.

![image](https://github.com/user-attachments/assets/dfea7e5e-c19f-49fa-a9b2-9c80fd4551a4)

Volvemos a ejecutar el mismo comando que antes, y si miramos los permisos de /bin/bash, vemos que es un binario SUID, lo que significa que se ejecuta con permisos de root, sin importar quién lo ejecute.

![image](https://github.com/user-attachments/assets/f422bc27-d8ee-4a64-bfc5-7e4794bcd1d1)

Hacemos "bash -p" y ya somos root.

![image](https://github.com/user-attachments/assets/c69fde10-b1e8-4153-9e7c-b8cf288a4520)


