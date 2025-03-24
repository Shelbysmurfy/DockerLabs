# RESOLUCIÓN DE LA MÁQUINA DARKWEB

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/0271fd51-e2e3-4dcf-9d3d-9a94cbbf3c88)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/03817187-5db9-4547-9cad-4b1e88307b05)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3730c37f-4358-415c-9a07-f275315f1f99)

Usamos enum4linux para buscar recursos compartidos disponibles, usuarios...

![image](https://github.com/user-attachments/assets/d6c0d336-1871-4d93-8984-9de7fa52a31f)

![image](https://github.com/user-attachments/assets/30a514e7-ed31-4a1d-a389-5af8c75b1573)

![image](https://github.com/user-attachments/assets/10f2d110-9d47-401f-8c5b-447a0311f866)

Hacemos un smbclient sin indicar el usuario para ver si hay recursos compartidos.

![image](https://github.com/user-attachments/assets/4d5a180e-5df1-4755-aa97-d7e300c5935e)

Nos metemos en el darkshare y vemos esto: 

![image](https://github.com/user-attachments/assets/a06cf549-bd38-48a2-b790-50fe8f6fb533)

El archivo ilegal contiene un posible código cifrado.

![image](https://github.com/user-attachments/assets/0bfcece8-f9da-4dda-9a09-421bd9164a4c)

Vamos a usar el decoder de cifrado de césar para saber que dice.

![image](https://github.com/user-attachments/assets/a7850f37-e9fc-4988-9df0-ef95749833ba)

Buscamos información sobre las direcciones .onion

![image](https://github.com/user-attachments/assets/9e1e23a2-747c-478a-81f8-041e38719448)

Abrimos la url que tenemos en el navegador tor.

![image](https://github.com/user-attachments/assets/849dcae1-eb67-478e-8d65-d3b11bec6ad3)

En el código fuente vemos un posible subdominio.

![image](https://github.com/user-attachments/assets/e27b8d99-5265-41e1-8ca3-8a92c90bf548)

En el vemos esto: 

![image](https://github.com/user-attachments/assets/1d9e84ce-5c5f-4f53-a321-d793ab998045)

Abrimos el código fuente y volvemos a ver algunos posibles subdominios.

![image](https://github.com/user-attachments/assets/94950044-9dd1-4cd8-98e4-0f0fba9a3708)

En el "redroom.html" vemos unas credenciales, que nos cuadra con el usuario que hemos encontrado antes al hacer enum4linux.

![image](https://github.com/user-attachments/assets/ea65cee3-ad45-49ba-b641-3ddc99be2f19)

Con estas credenciales no podemos hacer nada de momento, vamos a ver si encontramos algo mas.

Abrimos el "marketplace.html" y vemos una posible ruta de un archivo.txt

![image](https://github.com/user-attachments/assets/e376b746-bd2d-4900-b8e8-202d28cf97d9)

Lo introducimos en la url y vemos esta lista.

![image](https://github.com/user-attachments/assets/db61ed4f-43cd-49e4-9b03-0c8b3769e607)

Usamos la lista como posibles contraseñas del usuario dark y usamos hydra para encontrar credenciales válidas.

![image](https://github.com/user-attachments/assets/8dc9fa4d-d4de-4b7b-807d-b2db067c375c)

Nos conectamos al servicio ssh con las credenciales obtenidas "dark:oniondarkgood".

![image](https://github.com/user-attachments/assets/17c588b7-9777-439e-9ee7-12c313848bfc)

Hacemos ls y vemos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/742ce9e6-88c6-4737-93ae-2d0d0368f3f7)

Ahora hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/aa376176-4bd1-4165-8786-c9a5a32251a2)

Nos vamos al archivo hidden.p y vemos que no podemos editarlo, ya que tiene permisos de root.

![image](https://github.com/user-attachments/assets/5288313a-a967-4930-8a27-da9db1a8e3e3)

Pero en el vemos un path al archivo Update.sh, que contiene el comando whoami.

Vamos a eliminar este archivo y crear uno nuevo con permisos para poder escalar privilegios.

![image](https://github.com/user-attachments/assets/a57d4e4a-ce88-43e5-8b73-3f9788446107)

Ahora ejecutamos el permiso SUDO y si hacemos "bash -p" ya somos root.

![image](https://github.com/user-attachments/assets/4a0b30af-f86c-4432-8c4c-9aeb0d51459a)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/d14bf258-d5ea-46e1-b413-b318eb0ee7b6)

