# RESOLUCIÓN DE LA MÁQUINA DEVTOOLS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/28793624-17af-4d9b-a8f9-0741cfd48411)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/cb8b663b-c2ef-4cae-904b-45127b14f96a)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/df9a3149-119e-4be3-a1ca-b984ee8a90be)

Abrimos la web y nos salta esto: 

![image](https://github.com/user-attachments/assets/8b574ec1-3d87-4dbe-a154-bc89f407c56e)

Nos podemos saltar el prompt, marcando la casilla que indica que no queremos que vuelva a mostrarse.

Seguidamente miramos el código fuente y encontramos un archivo.js con unas posibles credenciales.

![image](https://github.com/user-attachments/assets/424b48ba-98cc-40b0-a4d3-32df2dda7258)

![image](https://github.com/user-attachments/assets/536ab69c-e795-49aa-a4ab-6bf6a4d22239)

Introduzco las credenciales y son correctas (chocolate:chocolate)

![image](https://github.com/user-attachments/assets/95f7b287-223e-45d7-9f80-a9ac8e214482)

Nos menciona una posible contraseña (baluleroh), así que vamos a hacer hydra en busca de el usuario de esta.

![image](https://github.com/user-attachments/assets/f7919ca4-12a8-4a8f-99a8-1ddb7d8c9a4f)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/f3be86cd-8cc8-4432-882c-4a174eaaed56)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/8936f05d-fc8d-4882-96b0-0060cbd3dde6)

Hay un archivo en el directorio home que nos da esta pista.

![image](https://github.com/user-attachments/assets/0a7661c3-ce43-4e82-8407-a75bbfc38b64)

Vamos a aprovechar las permisos SUDO para leer este archivo.

![image](https://github.com/user-attachments/assets/52e0baf6-63ba-4e54-961f-1879ab5aa099)

Y ya somos root.

![image](https://github.com/user-attachments/assets/912e27d2-cdd6-47ef-97bd-971cf37cee38)

