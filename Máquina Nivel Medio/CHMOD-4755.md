# RESOLUCIÓN DE LA MÁQUINA CHMOD-4755

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/f3aa9c3d-d2b1-4f64-af12-7913f1de458b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/eac1d6c5-ac9d-48b6-8675-e3ecf60f1cf4)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/5f7e99b9-4c63-4062-a0dd-9a817c219e40)

Hacemos uso de la herramienta enum4linux, en busca de posibles usuarios, grupos, resursos compartidos...

![image](https://github.com/user-attachments/assets/b8a82bf9-68a1-4031-8f25-f7b0eac52cd2)

![image](https://github.com/user-attachments/assets/987b0fd1-2686-4431-bc73-67ece4c3df16)

![image](https://github.com/user-attachments/assets/891e9e9a-3304-498e-9185-5abb8076e51f)

Ahora haremos uso de la herramienta netexec en busca de las contraseñas para los dos usuarios que hemos encontrado.

![image](https://github.com/user-attachments/assets/8a065701-e88b-48e5-8996-adaf79fbd8ae)

Utilizamos nmap con las credenciales que hemos encontrado en busca de los recursos compartidos disponibles y si tenemos permsisos para ellos.

![image](https://github.com/user-attachments/assets/9bec7ff8-dbaf-4452-96ea-8021a28834e3)

Nos conectamos al recurso share_secret_only con las credenciales que tenemos.

![image](https://github.com/user-attachments/assets/bcacdec2-709d-4d1e-8faf-10c632fef52a)

![image](https://github.com/user-attachments/assets/db6b5730-d602-414a-965d-0b43db399389)

Como nos dice que leamos mejor, que es la única pista que tenemos, vamos a intentar varias combinaciones de credenciales, con lo que tenemos para conectarnos al servicio ssh.

Nos conectamos al servicio ssh con las credenciales (rabol:share_secret_only)

![image](https://github.com/user-attachments/assets/eed96705-3bde-42d0-9eef-c79b1b1ad590)

Entramos y vemos que no podemos ejecutar casi ningún comando, estamos ante una restricted bash.

![image](https://github.com/user-attachments/assets/ab9050a9-b6b2-4ecf-a9e4-9e3502b96527)

Si listamos el contenido de el directorio bin, vemos ls y python3, que al parecer son los únicos dos comandos que podré ejecutar.

![image](https://github.com/user-attachments/assets/49e47be1-007f-450e-b8e3-4f4cd16d5301)

Invocamos una shell normal gracias a python3.

![image](https://github.com/user-attachments/assets/b3ca7934-4424-4097-8a40-6b6d404607b2)

Pero si intentamos ejecutar algun comando veremos que no podemos, así que vamos a establecer la variable de entorno PATH a /bin, para así poder ejecutar comandos con normalidad.

![image](https://github.com/user-attachments/assets/39e8a442-dbae-4455-be71-d8f7319dd080)

Y vemos la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/0fbe2b47-4019-41e7-a19c-34b247ebc195)

Miramos los permisos SUID, y encontramos el curl disponible.

![image](https://github.com/user-attachments/assets/48a0509c-5ae6-4a63-ac37-c2b293bf70a8)

Me creo un archivo en mi máquina local, de el /etc/passwd de mi máquina víctima pero quitándole la x del root, para escalar privilegios.

![image](https://github.com/user-attachments/assets/0c4b18a8-fd6d-4aaf-866c-3e72707819e7)

Nos abrimos un servidor con python.

![image](https://github.com/user-attachments/assets/4ed97517-e63e-4f45-9d6a-213da36cea3f)

Y ejecutamos el comando que nos dice el GTFObins para convertir el archivo que hemos creado en nuestra máquina por el /etc/passwd

![image](https://github.com/user-attachments/assets/ee7df7cd-911b-4a51-a870-664eb0dddf91)

Miramos el /etc/passwd y se ha cambiado correctamente.

![image](https://github.com/user-attachments/assets/837d2c4f-ad03-4c40-841c-e95724844c41)

Y ya somos root.

![image](https://github.com/user-attachments/assets/5dea2e1f-41f9-438a-9fdb-96ae927c0bfc)

Y conseguimos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/d436a1fa-5a1a-462c-a11b-5bbf96c1a047)

