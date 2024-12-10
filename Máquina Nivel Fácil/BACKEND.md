# RESOLUCIÓN DE LA MÁQUINA BACKEND

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/f189ca1d-c8c7-476a-9977-b0ef8d965ade)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/fa2989b6-1ee8-4737-9508-4eef22342385)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/06cbd08d-b0d1-49ab-b4ff-c2d7a1d3c052)

Abrimos la web.

![image](https://github.com/user-attachments/assets/f4f69b38-214a-46e2-b6da-e3a0b841a99d)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/7a7c2078-6890-498d-9301-3f9914a942a1)

Abrimos el login.html

![image](https://github.com/user-attachments/assets/1d5c8674-1db9-49b7-a28b-08dd38195473)

Hacemos sql-injection, en el login y nos muestra el siguiente mensaje.

![image](https://github.com/user-attachments/assets/bad20d24-e9d1-4e39-beac-10d01ba95156)

![image](https://github.com/user-attachments/assets/ed90132f-c5fd-48bc-9fa0-324e272ea3b0)

Procedemos a usar sqlmap para ver las bases de datos.

![image](https://github.com/user-attachments/assets/0b7eab94-b145-4165-8e86-03a2485f5457)

![image](https://github.com/user-attachments/assets/d899b7ec-4d22-42a0-bbb3-ed9944f4d76c)

Ahora usamos sqlmap para ver las tablas dentro de users.

![image](https://github.com/user-attachments/assets/439f72ae-e5cc-4a90-96e9-7fd5e0c336b8)

![image](https://github.com/user-attachments/assets/1823fef7-aa57-4f9f-a2e7-cfbc10de5a65)

Ahora lo usamos para ver las columnas dentro de la tabla usuarios.

![image](https://github.com/user-attachments/assets/5c1d892f-6221-4b98-9089-3f2585a35550)

![image](https://github.com/user-attachments/assets/4ae8c869-6f33-4191-9b3d-d5b06e335b72)

Finalmente lo usamos para ver el id, usuarios y contraseñas.

![image](https://github.com/user-attachments/assets/1e566b7b-188f-4e81-b0c4-309d77914c55)

![image](https://github.com/user-attachments/assets/4692072a-f772-4caa-98c1-43289cce26a8)

Nos vamos al login y vemos que los tres usuarios no hacen nada al loguearnos.

Así que intentamos conectarnos al servicio ssh, y el usuario pepe nos lo permite.

![image](https://github.com/user-attachments/assets/1f5c75bb-a5e2-47ab-9dcd-ab859d9bb7ec)

Hacemos búsqueda de permisos SUID y podemos observar que tenemos al binario grep y el ls.

![image](https://github.com/user-attachments/assets/41d5f762-cc85-4996-9440-6270800d9e0d)

Visionamos el contenido que hay en el directorio /root con ls.

![image](https://github.com/user-attachments/assets/e935c529-a910-480c-b288-499cae4ac02a)

Usamos grep para ver que hay dentro del archivo pass.hash

![image](https://github.com/user-attachments/assets/73520772-f52b-47c8-93b1-7decefd0101f)

Usamos crackstation para descifrar la posible contraseña que hemos obtenido.

![image](https://github.com/user-attachments/assets/c01ec6f6-9093-4f78-a7d1-76d4d100fe30)

Y ya somos root.

![image](https://github.com/user-attachments/assets/4318c9b1-d574-4d14-b97f-69db30ac7829)








