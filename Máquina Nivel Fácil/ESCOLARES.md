# RESOLUCIÓN DE LA MÁQUINA ESCOLARES

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/8e12f8eb-d836-4293-9a8f-6fa7df26ae9d)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/21c7afba-3034-475e-8349-a714236ca9fe)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/60ff3c13-d160-4442-bf43-1339d4dbbff7)

Entramos en la web.

![image](https://github.com/user-attachments/assets/7f869f53-205a-42d3-933f-84f975a6b60b)

En el código fuente nos dan una pista sobre un directorio.

![image](https://github.com/user-attachments/assets/9e461fed-a596-4548-9c29-2ae64e64829b)

Nos encontramos con una lista de profesores y datos sobre ellos.

![image](https://github.com/user-attachments/assets/5ecd0bba-da97-4c31-8134-478e95762281)

Hacemos fuerza bruita con gobuster para buscar directorios.

![image](https://github.com/user-attachments/assets/704cf205-c96b-41fc-84a4-f0e2bfa2363d)

Volvemos a hacer fuerza bruta pero poniendo en la ruta el directorio wordpress.

![image](https://github.com/user-attachments/assets/6547c758-d780-4973-afef-d8d1f4131a82)

En el wp-admin, no me deja entrar por el dominio, así que vamos al /etc/hosts y lo añadimos para poder tener acceso.

![image](https://github.com/user-attachments/assets/430d8480-2a97-4f84-9d8b-fb78bb1d8487)

![image](https://github.com/user-attachments/assets/5717b18b-7698-4a00-9a85-d8feb963d0f2)

Viendo el login de wordpress, en la página de usuarios hay uno que se llama luis que nos da información como si fuera admin de wordpress.

![image](https://github.com/user-attachments/assets/2011b4b6-69a1-422c-bffc-f9a49254f8ae)

Haremos uso de la herramiento cupp.py para ello antes tenemos que añadirla a nuestra máquina.

![image](https://github.com/user-attachments/assets/96507e20-c4d7-47e3-a28a-49aaa1751ae7)

Y ahora la ejecutaremos.

![image](https://github.com/user-attachments/assets/68e6b10e-92ae-473a-a68d-22dfe98bd535)

![image](https://github.com/user-attachments/assets/0bf09cb4-82ad-4582-864d-bdd1194890a5)

Haremos wpscan para saber su contraseña y de esta manera poder entrar como admin en wordpress.

Lo haremos con el usuario: luisillo y de password usaremos el diccionario que nos ha creado la herramienta cupp.py.

![image](https://github.com/user-attachments/assets/158f09a4-e477-4e62-8cc6-77b41ba582ed)

![image](https://github.com/user-attachments/assets/2d6a904a-3bc4-4940-87d3-5ad0c332aae7)

Entramos en el login de wordpress con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/051fa194-3269-472d-a42f-627627e2237e)

Nos vamos al WP File Manager, que esta descargado, y entramos en el apartado de /wp-content/uploads, y subimos el PentestMonkey.

![image](https://github.com/user-attachments/assets/ffbb2164-5591-4daa-a153-a9bb3a932f9c)

Nos vamos a los uploads de la web, y lo ejecutamos mientras estamos en escucha en nuestra terminal.

![image](https://github.com/user-attachments/assets/fe603787-ad7d-4ea6-8b1c-1a36e9da3004)

Y de esta manera ganamos acceso a la máquina.

![image](https://github.com/user-attachments/assets/729269f9-6230-445a-8391-2282f209d918)

Nos vamos al directorio home y nos encontrasmos con unas credenciales.

![image](https://github.com/user-attachments/assets/b90393e3-64fb-4a70-9bcc-837c948ef9c8)

De esta manera entramos como luisillo.

![image](https://github.com/user-attachments/assets/7f3493af-6276-45eb-a641-c0abccb8bb95)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b6a55e26-2065-4a03-b916-3e89f5722931)

Nos vamos al GTFObins y seguimos los pasos que nos dice.

![image](https://github.com/user-attachments/assets/6a4c610d-7deb-4ec4-a8cd-980c285a5790)

Y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/10ad2390-a898-40de-92b1-1133bd420e2c)








