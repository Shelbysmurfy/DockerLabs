# RESOLUCIÓN DE LA MÁQUINA MIRAME

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/cc880884-21ea-4ec1-a789-3e016d285278)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/2747980b-88fb-4737-8616-0df275f10477)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/da09a5b8-ef16-4fa9-830c-a5e801f5a78e)

Abrimos la web y nos encontramos un login.

![image](https://github.com/user-attachments/assets/eae2fa01-5054-4641-baaf-0319edc82374)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/154df804-ea1d-458b-976c-64dedb90198f)

Hacemos sql-injection, en el login y nos muestra el siguiente mensaje.

![image](https://github.com/user-attachments/assets/25d9b58b-252a-40c9-8abb-0b69d5a42efe)

![image](https://github.com/user-attachments/assets/6d5577c5-9927-4b60-a995-6b7a9cf8276c)

Procedemos a usar sqlmap para ver las bases de datos.

![image](https://github.com/user-attachments/assets/ea7e666d-c6e6-4f70-9784-311b90fa3d87)

![image](https://github.com/user-attachments/assets/b6b5190d-6d07-4aeb-a561-15ed944bb741)

Ahora usamos sqlmap para ver las tablas dentro uses.

![image](https://github.com/user-attachments/assets/7b04eede-cdf1-4c91-a815-e1d3a5121476)

![image](https://github.com/user-attachments/assets/cc61b5fb-13ae-4157-98e6-c4665ecf34c8)

Ahora lo usamos para ver las columnas dentro de la tabla usuarios.

![image](https://github.com/user-attachments/assets/ed992d4e-ed59-4a33-825d-d69d0071d798)

![image](https://github.com/user-attachments/assets/7982f917-52be-43ef-bc8b-639a6b450f21)

Finalmente lo usamos para ver el id, usuarios y contraseñas.

![image](https://github.com/user-attachments/assets/dea410a8-8e10-438a-acb2-386f97eb69eb)

![image](https://github.com/user-attachments/assets/0e9e40b7-20ca-42fe-b002-6c0094004ad5)

Nos vamos al login y vemos que el usuario correcto es el lucas.

Este nos redirige a page.php, donde tenemos una herramienta para consultar el clima.

![image](https://github.com/user-attachments/assets/badb3665-635a-4458-a942-6efaf803f52d)

Una de las credenciales se llama directoriotravieso, lo probamos a usarlo como un directorio y nos muestra esto: 

![image](https://github.com/user-attachments/assets/81c83534-113e-4bf6-b25a-210c4050196b)

Tenemos una imagen que puede contener información.

![image](https://github.com/user-attachments/assets/0eb55116-3443-4cd8-806a-7124a3216d62)

Vamos a hacer Esteganografía para ver si podemos sacar información.

Hacemos uso de la herramienta stegseek para sacar información de la imagen.

![image](https://github.com/user-attachments/assets/e42e3183-f04c-494d-bb3f-eac46c7630de)

Usamos la herramienta steghide con la passphrase que hemos conseguido y vemos un archivo .zip

![image](https://github.com/user-attachments/assets/a66e1c47-0734-4a2d-b3c0-4d811580e5b8)

Para romper este archivo usaremos zip2john para extraer el hash y luego usaremos john para obtener el password.

![image](https://github.com/user-attachments/assets/faa33113-1b53-4ba5-aa94-efde235585ef)

Descomprimimos el archivo con la contraseña que hemos conseguido y vemos un nuevo archivo .txt

![image](https://github.com/user-attachments/assets/07435d34-a32c-4250-9778-e7887da4eb1f)

Este archivo contiene unas credenciales.

![image](https://github.com/user-attachments/assets/cf505964-ebc9-4787-9dc0-af8f78e935f3)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/41a7cbcb-f193-4375-8940-5d38f5e6b011)

Hacemos búsqueda de permisos SUID y podemos observar que tenemos al binario find.

![image](https://github.com/user-attachments/assets/02f91ebd-8cb0-4c7e-b207-f159e7b714fb)

Nos vamos al GTFObins.

![image](https://github.com/user-attachments/assets/7b756c98-26c2-466d-80d7-bb0beea41ddd)

Y ya somos root.

![image](https://github.com/user-attachments/assets/99ec6fa8-a8b7-4bfe-b5c5-4d92ec24d165)





















