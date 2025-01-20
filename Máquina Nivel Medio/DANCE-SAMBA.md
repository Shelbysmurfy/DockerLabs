# RESOLUCIÓN DE LA MÁQUINA DANCE-SAMBA

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/d5543897-d337-4e3c-b5ca-122c0d9d0361)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/052b9a66-a9af-49e0-8e45-ae5821b6ffb5)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a0374ebb-858d-4be2-a96c-8196a24e386c)

Entramos al puerto 21 (ftp), con el usuario anonymous.

![image](https://github.com/user-attachments/assets/e45b9564-20ad-497e-84d8-64b2afa5c326)

Abrimos el archivo nota.txt y vemos esto: 

![image](https://github.com/user-attachments/assets/0cd2f920-2245-40c6-a25d-65de257faa3f)

Hacemos uso de la herramienta enum4linux para ver los directorios smb activos.

![image](https://github.com/user-attachments/assets/a6f05bbd-d8a3-41cf-b7f5-450db4bce0fb)

![image](https://github.com/user-attachments/assets/093ff98a-6d6e-4a89-8894-46abcbffde4f)

Seguidamente sabiendo que hay directorios activos, y sabemos la existencia de un posible usuario: macarena, vamos a hacer uso de la herramienta crackmapexec para sacar credenciales válidas.

![image](https://github.com/user-attachments/assets/5136f6a8-8477-48d4-8dbc-6b5cabbece1e)

Teniendo credenciales válidas vamos a entrar al directorio macarena.

![image](https://github.com/user-attachments/assets/21a74457-afb9-4ce1-83be-67b55b6d1f93)

Encontramos la primera flag la del user.

![image](https://github.com/user-attachments/assets/871ec341-d1c5-4bda-99ad-95bce315aa42)

Si subimos una revershell, al no tener puerto 80, no podemos explotarla. Por tanto, lo que vamos a hacer, va a ser crear una llave SSH de 2048 bits en formato openssh con la herramienta puttygen.

![image](https://github.com/user-attachments/assets/3799320c-e4d2-4db0-a47f-a546823d7bd6)

Seguidamente ejecutamos el siguiente comando para extraer la clave pública del archivo que hemos creado de clave privada.

![image](https://github.com/user-attachments/assets/1f156caf-2e06-4274-be3a-0579af850947)

Le damos permisos 600 al archivo que id_rsa.

![image](https://github.com/user-attachments/assets/360d0095-b539-48ec-b62c-1629eba9d25c)

Cuando lo subamos tendremos que crear un directorio .ssh, donde pondremos nuestra clave pública.

![image](https://github.com/user-attachments/assets/4d505f18-d58a-46e2-9f43-bbf12d4c3f8e)

Y de esta manera podemos conectarnos al servicio ssh con el usuario macarena.

![image](https://github.com/user-attachments/assets/8119ed88-6725-4fb1-8de8-990545fee14f)

Nos vamos al directorio /home/secret y encontramos una posible clave cifrada.

![image](https://github.com/user-attachments/assets/93e699ba-2290-4bbb-9472-ad4961bb4067)

Nos vamos a cyberchef y las desciframos.

![image](https://github.com/user-attachments/assets/78b46eb0-c519-410f-a4af-0c6bce25e058)

Hacemos sudo -l ponemos la credencial que hemos obtenido y ganamos acceso.

![image](https://github.com/user-attachments/assets/ec7a3736-5870-46ed-ac71-bc9009929ba7)

Viendo el permiso SUDO que tenemos, vamos a buscar posibles archivos que no podamos abrir. encontramos uno en el directorio /opt

![image](https://github.com/user-attachments/assets/af52d59c-f2ed-4b56-9d74-3177fb4344c0)

Ejecutamos el permiso y el archivo contiene unas credenciales.

![image](https://github.com/user-attachments/assets/507cd90b-2e4f-4a7e-bca2-110b4c2a094b)

Nos conectamos como usuario root con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/1557fa21-575e-471b-9025-142989fc2d72)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/15d062bb-8288-45fd-8dff-5abb7a74bda4)




