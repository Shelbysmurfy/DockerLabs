# RESOLUCIÓN DE LA MÁQUINA STACK 

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/975d884a-333a-4cf9-bc38-d61f3f983095)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/b4b323fb-f3c2-407e-859b-4afd51843969)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/0c0f6c25-d0b6-4499-9518-47b5ba1cc3ac)

Abrimos la web, y cuando la inspeccionamos vemos esto: 

![image](https://github.com/user-attachments/assets/2c6984c2-d5a5-4330-b1de-823e24796b88)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/3e1c98db-f72a-4539-8d58-ee627297c97f)

Nos metemos en el /note.txt

![image](https://github.com/user-attachments/assets/a7bd893e-31dd-4b0b-8ac8-d70590ff0347)

Después de hacer varios intentos con wfuzz en busca del parámetro para poder hacer un LFI en busca de el /etc/passwd, encontramos el "file".

![image](https://github.com/user-attachments/assets/eddf0b60-bac8-403d-879a-0b371d90a939)

Y vemos el usuario del que nos hablaba antes, el bob.

![image](https://github.com/user-attachments/assets/dffda859-c128-4be2-af1b-f7a8287bfa48)

Encontramos la password que nos decia antes, que estaba en el directorio /usr/share/bob/password.txt

![image](https://github.com/user-attachments/assets/32c09052-83a7-447a-86d5-458e56f378e0)

Nos conectamos al servicio ssh con las credeenciales obtenidas "bob:llv6ox3lx300"

![image](https://github.com/user-attachments/assets/00a3e52c-a5fd-4a48-aad1-88a7654e0a63)

Buscamos los permisos SUID y vemos esto: 

![image](https://github.com/user-attachments/assets/9c326aa8-04a3-4abc-930e-c84227351019)

Vamos al archivo que nos menciona que está en el directorio /opt y vemos que tiene permisos de root.

![image](https://github.com/user-attachments/assets/bb5f8360-dfb3-4644-8331-5d7e25285083)

Si intentamos ejecutarlo nos pide una contraseña que no sabemos.

![image](https://github.com/user-attachments/assets/7d230221-9164-4e99-ad50-e535d56c377f)

Vamos a intentar si es vulenrable a Buffer Overflow.

![image](https://github.com/user-attachments/assets/61993e34-5a4f-41d8-a75b-78f65d97d234)

Ahora vamos a pasarlo a nuetra máquina.

![image](https://github.com/user-attachments/assets/e9370710-dfba-45b0-ba50-f6d6b6dbd0f9)

![image](https://github.com/user-attachments/assets/f6e56303-342f-4897-90d3-bba499c9212d)

Utilizamos la herramienta gdb para el archivo command_exec

![image](https://github.com/user-attachments/assets/3b4f1e84-b9eb-44f4-80e9-ead6aa534e2d)

Ahora vamos a usar la herramienta de metasploit para crear un pattern y un offset.

![image](https://github.com/user-attachments/assets/a20f844e-f048-43f1-b2c6-16f583be1086)

Y seguidamente runearemos el gdb y introduciremos como contraseña el pattern creado.

![image](https://github.com/user-attachments/assets/4cdaebc5-b5d1-4bee-b742-4b3419e5e21c)

ME DEBERIA MOSTRAR ESTO: 

![image](https://github.com/user-attachments/assets/c9ad6e26-0b7c-4c95-8bac-e9f24038594c)

Entonces para determinar el desplazamiento exacto (offset) donde ocurre la sobrescritura, usariamos pattern_offset.rb.

![image](https://github.com/user-attachments/assets/04f2439f-aa6f-434c-8d7c-0f65dcf38d68)

Yo con esto sabria que el offset es de 88 bytes.

![image](https://github.com/user-attachments/assets/76437039-d158-4fa4-8f56-9f0b7a91dc3c)

Pero para ser mas certeros y encontrar el offset real exacto, vamos a ejecutar lo siguiente.

Cambiando el valor de las A, hasta que todo sea 42, que hace referencia a la letra B.

![image](https://github.com/user-attachments/assets/82176ffb-e40a-45ed-9893-7129f648f8b1)

Ahora crearíamos un archivo .py, para escalar privilegios.

![image](https://github.com/user-attachments/assets/79d8332f-95df-4291-a818-bca2280c775b)

De esta manera quitaríamos la x, de el root, y escalaríamos privilegios.

![image](https://github.com/user-attachments/assets/bbb638b2-b8a7-4e3f-89be-29e01b79ff5a)



