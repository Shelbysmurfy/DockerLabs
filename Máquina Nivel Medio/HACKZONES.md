# RESOLUCIÓN DE LA MÁQUINA HACKZONES

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/788a438c-acae-451a-8182-1f02934cea29)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/64747dff-451c-45f3-bbf8-ee7e87a97311)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3367b31f-d7ed-40ed-bc24-500c8f61bced)

Abrimos la web.

![image](https://github.com/user-attachments/assets/5a495bab-ef1a-46f8-946f-ad45a5ac235d)

En el /etc/hosts, ponemos el dominio que nos dan (hackzones.hl), lo abrimos y vemos un login.

![image](https://github.com/user-attachments/assets/2d49fef6-9fff-487a-98c6-f26ffe6f40e6)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/6a99c462-24e2-4e28-8966-e840b64e04c8)

Nos vamos al /dashboard.html y vemos el Panel de Admin.

![image](https://github.com/user-attachments/assets/26465d31-094c-4491-9303-2c39d35790d1)

Si clicamos donde la "foto de perfil", vemos que podemos subir archivos.

![image](https://github.com/user-attachments/assets/e68f5881-70a8-44e3-b1da-e00fc53cec88)

Subimos un archivo malicioso exitosamente.

![image](https://github.com/user-attachments/assets/a9768060-58a7-4b98-a051-eaec45bdde59)

Vamos al /uploads, vemos que se ha subido correctamente y comprobamos que podemos ejecutar comandos.

![image](https://github.com/user-attachments/assets/4dafaed6-5390-40ca-a94b-0d108cb0d054)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/b8f74408-d8c7-4908-a400-1f013a325a19)

Encontramos unas credenciales, que sirven para ganar acceso desde el login, pero que nos llevan al panel de login que ya tenemos acceso sin necesidad de estas.

![image](https://github.com/user-attachments/assets/3127d1f9-99c8-4d16-a33e-7950db354c07)

También encontramos un archivo llamado secret.sh

![image](https://github.com/user-attachments/assets/c6c5e5b5-243a-4b5d-a2ec-1c7bb35039f7)

Lo intentamos ejecutar pero nos dice que tenemos que ejecutarlo como root.

![image](https://github.com/user-attachments/assets/0e8d2773-f938-40a3-8a3a-2050a979a0e5)

Como podemos verlo, nos lo copiamos y lo pegamos en nuestra máquina, seguidamente lo ejecutamos como root y nos muestra esta credencial.

![image](https://github.com/user-attachments/assets/5ce8a787-1ef1-4aae-ac3b-880187df2ddc)

En nuestra máquina tenemos el usuario mrRobot, así que vemos a usar la contraseña para este usuario.

![image](https://github.com/user-attachments/assets/688a3f5a-02a5-429f-aa22-4bfa61c259eb)

Nos conectamos al servicio ssh con las credenciales obtenidas (mrrobot:Password@$$!123).

![image](https://github.com/user-attachments/assets/5ae3711a-ce03-4115-94ca-e874851f9721)

Y encontramos la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/8cd3d739-6fa0-46e5-8d28-437aad31bcf6)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/f6d22447-8605-4622-b038-bcbd13d74f4f)

En el directorio /opt hay un archivo que no podemos abrir, así que vamos a abrirlo gracias a esto.

Encontramos unas credenciales (root:rooteable)

![image](https://github.com/user-attachments/assets/d93707d5-cd7b-4c1b-800e-dc0ed14d3491)

Nos conectamos como usuario root.

![image](https://github.com/user-attachments/assets/440d5337-d6ec-4300-b26f-279602886e95)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/bc9ba36c-7bcb-438c-a3dc-a7940af611aa)
