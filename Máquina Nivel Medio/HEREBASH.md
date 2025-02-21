# RESOLUCIÓN DE LA MÁQUINA HEREBASH

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/37c1b14a-8a4b-4dc2-b05a-ae1608d1ac2f)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/cabe2f11-c94c-4b10-b9ed-c57f63262509)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/2e8e1ebe-0ebf-4cdf-9e78-4ff9b77dd295)

Abrimos la web.

![image](https://github.com/user-attachments/assets/ceb04283-542c-4af8-8505-640feb34903a)

Encontramos un link dentro de la web "ANOTHER PAGE", que nos lleva a otra página.

![image](https://github.com/user-attachments/assets/4c108bc2-405b-4c2a-8ceb-9e3fb03e6f21)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/e3f8035d-a650-431a-8342-8eeb75f9f0cf)

En el directorio /spongebob, encontramos una imagen, la descragamos.

![image](https://github.com/user-attachments/assets/68a5d5b2-efea-4993-878e-5de68ff00200)

Usamos la herramienta steghide para ver si sacamos algo de la imagen, y después de probar varias passpharse, con "spongebob", nos funciona.

![image](https://github.com/user-attachments/assets/039a548d-2670-41f0-a9f0-fb2ac07da6bd)

Para romper este archivo usaremos zip2john para extraer el hash y luego usaremos john para obtener el password.

![image](https://github.com/user-attachments/assets/a57557fc-2bfd-4be6-bd40-e1aec0c6ef5f)

Descomprimimos el archivo con la contraseña que hemos conseguido y vemos un nuevo archivo .txt

![image](https://github.com/user-attachments/assets/f9b21c7e-dd88-4744-955b-4209860d02a6)

El archivo contiene esto: 

![image](https://github.com/user-attachments/assets/325e405f-13a3-4d2e-9e6d-1655c908264e)

Hacemos hydra y encontramos estas credenciales: 

![image](https://github.com/user-attachments/assets/1670c6bd-df48-4709-b8ec-032c56044550)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/2d02a9c5-234c-487e-ac77-79fc40077fb5)

Si nos vamos a /home/rosa, encontramos un directorio bastante raro "-", lo abrimos.

![image](https://github.com/user-attachments/assets/4f59ae79-638f-45d5-b2ba-a213bf05306d)

Y dentro de cada uno de estos hay esto: 

![image](https://github.com/user-attachments/assets/78350561-4b04-4368-9e67-280e7288d6e5)

Cada archivo contiene unas credenciales, pero los que yo he visto todos son así: 

![image](https://github.com/user-attachments/assets/d30ad79f-e6aa-438c-8c84-94f947ba1d2b)

Así que vamos a ejecutar un comando find, que busque en todos los archivos del directorio ./-, concatene sus contenidos y muestra solo las líneas que no terminan en x.

![image](https://github.com/user-attachments/assets/8367a520-60dd-4661-950c-8f61421f48c0)

Nos conectamos como pedro.

![image](https://github.com/user-attachments/assets/a23dc636-beeb-4cd2-9cb6-12a67542104e)

Como no encontramos nada, vamos a hacer uso de find para buscar posibles archivos en el sistema que contengan su nombre, ya que es el único usuario que no hemos conseguido su contraseña, y puede ser la manera de escalar privilegios.

![image](https://github.com/user-attachments/assets/58bcab38-16e4-4acc-b044-28aba1589423)

Encontramos la password de el usuario juan.

![image](https://github.com/user-attachments/assets/8f83f84f-4ba2-4df5-a140-ea8a505ba797)

Nos conectamos como juan.

![image](https://github.com/user-attachments/assets/63c3520c-8573-4044-a952-85018b7b1f10)

Miramos los directorios y archivos ocultos dentro del directorio juan y vemos esto: 

![image](https://github.com/user-attachments/assets/485b9582-08ef-4407-a9fe-cb520258ad85)

Ejecutamos el comando pass y nos devuelve la contraseña del posible usuario root.

![image](https://github.com/user-attachments/assets/cbab72ca-e62f-4d34-9141-1dde21d31553)

Y ya somos root.

![image](https://github.com/user-attachments/assets/e0e6a078-e238-4954-99da-b7d54d976b45)

