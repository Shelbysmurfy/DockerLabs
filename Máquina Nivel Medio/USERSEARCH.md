# RESOLUCIÓN DE LA MÁQUINA USERSEARCH

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/1c6b9d47-5267-45a5-a0f5-629f1c7c4701)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/3e8b7ad6-6a71-45d0-8344-e5fcf5ec6f39)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/69293a97-08e5-4364-bacd-7e1cfc8c354e)

Entramos en la web.

![image](https://github.com/user-attachments/assets/d93c451a-9ce0-4711-a33d-5a3616f4b084)

Usamos un usuario básico como es admin y nos devuelve una contraseña.

![image](https://github.com/user-attachments/assets/03ce53a5-b90c-47d5-a7c4-8fe76a774f42)

Probamos las credenciales para el servicio ssh y no funcionan.

Hacemos fuerza bruta con gobuster y encontramos una posible base de datos.

![image](https://github.com/user-attachments/assets/1b3bbfda-b0b3-42c0-84ad-56e7012fed23)

Nos conectamos a la base de datos. 

![image](https://github.com/user-attachments/assets/eee4d169-b832-457f-b5d9-f8c0bc454d55)

![image](https://github.com/user-attachments/assets/0845b130-f91f-441e-9105-8ce1e841d902)

Nos metemos en la base de datos testdb.

![image](https://github.com/user-attachments/assets/85c00590-b884-49d6-a0ac-6414f79bffd1)

![image](https://github.com/user-attachments/assets/2b6f38ad-6092-4e0f-b09b-fc10e9842c76)

Y ahora nos vamos a la tabla users.

![image](https://github.com/user-attachments/assets/db375ce7-a746-43d7-a69e-d4bff4608eba)

![image](https://github.com/user-attachments/assets/3af182cb-a572-443b-88a5-55c8b9fbbd6e)

Y ahora extraigo los datos de esta tabla.

![image](https://github.com/user-attachments/assets/81ad305e-d8c6-4fc8-b5ba-30d4086e1ef6)

![image](https://github.com/user-attachments/assets/81ecbaf7-78b1-4891-850a-fcaced5fb48b)

Probamos los tres usuarios, y conseguimos conectarnos con las credenciales (kvzlx:kvzlxpassword)

![image](https://github.com/user-attachments/assets/77fb07a1-8de7-460c-a34f-d44a21de1b49)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/93466b99-81a3-49f1-8c1b-db9e002e0157)

Miramos los permisos que tenemos sobre el archivo, lo borramos y creamos un archivo.py para escalar privilegios.

![image](https://github.com/user-attachments/assets/06fb5122-543a-4694-925a-1cef9d2ecdf1)

Y ya somos root.

![image](https://github.com/user-attachments/assets/1c444aab-6f5a-48d8-b880-0d26c34d3367)




