# RESOLUCIÓN DE LA MÁQUINA HACKPENGUIN

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a03b091a-05f2-4ff4-87d0-f4ba309b5027)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/1ae42c74-6399-4520-9f7b-c73295f01553)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/697723d4-8424-4afd-bc32-529f6bb2971c)

Abrimos la web y no hay nada.

![image](https://github.com/user-attachments/assets/086ef694-8308-4165-ae8a-95f5818b715d)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/46b97104-0bf5-4c17-a285-25e434514425)

Nos vamos a penguin.html y encontramos una imagen, nos la descargamos.

![image](https://github.com/user-attachments/assets/9dbdd79d-1ccb-4be7-84de-24a22564a31e)

Hacemos uso de la herramienta stegseek y encontramos la passphrase.

![image](https://github.com/user-attachments/assets/b0e9979f-213b-4af6-8f14-5bdd041b9de7)

Ahora usamos steghide y le pasamos la passphrase que hemos conseguido.

![image](https://github.com/user-attachments/assets/a18d177e-7549-41af-b49c-f860a3e86bf4)

Tenimos un archivo.kdbx que no podemos abrir, vamos a usar la herramienta keepass2johh para extraer el hash.

![image](https://github.com/user-attachments/assets/826765d9-539f-4e54-bff3-9fb132db65b1)

Y ahora con john sacaremos credenciales "penguin:password1"

Nos conectamos por keepass con las credenciales obtenidas, y vemos esto: 

![image](https://github.com/user-attachments/assets/a044131e-1fd6-43e5-95f0-f771123c2c22)

Nos conectamos al servicio ssh con las credenciales obtenidas "penguin:pinguinomaravilloso123".

![image](https://github.com/user-attachments/assets/9bacc5ec-49df-42d1-b5a6-6cd101777fa5)

En el directorio home tenemos estos dos archivos, y sus permisos nos permiten editar los archivos.

![image](https://github.com/user-attachments/assets/93a7304d-3394-4368-9726-c00b862f9459)

Añadimos esto al archivo: 

![image](https://github.com/user-attachments/assets/32098fc6-4dc3-417d-812c-81a03d3dee96)

Y si hacemos "bash -p", ya somos root.

![image](https://github.com/user-attachments/assets/10f6d5ba-732f-4727-921e-bc360b10e7d0)

