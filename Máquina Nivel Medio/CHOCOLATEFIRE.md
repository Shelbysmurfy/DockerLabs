# RESOLUCIÓN DE LA MÁQUINA CHOCOLATEFIRE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/995c1087-0521-4cba-ae7f-49536b1afad3)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/515ee773-60e6-4705-bff3-5e0ad09e68cd)
![image](https://github.com/user-attachments/assets/073d7957-9533-4b08-99b6-a44e23d195fd)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/30884321-9481-49c7-b0ad-813af253a47f)
![image](https://github.com/user-attachments/assets/490d911a-160d-4f92-b558-9ebb8409434c)

En el puerto 9090, encontramos un login.

![image](https://github.com/user-attachments/assets/4f96969f-d917-4f56-a32f-fa7773b32b42)

Nos conectamos con las credenciales básicas "admin:admin".

![image](https://github.com/user-attachments/assets/d3d544f6-85eb-4539-9727-f8fe8301b858)

Encontramos una subida de archivos.jar

![image](https://github.com/user-attachments/assets/db283e52-d890-4947-a214-e11859bcb7b8)

Antes de probar a subir algún archivo malicioso, vamos a probara a usar hydra en para el usuario chocolatitochingon, que vemos en el apartado de users.

![image](https://github.com/user-attachments/assets/cf415f4f-4c0e-44ab-a7d2-23ad5c3ab322)

Encontramos unas credenciales válidas "chocolatitochingon:chocolate".

![image](https://github.com/user-attachments/assets/9bf43fdf-875b-41f6-a651-390134707ca9)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/c09766b6-8816-435a-9e02-3464f72a164f)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/6b07f3b6-8bc8-41a6-a483-621a38ce0021)

Eejecutamos los pasos que nos dice el GTFObins y escalamos privilegios correctamente.

![image](https://github.com/user-attachments/assets/a35ae29d-a182-4081-841a-e75bcb738538)

![image](https://github.com/user-attachments/assets/d136b454-0d7a-47d8-9476-8ae48254b4dc)

Volvemos a hacer sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/28551f73-42fc-4e2f-bfb4-4c7cf9485793)

Miramos el contenido del script.sh antes de eejcutarlo.

![image](https://github.com/user-attachments/assets/0d0ffb53-0b1c-4c37-8ab7-9f2bd6cd9040)

Parece una bash eq Privilege Escalation: 

![image](https://github.com/user-attachments/assets/0e50c5a6-8d4f-49b8-8e4b-ad1baf0c943f)

Así que vamos a ejecutar el comando que nos dice para poder convertirnos en root "a[$(/bin/bash >&2)]+42".

![image](https://github.com/user-attachments/assets/1518ea35-6b69-4e5c-ac32-d0bdfa4880ac)

