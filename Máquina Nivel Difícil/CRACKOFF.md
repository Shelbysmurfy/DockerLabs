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

