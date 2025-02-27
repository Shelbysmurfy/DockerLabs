# RESOLUCIÓN DE LA MÁQUINA INJ3CT0RSS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a6058bbd-9bd1-4c3d-af34-0420b258352b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/507c04c6-6669-483d-b3fa-fe0a3a37f965)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/0e29210f-61a9-4211-ba8c-4cdaf24651e4)

Abrimos la web.

![image](https://github.com/user-attachments/assets/e85867d5-abe1-4e26-b184-41d525824ff8)

Nos registramos y logueamos.

![image](https://github.com/user-attachments/assets/47f53b2a-b2f9-4fe5-8a17-9674b73f9815)

Una vez dentro vemos una serie de desafios.

![image](https://github.com/user-attachments/assets/4583584e-8989-4782-bfa5-91c797667289)

Pero no podemos entrar en ninguno ni hacer nada, así que volvemos a la plantilla de inicio de sesión y intentamos hacer SQLI, mediante un comando básico.

![image](https://github.com/user-attachments/assets/93e4cd83-91f4-40d7-a261-852d03cc7eff)

![image](https://github.com/user-attachments/assets/c71a5930-88c3-4210-8469-577e3bf8d2b6)

Como sabemos que es vulnerable a SQLI, vamos a usar el comando "sqlmap" en el login, para encontrar posibles credenciales.

Para ello primero tendremos que coger la petición con burpsuite de el login y guaradarla en un archivo en nuestra máquina.

Si cogíamos la petición con el comando "' or 1=1; --", nos lo url encodea y da error cuando hacemos sqlmap, así que le hemos puesto admin:admin, y de esta manera todo va perfecto.

![image](https://github.com/user-attachments/assets/52c7a9b5-ea73-494c-b296-30a82948eee3)

Ejecutamos el archivo con sqlmap a través del parámetro -r y encontramos una lista de credenciales.

![image](https://github.com/user-attachments/assets/c1ee62c6-dd5d-4e3d-9484-13a606f491bb)

![image](https://github.com/user-attachments/assets/adfa2491-fc2d-40aa-978d-60053250d570)

Usamos el "no_mirar_en_este_directorio" como directorio, y encontramos un archivo.zip

![image](https://github.com/user-attachments/assets/4995c7fa-b15f-4905-8b5d-d2a9b586490f)

Hacemos unzip y vemos que nos pide una contraseña, así que vamos a usar zip2john para obtener el hash, y con john lo vamos a romper gracias a el diccionario rockyou.

![image](https://github.com/user-attachments/assets/222075be-fdd9-4c79-9094-373fe20881f0)

Hacemos unzip de el archivo.zip con la contraseña obtenida, y conseguimos un archivo.txt.

![image](https://github.com/user-attachments/assets/ec11068c-cb5e-4810-9706-fccd8096768a)

![image](https://github.com/user-attachments/assets/ae06976c-a7d9-44cb-b3d9-d469ec3c0fd1)

Nos conectamos al servicio ssh con las credenciales obtenidas "ralf:supersecurepassword".

![image](https://github.com/user-attachments/assets/eee088a2-2a53-4cca-b96c-82bb6a654185)

Hacemos ls y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/76dc63f8-ae15-4155-813c-e22b461dbfe4)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/ac36ee04-29b0-48de-b0bc-e221a2b43c4f)

Solo nos permite usar busybox con cosas que esten en el directorio /nothing/, aprovechamos esto para tirar un directorio para atras y ejecutar el comando sh, ya que es lo que nos indica el GTFObins.

![image](https://github.com/user-attachments/assets/370b0231-1c71-4f05-a647-64cf30b5eb07)

![image](https://github.com/user-attachments/assets/20903ed1-07db-4ac7-8565-70d9785b0621)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/eb1b14ce-3e31-40cd-a1b8-d1169606a997)

Probamos a mirar con el permiso SUDO algun archivo dentro del usuario root, y encontramos el id_rsa.

![image](https://github.com/user-attachments/assets/c450617a-02a8-4dbe-b15a-1448aa583974)

Nos la traemos a nuestra máquina, le damos permisos y nos conectamos al servicio ssh como root.

![image](https://github.com/user-attachments/assets/ba1f6b98-d597-4b5c-a5cf-7825851b52a1)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/05cc922f-05dc-4659-ba6c-b66b67942bdd)

