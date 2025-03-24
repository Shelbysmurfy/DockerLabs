# RESOLUCIÓN DE LA MÁQUINA SKULLNET

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/86ff93ae-2452-4c37-b49a-5d8eaf92cb76)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/a8b626e6-a61f-4889-8cd3-ed2e4427b6c0)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/51353bce-4c02-45c4-a0fa-458ab3cf7a56)

Vamos a añadir el dominio que se nos menciona en el /etc/hosts

![image](https://github.com/user-attachments/assets/9cdd5ae7-f0d3-4806-8c84-41d5db855611)

Abrimos la web pero no podemos hacer nada.

![image](https://github.com/user-attachments/assets/d3cf2584-ea3c-41f2-b229-d19372221e82)

Vamos a hacer un dirsearch.

![image](https://github.com/user-attachments/assets/8842238e-35bc-4082-b640-72e01d7d1cf0)

Sabiendo que estamos tratando con git vamos a traernos todo lo que tenemos a nuestra máquina con wget.

![image](https://github.com/user-attachments/assets/0bbb8246-8ba9-46df-b0ce-b8666e7b7649)

![image](https://github.com/user-attachments/assets/ae1b081e-e61b-40d8-9b47-5641364e38df)

![image](https://github.com/user-attachments/assets/d1e64013-9429-4f43-bcfe-ecabeb9c166d)

Si hacemos un ls -la, vemos esto: 

![image](https://github.com/user-attachments/assets/440b7d1e-b82b-4825-aa22-70a03a6a6b70)

Sabiendo que tenemos un .git, podemos ejecutar comandos de git para así poder manipular este repositorio.

![image](https://github.com/user-attachments/assets/de279b43-2abc-4464-86fb-4e16832db9e1)
![image](https://github.com/user-attachments/assets/84b9b706-f7f4-43f2-91c4-59cd7281b2af)

Hacemos un git show de los dos para saber la información que tiene y vemos que el segundo es el que nos interessa.

Así que vamos a hacer un "git reset" de este y luego un "git checkout" para poder tener los archivos que nos muestra.

![image](https://github.com/user-attachments/assets/95e819d2-4654-48b4-ab22-ec636789aaf3)

Miramos que contiene el archivo.txt y vemos unas posibles credenciales "skulloperator:+%7nj^g!DQxp]a>c4v&0".

![image](https://github.com/user-attachments/assets/9015f4dc-1a36-4b09-8469-75c0b8ec6682)

En este archivo nos habla de otro archivo que también se nos ha dado, refiriéndose al network.pcap

Sabiendo que tiene la extensión .pcap, vamos a abrirlo con wireshark.

![image](https://github.com/user-attachments/assets/4d86ab31-9549-49dd-b422-c39f1421d5ef)

Al abrirlo, vemos que hace una conexión ssh cuando el puerto no lo hemos visto abierto y también, que lanza 3 SYN’s a diferentes puertos, por lo que nos da una idea de que puede ser un port knocking.

Ejecutamos el port knocking y comprobamos que el puerto 22 se ha abierto correctamente.

![image](https://github.com/user-attachments/assets/0bdb6d2c-1a99-447b-8685-9ec6dc335bdd)

![image](https://github.com/user-attachments/assets/ea5f27d6-ed2b-48fb-b45e-755c39df1346)

Seguidamente nos conectamos al servicio ssh con las credenciales obtenidas anteriormente.

![image](https://github.com/user-attachments/assets/d9657ddb-f04d-4fb7-9497-edcccc18f810)

Hacemos ls y vemos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/d298b0ee-0f92-4a68-9447-e250b4c60859)

Revisamos los procesos que se han ejecutado con "ps -faux".

![image](https://github.com/user-attachments/assets/a75c5b89-a8f5-4f24-aae4-732982118de3)

Vamos a mirar el archivo.py

![image](https://github.com/user-attachments/assets/957f6e3b-639c-4c85-b02b-d15203015dc9)
![image](https://github.com/user-attachments/assets/ebdd229b-0f0a-4dbf-b6d6-e3162541d0cc)

Encontramos una clave cifrada en base64, vamos a descifrarla "we_are_bones_513546516486484".

![image](https://github.com/user-attachments/assets/1f5492ba-0f06-4cc5-9c6b-ebe4f4fdbfab)

Y ahora vamos a hacer uso de curl para ejecutar el comando "whoami", junto al parámetro "exec", que se nos menciona.

También tendremos que especificar la clave de autorización, junto a la palabra "Basic".

![image](https://github.com/user-attachments/assets/a2a185e2-2d80-4632-b4cc-ee589a831c7a)

Solo nos deja ejecutar estos dos comandos, así que tendremos que buscar otra forma de ejecutar comandos.

![image](https://github.com/user-attachments/assets/66d921cf-f639-48f2-8d1f-df1dd0a5e6e0)

Probamos a ejecutar otro comando después del whoami, añadiéndole un punto i coma, pero no funciona.

![image](https://github.com/user-attachments/assets/4eb641fd-6ce4-47ca-a81a-de221ea1695b)

Pero si url encodeamos esto si vemos resultado.

![image](https://github.com/user-attachments/assets/395e70d1-410a-4899-b218-f950d3aa15fe)

![image](https://github.com/user-attachments/assets/de27eb93-bb9e-4b9b-87fe-b2132087d9d5)

Vamos a ejecutar el comando "chmod u+s /bin/bash", para poder escalar privilegios, para ello primero tendremos que url encodearlo.

![image](https://github.com/user-attachments/assets/5ce3f615-e8bd-4768-adab-00b0c0e69481)

Lo ejecutamos y si usamos el comando "bash -p", nos convertimos en root.

![image](https://github.com/user-attachments/assets/043f5e64-3268-413f-9fac-0ffe04789327)

Hacemos ls y vemos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/1ec177be-32b2-4601-b57e-fd149f00b5bd)






