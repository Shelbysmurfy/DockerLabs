# RESOLUCIÓN DE LA MÁQUINA LIBRARY

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/8a354bb1-b250-4484-af0f-33e335dd958d)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/dd23cd7f-461e-44f0-84d5-7dabf44bbb44)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/5e9b7ab1-437d-4227-9958-6a2c32367e28)

Entramos en la web.

![image](https://github.com/user-attachments/assets/1602df33-39fc-4301-88f6-75c55efd06d1)

Hacemos fuerza bruta con dirsearch.

![image](https://github.com/user-attachments/assets/a87d29fe-4b38-4c92-8d19-98e2cec29a87)

Entramos en el index.php y vemos esto: 

![image](https://github.com/user-attachments/assets/f11d1808-d44e-46ac-b9aa-acd687de20cb)

Hacemos uso de la herramienta hydra usando como contraseña lo que hemos encontrado.

![image](https://github.com/user-attachments/assets/3076aaa3-58c3-42d2-9acf-7e79b49d0568)

Entramos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/a2b23597-d841-4391-919d-dd757aec06ab)

Hacemos sudo -l y vemos lo siguiente: 

![image](https://github.com/user-attachments/assets/bbba2daf-42e0-4847-a7d3-f2b00d43ae0e)

Borramos el script.py del directorio opt y creamos otro con el mismo nombre pero diferente contenido.

Lo que pondremos se basara en lo que nos sale en el GTFObins, que es para ganar privilegios a través de python.

![image](https://github.com/user-attachments/assets/d946e7b9-b3f7-45fc-a808-982eb420fb3a)

![image](https://github.com/user-attachments/assets/d5ddd137-559d-4c90-b88a-2bc5f79dfcf8)

Y ya somos root.

![image](https://github.com/user-attachments/assets/0ffc192a-687a-4f8f-908f-475a0cc694c2)


