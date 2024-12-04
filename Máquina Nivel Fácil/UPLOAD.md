# RESOLUCIÓN DE LA MÁQUINA UPLOAD

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/68fd4628-211c-4255-87b4-5b585d1cc231)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/03de52d5-6bbe-423e-b5ba-412b1f7dc67c)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/87e0d1a7-5d51-4a6f-bdfb-2c4b43ff32ed)

Abrimos la web y nos encontramos con una subida de archivos.

![image](https://github.com/user-attachments/assets/e6f2ac47-0163-44e5-bdf6-6241611fbfa6)

Subimos un archivo php malicioso.

![image](https://github.com/user-attachments/assets/872cb696-50aa-4b89-9cf2-9a15bff03ca6)

Nos vamos al directorio /uploads y lo abrimos.

![image](https://github.com/user-attachments/assets/9afe4436-c9b3-442b-9845-9499842d52ba)

Funciona correctamente y nos deja inyectar código.

![image](https://github.com/user-attachments/assets/0a9ef241-42c9-49be-ac79-b253727570ba)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/7ab782f7-99d7-4f06-899c-8cdf88b37460)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/ca707a92-7302-4695-a9c0-e6f54eb53359)

Y ya somos root.

![image](https://github.com/user-attachments/assets/cace9c57-b64b-4ce4-8824-d64f453019c2)

