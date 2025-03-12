# RESOLUCIÓN DE LA MÁQUINA CACHOPO

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/f0a4c999-363a-416e-84e1-9c1b1462513f)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/deecee82-c953-4ca5-9090-4e7aeb203601)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/9a0fa739-c681-4e61-bdf2-f45ed0cecd36)

Abrimos la web.

![image](https://github.com/user-attachments/assets/0179d288-24f1-41f6-b3d7-ed0e74e9d1bd)

Encontramos un formulario para hacer una reserva, pero no funciona, vamos a abrir el BurpSuite para ver la petición.

![image](https://github.com/user-attachments/assets/1b00c31e-b483-46e5-85b4-8340d4074d67)

![image](https://github.com/user-attachments/assets/2d0c2d0a-895a-411e-bfc0-56073d5c498a)

Miramos información sobre el error que nos devuelve "Incorrect padding".

![image](https://github.com/user-attachments/assets/7706a8bf-a026-467d-b580-e53a4781977a)

Miramos de ejecutar pol en base 64 y nos devuelve esto: 

![image](https://github.com/user-attachments/assets/15774894-7448-4d30-a285-959868a09c46)

Intentamos ejecutar el comando "cat /etc/passwd" en base64 y nos devuelve resultado.

![image](https://github.com/user-attachments/assets/55b6b584-facd-4166-9465-4c0ee9adf461)

Vamos a hacer fuerza bruta con hydra para el usuario que hemos encontrado "cachopin".

![image](https://github.com/user-attachments/assets/74506e68-e78b-45c3-8fa5-f957a70cf2c4)

Nos conectamos al servicio ssh con las credenciales obtenidas "cachopin:simple".

![image](https://github.com/user-attachments/assets/ee5a3782-10ca-4af3-9f87-ba76051b4cb0)

Después de un rato buscando nos encontramos con una lista de hashes.

![image](https://github.com/user-attachments/assets/1dc9719f-4b83-4b4f-b94d-932c752e952a)

Para estos tendremos que usar una herramienta que tiene el creador de esta máquina en github, ya que si intentamos con john no vamos a conseguir nada.

Github: https://github.com/PatxaSec/SHA_Decrypt

Instalamos una libreria.

![image](https://github.com/user-attachments/assets/cd413248-f2cb-47ce-b236-d5c77bb4b9ac)

Nos copiamos el archivo sha2text.py en nuestra máquina.

![image](https://github.com/user-attachments/assets/c110b248-4a68-4bf1-a58e-a32b5066d7b1)

Y ejecutamos el siguiente comando con cada uno de los hashes hasta obtener resultado. 

![image](https://github.com/user-attachments/assets/fa4f34cf-0ccd-4c70-972d-c78e82a81672)

En el segundo hash obtenemos una respuesta.

![image](https://github.com/user-attachments/assets/bd097bf8-9c20-40f5-b4e1-b6988a6e0a21)

Como antes en el /etc/passwd no habíamos visto más usuarios, vamos a probar esta credencial como contraseña del usuario root.

Y ya somos root.

![image](https://github.com/user-attachments/assets/4eabd110-2c65-4e0d-963d-bebeae6a10b9)
