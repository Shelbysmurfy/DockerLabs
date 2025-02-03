# RESOLUCIÓN DE LA MÁQUINA UNRECOVER

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/52d84acb-a8fd-4a45-b737-b77ea2ed31c7)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/376311a7-f651-4a52-acb0-7728258c6c1d)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/8acd3f21-2f70-4e18-b3cc-d26573b18465)

Abrimos la web y vemos un posible usuarios, capybara.

![image](https://github.com/user-attachments/assets/13a53c20-8b2d-4a33-a646-9dec7067d7a0)

Lo probamos con hydra para todos los servicios disponibles, y en mysql, nos devuelve una contraseña.

![image](https://github.com/user-attachments/assets/36bdbcdc-f87a-44a3-b53b-e4001c0833c6)

Nos conectamos al servico de mysql con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/12394dad-c67a-4b58-9608-2c6a3c02914d)

Encontramos unas credenciales (balulero/520d3142a140addb8be7d858a7e29e15)

![image](https://github.com/user-attachments/assets/08c7ba20-872b-4fdd-8926-73d3e7f5b587)

Con la herramienta hash-identifier vemos en que tipo de cifrado esta esta password.

![image](https://github.com/user-attachments/assets/961a8d59-a16d-414d-84ff-f3622c62e831)

Con CrackStation desciframos la contraseña.

![image](https://github.com/user-attachments/assets/e0dc53f4-8ab0-4f91-9fd0-922c036a0409)

Nos conectamos al servicio ftp con las credenciales obtenidas y vemos esto: 

![image](https://github.com/user-attachments/assets/f7c37bcb-7e3a-4d9d-a746-d1d9970c17a3)

Nos traemos el archivo a nuestra máquina y lo abrimos.

![image](https://github.com/user-attachments/assets/c09b19dc-6b5b-48e5-81c2-45bb14111b67)

Nos conectamos al servico ssh con las mismas credenciales con las que nos hemos conectado al servicio ftp.

![image](https://github.com/user-attachments/assets/d63922ab-57f4-4d03-94a1-ec99c91bdb31)

Nos conectamos como root con las credenciales que hemos visto en el archivo backup.pdf

![image](https://github.com/user-attachments/assets/535d388c-7e6c-40dd-936e-f716dfd9816c)






