# RESOLUCIÓN DE LA MÁQUINA JENKHACK

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/ca9d7cdd-debe-446f-a221-5cf091bc7c0a)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/652285bb-0fe0-42b7-a91a-099f6ca75c27)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/7077742f-3b7a-4f17-b192-27663308dce6)

En el código fuente del puerto 80 encontramos el dominio: jenkhack.hl, y unas posibles credenciales (jenkins-admin / cassandra).

![image](https://github.com/user-attachments/assets/7521cb64-543f-4b35-9814-20775e1c92d7)

Probamos en el puerto 8080 esas credenciales y obtenemos acceso.

![image](https://github.com/user-attachments/assets/94dab640-4986-4fb9-924e-c3dca25c5fe5)

![image](https://github.com/user-attachments/assets/bd79c5fe-cb24-41b8-abd5-688d40b8a776)

Información importante: https://cloud.hacktricks.xyz/es-cloud/pentesting-ci-cd/jenkins-security/jenkins-rce-with-groovy-script

Vamos a la url de jenkins y añadimos /script

Luego añadimos este código: 

![image](https://github.com/user-attachments/assets/7caa69cc-629e-44df-80be-c972cb01fa2b)

Nos ponemos en escucha desde nuestra terminal y ganamos acceso a la máquina.

![image](https://github.com/user-attachments/assets/c65376e8-fbf1-47b8-870b-9f5c976d83d0)

Encontramos información sobre el usuari jenkhack.

![image](https://github.com/user-attachments/assets/402cc7c9-d655-4116-8b0a-d2dcf8a143d9)

Nos vamos a cyberchef y lo decodeamos.

![image](https://github.com/user-attachments/assets/a4e365d3-a060-4bee-9591-1851fe1f7105)

Y ya somos el usuari jenkhack.

![image](https://github.com/user-attachments/assets/17fcb3d0-8203-40c5-b538-51a5a24ef9e0)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b4945794-e7ff-437d-a7ef-42cfd5e599e9)

Nos vamos al directorio /opt y vemos un archivo que es el que se ejecuta al hacer lo que sale en el sudo -l.

Por tanto vamos a modificar ese archivo.

![image](https://github.com/user-attachments/assets/289f9bcd-e06f-44e4-94d2-3d9d2ffd7fe8)

Una vez modificado le damos permisos de ejecución y conseguimos acceso como root.

![image](https://github.com/user-attachments/assets/8dc923ba-bb5d-4bd8-8562-9dfc78f58125)



