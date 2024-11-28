# RESOLUCIÓN DE LA MÁQUINA PRESSENTER

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/ca45352d-9c70-48e2-898c-7e67bc884d24)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/7d17d1c9-6f2f-4aeb-ba97-fd19fcc63a6e)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/19ceb9ad-11f0-4bbc-855b-1185cfeefae9)

Abrimos la web.

![image](https://github.com/user-attachments/assets/e1b1abd6-5671-4f8a-94c3-6c5146611a26)

Añadimos el dominio de esta página al /etc/hosts.

![image](https://github.com/user-attachments/assets/f4baa52a-94b2-4eac-b430-8795e9fd84d2)

![image](https://github.com/user-attachments/assets/c896fec5-8268-448f-b9cd-32f7e74b926a)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/aeb45aa7-019e-4e87-9f1e-d8ff767a273f)

La única ruta interesante es la de wp-login.php, que nos lleva a un login de wordpress.

![image](https://github.com/user-attachments/assets/2e3fb8bc-314f-4d3a-ad7d-6286078f236b)

Si ponemos un usuario mal nos lo dice, después de estar investigando un rato por la web hemos encontrado un usuario que parece ser correcto.

![image](https://github.com/user-attachments/assets/7136fe34-1b06-4f28-b466-17d6737dd25b)

![image](https://github.com/user-attachments/assets/c79a5881-b14b-4271-a2f7-faae2b12a0e3)

Hacemos uso de la herramienta wpscan para buscar la contraseña del usuario pressi.

![image](https://github.com/user-attachments/assets/b170b93a-b480-411c-bc7e-a66d6b0049e6)

![image](https://github.com/user-attachments/assets/26b596c2-85be-405a-81d9-6ac42f848d46)

Entramos en el login de wordpress con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/900a4c05-08b7-46ee-850b-b1957f37783f)

Nos descargamos el pluggin File Manager, y subimos el archivo php malicioso.

![image](https://github.com/user-attachments/assets/427d4824-b3ee-4e3d-a560-c95b55e799b6)

Nos vamos a la ruta y lo abrimos.

![image](https://github.com/user-attachments/assets/c7451148-21cf-4dca-aedf-3da75a49c49b)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/d3895906-23a0-4069-ac26-a26288e4204a)

Encontramos unas credenciales de una base de datos en la carpeta de wp-config.php

![image](https://github.com/user-attachments/assets/d84c7e06-c91c-4421-b50b-a1ff3c1a8563)

Nos conectamos al servicio de mysql con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/ef6e5dd0-aa03-4548-94ac-729ed3295a69)

Conseguimos las credenciales de un usuario que hemos podido ver antes en el directorio home.

![image](https://github.com/user-attachments/assets/1923e2bd-39c9-4648-b16e-7a94ced8de07)

![image](https://github.com/user-attachments/assets/6581ee2c-53ed-4dda-854b-9869ee1f0183)

Nos conectamos como usuario enter.

![image](https://github.com/user-attachments/assets/85114904-5b14-4976-9ee7-c72c7025ff00)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/9b1feae3-0f4e-4a46-b04f-7ca8b042d8d3)

La información que nos da no sirve para nada, y al parecer no hay nada que nos permita elevar nuestros privilegios.

Después de un buen rato buscando y probando he podido elevar privilegios.

Usando como usuario: root y como contraseña: kernellinuxhack, la misma password que hemos usado anteriormente con el usuario enter.

![image](https://github.com/user-attachments/assets/001ab000-cc30-4d6f-b5ae-a40db6ff6925)

