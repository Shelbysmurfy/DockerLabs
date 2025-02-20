# RESOLUCIÓN DE LA MÁQUINA FORGOTTEN_PORTAL

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/8e6ef28d-3417-4761-a48e-d854d5d03a16)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/01d097fa-26dc-4aa5-aa4e-fdd251dbcad2)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/76699ade-4a82-4296-b2d0-61e5589210bc)

Abrimos la web.

![image](https://github.com/user-attachments/assets/70a5cf8c-ad0f-4000-849a-0e63e073b63b)

Miramos el código fuente de la página y nso dan de pista un posible usuario y una ruta.

![image](https://github.com/user-attachments/assets/2607597f-e23c-4f21-873b-9c5a2985bda9)

Vamos a la ruta y vemos una subida de archivos.

![image](https://github.com/user-attachments/assets/79daabdc-a28b-4cab-9951-4a6780b5dd27)

Subimos un archivo malicioso.

![image](https://github.com/user-attachments/assets/9374ef3d-3942-4737-97cb-0d3911fc9367)

Y vemos que podemos inyectar comandos correctamente.

![image](https://github.com/user-attachments/assets/aa01e2c9-5f48-429f-a565-e7dea07b2ebd)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/f82f0ac2-1344-4ae4-ac41-574cee6a77a1)

Encontramos un archivo, acces.log que tiene una clave codificada.

![image](https://github.com/user-attachments/assets/0593622a-e467-4351-baf9-3d01c3775f54)

Nos vamos a cyberchef y sacamos unas credenciales válidas, para un usuario existente.

![image](https://github.com/user-attachments/assets/901559a8-11ff-404d-9ba6-794ae8531aad)

Nos conectamos como alice con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/f43c1e71-681f-4b11-92d9-a11260fba38c)

Y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/90d4077c-6d52-4eaa-a0a8-1b6f212c3635)

Encontramos un archivo con información muy importante, sobre una posible clave id_rsa que comparten todos los usuarios.

![image](https://github.com/user-attachments/assets/08323082-4bfe-4bcb-b4dc-67b4be5e5c46)

Y ya la hemos encontrado.

![image](https://github.com/user-attachments/assets/2550011d-cbb0-4fc5-a80d-e4f96ad0cc8d)

Nos traemos la clave id_rsa a nuestra máquina, le damos permisos, y nos conectamos como usuario bob, con la passphrase que nos han dado anteriormente.

![image](https://github.com/user-attachments/assets/fcc932e7-53ba-490b-9376-7690d727f420)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/5aaf8003-0d27-4424-aae6-f262086afeb7)

Y ya somos root.

![image](https://github.com/user-attachments/assets/7e9a9d19-ca3c-4cf5-b286-b1539096a2a2)

Y conseguimos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/95c2e6a6-a30d-4b24-9be1-6757b67dee7e)

