# RESOLUCIÓN DE LA MÁQUINA MAPACHE2

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/25acf3aa-c209-41bd-a2a2-d3583c532aa5)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/372e32d5-5ed2-42f1-a2d0-bbfd33ee307c)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/009541a1-f046-4b7d-a938-9eeec559f48e)

Abrimos la web.

![image](https://github.com/user-attachments/assets/297c4c2b-a074-421f-a7a1-a3eda421022f)

Vamos a hacer fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/b5e0738e-e98d-4f4c-a5e3-7fe94a9d4de9)

Nos metemos en login.php y probamos algunas credenciales básicas pero no funcionan.

![image](https://github.com/user-attachments/assets/3ca76fd2-1b02-462e-bdc6-a6dcbcd3870c)

Nos metemos en el puerto 3306, que hace referencia a la base de datos y vemos un posible usuario.

![image](https://github.com/user-attachments/assets/1433f48f-d3a1-43ed-a988-a4bb8a3e2676)

Hacemos fuerza bruta con hydra en busca de una contraseña para el usuario medusa pero no encontramos nada.

Hacemos un cewl para crear un archivo.txt con palabras que hay dentro de la web, y con ellas buscar una posible contraseña para nuestro usuario.

![image](https://github.com/user-attachments/assets/4f97bb50-28f4-40e0-9a49-ad3f1f6d8baa)

![image](https://github.com/user-attachments/assets/3081600b-96c4-427f-976a-926248aced51)

Nos conectamos con las credenciales obtenidas "medusa:enthusiasts".

![image](https://github.com/user-attachments/assets/2cc5a80a-39f2-4ccf-b7ee-18818019d8ff)

Miramos el código fuente y vemos una pista.

![image](https://github.com/user-attachments/assets/97b690a8-336a-4d30-a5a7-15eaef2a5f43)

Probamos a hacer hydra para el servicio ssh con el usuario kinder, tanto en mayúscula como en minúscula pero nos sale nada.

![image](https://github.com/user-attachments/assets/59958e1d-3c0a-45cc-bba1-e109feb41eaa)

Después de un rato probando cosas, ponemos el nombre kinder con la k mayúscula, es decir "Kinder", y como contraseña medusa y ganamos acceso.

![image](https://github.com/user-attachments/assets/5fb72dff-99c2-4bb1-a953-7441e214ee73)

Hacemos ls y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/e6ddabe1-af07-4c83-954b-7770f5e0c2b4)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/f2d6f216-1ef8-4ad5-9926-3785983353f2)

Hacemos un find para buscar donde se encuentre apache2 y vemos esto: 

![image](https://github.com/user-attachments/assets/ff5413c0-e5f9-4ad6-b024-503bd7c970ab)

Nos vamos a la primera y vemos que el apache2 tiene estos permisos.

![image](https://github.com/user-attachments/assets/f5bd1d57-9ec1-46c9-931d-0afff0047b63)

Esto quiere decir que podemos leer, escribir y ejecutar el archivo. Así que vamos a editarlo para poder escalar privilegios y seguidamente vamos a ejecutarlo.

![image](https://github.com/user-attachments/assets/a73c0318-3478-4545-9cb4-dabe1be4ea9c)

Lo ejecutamos con el permiso SUDO que tenemos y ya somos root.

![image](https://github.com/user-attachments/assets/da632716-2d18-42ca-9d30-5961ca8250dd)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/17ced388-315b-4b7d-bc44-27bd97013b87)



