# RESOLUCIÓN DE LA MÁQUINA CRACKOFF

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/8969c6dc-103f-4255-ab7c-2816eb5b4c5d)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/57460607-65d1-49bb-9e59-023bcfc040f1)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/ae6a87d2-f136-4564-8df6-f2bb89dee508)

Abrimos la web.

![image](https://github.com/user-attachments/assets/f90d9464-45fe-48a6-bac0-44f59dec5321)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/a8d32833-cea5-451d-b95e-a40b7479cc53)

Abrimos el login.

![image](https://github.com/user-attachments/assets/765ae535-eba8-417f-a3b3-24f80fc03a04)

Intentamos a hacer SQLI con el comando '' or 1=1; --' y observamos que es vulnerable.

![image](https://github.com/user-attachments/assets/6c6b4a16-74c1-4330-8a96-84143184397b)

![image](https://github.com/user-attachments/assets/e6506b63-a26c-4c4f-ae87-37eee12b9dca)

Nos vamos al directorio /welcome.php y nos menciona qu podemos usar sqlmap para extraer datos.

![image](https://github.com/user-attachments/assets/c773b2aa-d386-45d4-82c6-cda6e20dba6a)

Hacemos un sqlmap, con el código del login.php y vemos estas credenciales.

![image](https://github.com/user-attachments/assets/690438f3-db2c-49bb-92f8-4c10ff18771a)

![image](https://github.com/user-attachments/assets/e4d1f805-b434-4f5f-a973-208a75ae57b0)

Vamos a guaradarlas en diferentes archivos, y vamos a usar hydra para ver que credencial es la que tenemos que usar para el servicio ssh.

![image](https://github.com/user-attachments/assets/0163dd98-6b8b-48b3-94e4-d98fb0701444)

![image](https://github.com/user-attachments/assets/b6a0b844-1ef8-4a2e-95b9-67ae68202efc)

Nos conectamos al servicio ssh con las credenciales obtenidas 'rosa:ultramegaverypasswordhack'.

![image](https://github.com/user-attachments/assets/55b28c03-b5ad-4c02-b2fa-6a85ed42cffe)

Nos traemos la herramienta linpeas a nuestra máquina víctima con wget, le damos permisos y lo ejecutamos.

![image](https://github.com/user-attachments/assets/5035c70d-5c43-4e69-8eb5-da69f20b314a)

Encontramos un archivo.txt de el usuario alice.

![image](https://github.com/user-attachments/assets/f497464e-f6ea-4e7e-bbf1-0d6daf9feab1)

Es una nota y dentro de esta encontramos una posible credencial.

![image](https://github.com/user-attachments/assets/a25d5adc-5a70-4b4b-bafd-b7b7beceddf0)

La probamos para todos los ususarios que tenemos pero no funciona.

Seguidamente hacemos uso del comando "netstat -an", y vemos esto: 

![image](https://github.com/user-attachments/assets/2881131a-161c-4308-aa8c-6b96cb892823)

Usamos curl vemos que tomcat esta corriendo por el puerto 8080.

![image](https://github.com/user-attachments/assets/e7e9be82-3299-48b2-b662-8bab27abbb5c)

Nos traemos el chisel a nuestra máquina.

![image](https://github.com/user-attachments/assets/0bf298bd-6c34-4e4e-a0fb-5b2e50fedc44)

Primero iniciamo un servidor de chisel desde nuestra máquina atacante.

![image](https://github.com/user-attachments/assets/cf9d6e21-1ed3-4009-9be6-749a7076a1b8)

Y ahora desde nuestra máquina víctima establecemos el client a traves de la conexión con la máquina atacante por el puerto 9090. Seguidamente usamos "R:8080:127.0.0.1:8080", esto le dice al client de chisel que establezca un túnel inverso desde el puerto 8080 en la máquina víctima, hacia e puerto 8080 de la máquina atacante. Y una vez hecho esto podremos acceder a Tomcat que se esta ejecutando en la máquina víctima desde nuestra máquina atacante a través del localhost.

![image](https://github.com/user-attachments/assets/a8a659a7-100c-4be5-9c42-9aa5447bbda7)

Abrimos el Tomcat en nuestro navegador.

![image](https://github.com/user-attachments/assets/eff8f7f3-86ce-42a1-a2ae-6f93d3ec50e6)

Nos pide unas credenciales al intentar hacer cualquier cosa, así que vamos a hacktricks para ver que podemos hacer.

![image](https://github.com/user-attachments/assets/ce91e167-c4e5-4926-bc59-bac8abea2df0)

Nos dice unas credenciales default, que si probamos no funcionan, pero un poco más abajo vemos que podemos abusar de una vulnerabilidad.

![image](https://github.com/user-attachments/assets/9b235d0d-eee0-4c78-bcf0-cf51ec410d62)

Añadimos el rhosts que viene a ser la IP por la cual se está ejecutando el Tomcat y seguidamente añadimos los dos diccionarios que habíamos creado antes con las credenciales que habíamos encontrado gracias a sqlmap.

![image](https://github.com/user-attachments/assets/b14d590f-2aa9-49c5-b14d-5c982365dcaf)

Lo ejecutamos y encontramos una credencial válida "tomitoma:supersecurepasswordultra".

![image](https://github.com/user-attachments/assets/355ac35b-dfe3-4170-86ef-37725e76bcd2)

Nos conectamos con las credenciales obtenidas y vemos una subida de archivo.war

![image](https://github.com/user-attachments/assets/ab2977b7-eca1-4e8f-ab27-b9a312dd90b5)

Subimos el archivo.

![image](https://github.com/user-attachments/assets/40fc8f4d-844e-4edf-b7ac-e91717b79da5)

![image](https://github.com/user-attachments/assets/333bcce4-577d-49af-9053-0621a7b87237)

Lo abrimos mientra estamos en escucha con netcat y ganamos acceso correctamente.

![image](https://github.com/user-attachments/assets/69c16564-796a-4b59-bd7d-3080d7aca28b)

![image](https://github.com/user-attachments/assets/af4d669d-bebe-4739-b216-a49f2e2387e5)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/2196eb42-afa6-427f-bd9c-2b826f6a0dc0)

Nos vamos al archivo y vemos que tenemos permisos para editar el archivo.

![image](https://github.com/user-attachments/assets/20dbd0b9-9e1d-4c61-828f-12afe7cab33f)

Escalamos privilegios con sh con este comando: 

![image](https://github.com/user-attachments/assets/0986d07b-2656-4d97-ae8c-7a2d74241f10)

Iniciamos el permiso SUDO.

![image](https://github.com/user-attachments/assets/2a3a0aff-af9d-4d8d-9563-8291a31e211b)

Hacemos bash -p y ya somos root.

![image](https://github.com/user-attachments/assets/b6df7111-5298-4a6b-a0a7-c72d486e8187)

Y encontramos la flag del usuario root.

![image](https://github.com/user-attachments/assets/6841a458-a5b7-4555-a9d9-5a264ca674bb)

