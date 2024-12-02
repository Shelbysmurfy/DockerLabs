# RESOLUCIÓN DE LA MÁQUINA PICADILLY

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/3b20a136-6d31-41fe-bff7-febcd5b20394)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/544f9680-3d86-4fd9-86a0-e3873ffa6612)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3271c5ad-72a1-45f1-9b78-c17ad13ffc95)

Abrimos la web por el puerto 80 y nos encontramos el archivo backup.txt

![image](https://github.com/user-attachments/assets/ff003742-cb8f-4a80-8aff-a2d7835eaf60)

![image](https://github.com/user-attachments/assets/7f0b5b87-23c3-4bb3-a601-9e022070ff24)

Nos da la pista que tenemos que usar un metodo de descifrado de un antiguo emperador romano.

Investigamos por internet y nos encontramos con el cifrado de César.

Así que usamos un decoder para descifrar la contraseña que tenemos encriptada.

![image](https://github.com/user-attachments/assets/80174690-a0b3-4042-b669-78ba0c0820b7)

Entramos en el puerto 443.

![image](https://github.com/user-attachments/assets/809fde6b-3915-48a4-87e1-e55648417f20)

Vemos que hay una subida de archivos, así que vamos a intentar subir un archivo malicioso.

![image](https://github.com/user-attachments/assets/025fa963-8403-4714-bca0-586f95cf3452)

![image](https://github.com/user-attachments/assets/5ebe4fe7-b62f-4c0f-b2ce-3d855505c5c1)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/82447cf5-8592-49d8-80fa-a56d2d71ea63)

Entramos como usuario mateo con las credenciales obtenidas, pero la contraseña es quitándole la "x".

![image](https://github.com/user-attachments/assets/fd68122f-d42a-4b6e-883b-009b90386af2)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/ab499908-4cda-4751-bbb2-ea748160140a)

Y ya somos root.

![image](https://github.com/user-attachments/assets/b625184c-22e7-4fa8-8387-e348453f2dc9)








