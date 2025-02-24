# RESOLUCIÓN DE LA MÁQUINA BADPLUGIN

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/bec7e796-b533-4d7c-ac4f-3b5e9dd99f06)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/2e0d172b-d907-4639-bbf3-04c46c8a395a)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/1f9beb85-c6b9-4616-936e-2dd32884b65f)

Abrimos la web.

![image](https://github.com/user-attachments/assets/c7c9a94c-0bf9-44b6-b6ab-b481fa572b83)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/d80a777b-b0bb-417d-905e-38b4b498dff8)

Intentamos entrar en /wordpress, y no nos deja, así que vamos a hacer otra vez gobuster.

![image](https://github.com/user-attachments/assets/269cf124-1afc-48ea-9c96-4af83a6be19e)

Cuando intento entrar en /wordpress/wp-admin/, me sale este error mencionando un dominio, así que vamos a arreglarlo.

![image](https://github.com/user-attachments/assets/d634101e-f49b-4314-8a8f-a3c8473c37db)

Y ya podemos entrar.

![image](https://github.com/user-attachments/assets/295fd338-f608-4c35-af5e-1624996c8e82)

Intentamos credenciales básicas "admin:admin" y vemos que el usuario admin es correcto pero su contraseña no.

![image](https://github.com/user-attachments/assets/cc7254d3-9d0b-4f16-a85a-a1a746ec8fb0)

Vamos a hacer uso de la herramienta wpscan para encontrar la contraseña de el usuario admin.

![image](https://github.com/user-attachments/assets/ee6f2fc2-99d5-4b4d-82a6-bf2880ccdb2f)

![image](https://github.com/user-attachments/assets/13921ae4-64bc-4f02-9f8b-ccf65d9d6e38)

Nos conectamos al servicio de wordpress con las credenciales "admin:rockyou".

![image](https://github.com/user-attachments/assets/d6217be0-795d-4863-8e14-8aede878e3ce)

Nos vamos a plugins y vemos una subida de archivos.zip

![image](https://github.com/user-attachments/assets/a5fe8cd0-7501-436f-a1a0-ffa845d55da7)

Creamos un archivo.zip malicioso (muy parecido al pentest_monkey), y lo subimos.

![image](https://github.com/user-attachments/assets/9defe1db-0571-409d-ab08-c9a6e71d7a94)

![image](https://github.com/user-attachments/assets/487312fc-9c92-43eb-b4e3-e71a5e0d0bdd)

Lo activamos mientras estamos en escucha desde la terminal y ganamos acceso.



