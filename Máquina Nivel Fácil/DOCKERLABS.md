# RESOLUCIÓN DE LA MÁQUINA DOCKERLABS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/756af11d-38e7-4262-b12b-09822a4161d7)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/7c1d3ee8-98c7-49e4-bfab-22984e2ff58a)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/c40c7776-ca6d-4e1b-8d52-b2666230aa92)

Abrimos la página web.

![image](https://github.com/user-attachments/assets/a297bbb4-23a0-4bd8-a252-e6475409b7a5)

Hago fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/a89161cb-9c79-43a3-a4ae-2568d797666b)

Entro en machine.php y me encuentro con una subida de archivos.

![image](https://github.com/user-attachments/assets/78cd9a97-5f53-4119-99f5-52201406b338)

Esta subida de archivos no permite la subida de archivos php, y nos salta que solo acepta archivos .zip

![image](https://github.com/user-attachments/assets/f6af872f-bffc-4229-a363-0c315cbc2bb8)

Intentaremos con burpsuite probar con todas las extensiones que funcionan como php, para ver si alguna la acepta.

![image](https://github.com/user-attachments/assets/8b8bd2d9-a32c-4bd8-a3f7-3fdf74824e89)

Finalmente con la extensión .phar si deja subir archivos.

![image](https://github.com/user-attachments/assets/94f8a5a7-9688-4cb3-84cb-eade8e38cf78)

Nos creamos un archivo shell.phar.

![image](https://github.com/user-attachments/assets/bdedfa2e-70bc-442d-86b4-00139cb37b05)

Lo subimos.

![image](https://github.com/user-attachments/assets/c4142de7-c6ce-4c02-8818-7fa59e839cb8)

Nos vamos al directorio /uploads, y ya lo tenemos.

![image](https://github.com/user-attachments/assets/46c5aba0-c0da-4b26-ac51-5744317e39ad)

Lo abrimos y ya podemos ejecutar comandos desde la url.

![image](https://github.com/user-attachments/assets/b6074cb0-3368-4651-a316-20bc93fe887d)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/3cdd9734-12e7-451e-9df4-68d79bfc08e6)

Nos ponemos en escucha desde la terminal y ganamos acceso a la máquina víctima.

![image](https://github.com/user-attachments/assets/d6f864b8-cc79-4b67-a3aa-33bc2098cff3)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/d189d61c-950d-4e63-9c11-163e95dab154)

Antes de ejecutar nada en el directorio /opt encuentramos un archivo .txt, que nos da información sobre una clave.

![image](https://github.com/user-attachments/assets/537c2986-d1db-491a-8bab-394137b57426)

Ejecutamos, siguiendo los pasos de GTFObins, las dos opciones que nos dan permisos como SUDO, y nos devuelven la contraseña, de el archivo clave.txt

![image](https://github.com/user-attachments/assets/00f0477d-2672-4823-93c4-a8443de9023f)

Y como nos decía el archivo txt, entramos como root, introducimos la contraseña y ganamos acceso.

![image](https://github.com/user-attachments/assets/80dba1fa-a65e-42c1-97db-b2f8ccfaa1bf)

