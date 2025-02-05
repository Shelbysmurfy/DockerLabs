# RESOLUCIÓN DE LA MÁQUINA SWISS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/2a29d063-2a82-4069-bfc6-0f85469501b8)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6c573528-43c3-45f0-961a-896f6f130224)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3d0a5789-ef22-4ac2-9b39-6cdfdd2fb0c8)

Abrimos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/94777a4f-c82a-4c90-b050-8fbb136b68e3)

Vamos a usar la herramienta Nuclei detectar vulnerabilidades de seguridad y encontramos esto: 

![image](https://github.com/user-attachments/assets/7cc8f06c-b1ed-479f-8ba8-5cc5cd05ccfc)

![image](https://github.com/user-attachments/assets/f5e261dd-deea-45d3-9b95-51d66d91afcf)

Lo usamos y vemos dos posibles usuarios: darks y cristal

![image](https://github.com/user-attachments/assets/3764ec6d-31aa-45da-9354-3078c771cf08)

Usamos un wrapper de github: php://filter/convert.base64-encode/resource=index.php

![image](https://github.com/user-attachments/assets/8ed3e053-8881-4f5d-9a65-ba78f829f280)

Como el anterior comando lo ha leido correctamente, ahora usaremos el exploit (php filter chain generator) que nos permite ejecutar comandos.

![image](https://github.com/user-attachments/assets/1848d00a-5346-4fca-b346-62b32d53ab6a)

![image](https://github.com/user-attachments/assets/e086256e-eb72-4afe-9f9f-ceddc9286dae)

Copiamos desde donde pone php hasta el final y lo copiamos en nuestra url, después del comando que indicamos que queremos ejecutar.

http://IP/index.php?cmd=id&file="php filter chain generator"

![image](https://github.com/user-attachments/assets/0f515745-3335-45a2-a047-b5c3c58d9e8c)

Intentamos hacer una reverse shell para conectarnos desde nuestra máquina o a través del docker pero no nos deja.

![image](https://github.com/user-attachments/assets/0bae58d4-d0ae-4a53-a8b4-12de11645da1)

![image](https://github.com/user-attachments/assets/6be924b5-89ac-41ce-bd52-104eb3747ab0)

Miraremos los procesos que se ejecutan en la máquina víctima con ps aux.

![image](https://github.com/user-attachments/assets/34254f2f-833b-42ba-8423-655abd29bafe)

Hemos visto que no podemos mandarnos una shell a 172.17.0.1, la vamos a cambiar por una que no nos aparezca cuando ejecutamos el ps aux.

![image](https://github.com/user-attachments/assets/744b3ce9-b170-4b74-9c52-6568719aa660)

Hacemos una reverse shell y ahora si nos deja.

![image](https://github.com/user-attachments/assets/1a692e30-fd63-4182-81cf-dcd0674153b5)

Una vez conectados hacemos ls y vemos el archivo credentials.txt, hacemos un strings y encontramos unas credenciales (darks/_dkvndsqwcdfef34445)

![image](https://github.com/user-attachments/assets/8dc6d054-cccd-4c27-b723-3192afbe2f85)

Nos conectamos al servico ssh con las credenciales obtenidas y encontramos este mensaje: 

![image](https://github.com/user-attachments/assets/0ed2a261-c0fa-4fbc-8446-c8c492eb17bd)

Nos encontramos con un archivo, que al parecer nos dice que ha habido un error en el socket, ya que los datos se envian a otra IP.

![image](https://github.com/user-attachments/assets/2f3409b3-7535-42fc-a753-1cef08f49103)

![image](https://github.com/user-attachments/assets/93745e95-cb9d-43c0-9a49-96f676e2f1a7)

La volvemos a cambiar.

![image](https://github.com/user-attachments/assets/7a028f0b-6f8e-47c1-88d4-0d026bc90d34)

Ejecutamos el sendinv2, que es el archivo donde hemos visto que habia que cambiar la IP, mientras tenemos el wireshark encendido y vemos que la información se envia al puerto 7777.

![image](https://github.com/user-attachments/assets/8a947778-2628-4f6d-aa87-791d9a1eb3e8)

Y poniéndonos en escucha por el puerto que hemos visto que llega la info que buscamos recibimos esto: 

![image](https://github.com/user-attachments/assets/c9bf6fc3-418c-403d-81b3-e786b8a5b6b1)

Lo decodeamos dos veces con cyberchef y vemos esta información: 

![image](https://github.com/user-attachments/assets/28a1a127-5086-459a-85eb-b544c8284fbe)

![image](https://github.com/user-attachments/assets/8d5178ad-dfb9-4057-88c2-d39fae10110e)

Nos conectamos al servicio ssh con las credenciales obtenidas. 

![image](https://github.com/user-attachments/assets/4d266374-19c2-4d08-abfa-da23a69d3a9b)

Vamos al directorio home y vemos 3 archivos.

![image](https://github.com/user-attachments/assets/54bc5c4d-7997-47db-84d4-e574f7254a6c)

Vemos que uno de ellos tiene permisos "editor", de lectura y escritura.

![image](https://github.com/user-attachments/assets/700bac97-6e90-4c57-9b40-9452e2a7f7f7)

Nos metemos en el systm.c y vemos esto: 

![image](https://github.com/user-attachments/assets/43ed9697-37fa-471a-aca2-5149c1371184)

Nos metemos al archivo registros.log, para ver los propios registros, y vemos esto: 

![image](https://github.com/user-attachments/assets/a9052d9c-453e-461b-bc2b-ea18961a854c)

Luego vamos al último archivo y vemos que el archivo que podemos editar se ejecuta cada 15s.

![image](https://github.com/user-attachments/assets/885bdd71-c706-437e-bd88-81109f6d9259)

Así que nos vamos a meter en el systm.c, que es el archivo que podemos editar y así poder ejecutar algo que nos permita escalar privilegios.

![image](https://github.com/user-attachments/assets/36ae165c-17c4-41c3-a210-6d45881da861)

Esperamos 15 s, y al hacer sudo -l vemos esto: 

![image](https://github.com/user-attachments/assets/307122ef-a4b8-4a80-863f-6dcaf7b4e072)

Por tanto, ahora si hacemos un sudo su, nos permite entrar como root sin pedirnos ninguna credencial.

![image](https://github.com/user-attachments/assets/c677d0dd-6f56-4115-b43c-308d4c087388)

