# RESOLUCIÓN DE LA MÁQUINA MASTER

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/9698a1f1-68c8-492f-83ee-004441992cd7)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/248f58b8-dcd7-44ae-aa40-1ff833500aca)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/fc0bdac1-7d1b-41a3-bec0-608d9ce3f22c)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/223b8b43-ac3e-482a-b44a-404ded472e23)

Viendo que tenemos wordpress, vamos a hacer uso de la herramienta wpscan en busca de posibles, versiones, plugins y usuarios.

![image](https://github.com/user-attachments/assets/f91862e9-8dbb-4555-9327-f8ec19135a74)

![image](https://github.com/user-attachments/assets/5e052c72-7bf9-42b1-8449-5fab6f7da537)

Encontramos el usuario Mario, buscamos posibles contraseñas para este con wpscan pero no encontramos nada.

Hacemos uso de la herramienta nuclei en busca de algun vulnerabilidad y emcontramos esta: 

![image](https://github.com/user-attachments/assets/ac2980d7-e083-48ac-b87a-f927cd6a6b30)

Buscamos el CVE de esta vulnerabilidad y luego buscamos un github que explique como explotarlo.

![image](https://github.com/user-attachments/assets/9a50b869-d1d0-4731-bb82-4647d1f3c636)

Github: https://github.com/diego-tella/CVE-2024-27956-RCE

![image](https://github.com/user-attachments/assets/9ddf6afc-9ffd-485c-9872-94478716b9a2)

Ejecutamos los tres pasos que nos indica y conseguimos unas credenciales "eviladmin:admin"

![image](https://github.com/user-attachments/assets/aecc1f0a-9b7f-48a2-b224-886960f3f96b)

Nos conectamos por el login de wordpress con estas credenciales.

![image](https://github.com/user-attachments/assets/19b4ea16-374b-4417-beaf-f7460efd5ea2)

Nos vamos a el apartado de plugins y descargamos el WP File Manager.

![image](https://github.com/user-attachments/assets/74230d05-1924-4846-b33e-6f89cf0a54dd)

Subimos un archivo malicioso.

![image](https://github.com/user-attachments/assets/45ca0737-da6d-4292-aa75-ec9c3ccc411f)

Nos vamos a la ruta donde lo hemos subido.

![image](https://github.com/user-attachments/assets/d59bdcd0-1570-4690-8b3b-3c4018fc77e3)

Entramos en el y vemos que podemos ejecutar comandos.

![image](https://github.com/user-attachments/assets/35358891-e48b-44e6-a470-2cc80015080b)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/bec15266-7bc2-4d99-9b28-b9384fe8d9df)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/c0db314f-c545-4b03-a441-ddc762428381)

Nos convertimos en pylon.

![image](https://github.com/user-attachments/assets/9c9bbe12-9066-4812-8d38-53e03fe5caf5)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/6f0d5752-53db-4330-9c98-1b67a128aefd)

Si nos vamos a /home/pylon, encontramos este archivo: 

![image](https://github.com/user-attachments/assets/57ce390b-7e54-487e-b7da-c4a015f2670e)

Hemos visto que para escalar privilegios nos enseña que en el usuario mario hay también un archivo.sh y cuando lo ejecutamos nos pide un número.

Vamos a esta web: https://exploit-notes.hdks.org/exploit/linux/privilege-escalation/bash-eq-privilege-escalation/

![image](https://github.com/user-attachments/assets/0ef0ff04-13f8-4b43-9e82-cab2127a307e)

De esta manera escalamos privilegios y ya somos el usuario mario.

![image](https://github.com/user-attachments/assets/ab724587-253a-4462-a746-605daa28041c)

hacemos sudo -l y vvolvemos a ver lo mismo pero ahora el archivo que tenia pylon.

![image](https://github.com/user-attachments/assets/525f0293-b5d4-49d8-9379-ec2c1e221dfc)

Así que hacemos lo mismo que antes pero poniendo como usuario el root, y de esta manera escalamos de privilegios.

![image](https://github.com/user-attachments/assets/9378ec99-770c-4c41-a694-aa644e1ba440)
