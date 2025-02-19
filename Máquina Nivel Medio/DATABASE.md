# RESOLUCIÓN DE LA MÁQUINA DATABASE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/b72abc36-13eb-42ff-ae17-3f106c9f3679)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/c302d704-899f-4bd9-995b-b6765fdee8aa)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/85931099-f5e6-4d15-83e3-b8e1430bdcc2)

Entramos en la web y vemos un login.

![image](https://github.com/user-attachments/assets/84bf743f-5194-402f-9f5e-218498523f9e)

Ponemos credenciales básicas y me devuelve "Wrong Credentials", en la pantalla.

![image](https://github.com/user-attachments/assets/3a5f2393-8ff6-4b52-a319-8db8587bdf31)

Vamos a hacer SQLI para poder ganar acceso, con un comando básico (' or 1=1; --)

Ganamos acceso, pero solo vemos este mensaje: 

![image](https://github.com/user-attachments/assets/e256cf03-cc4b-48ab-934a-0509c9e790e2)

Vamos a hacer uso de la herramienta enum4linux, en busca de recursos compartidos, usuarios...

![image](https://github.com/user-attachments/assets/f9ab27f0-3842-4c3f-a945-a8feb5e3c65a)

![image](https://github.com/user-attachments/assets/6e8c32fd-cb23-443c-8774-36860b3a039a)

Usamos netexec para buscar posibles contraseñas para los usuarios que tenemos, tanto el servicio smb como el ssh, y encontramos estas credenciales.

![image](https://github.com/user-attachments/assets/40ecc752-3e26-455e-8436-91221fb1ed0d)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/5249b9a7-fe0c-4ea0-95d4-a8490e8c4fe1)

Hacemos sudo -l y vemos esto, pero no conseguimos escalar privilegios.

![image](https://github.com/user-attachments/assets/9a17feba-00ef-43cc-a692-476a0d67344f)

Miramos los permisos SUID.

![image](https://github.com/user-attachments/assets/a09ba4e3-9bfa-477e-80b5-a853a27e0a4d)

Y ya somos root.

![image](https://github.com/user-attachments/assets/25322cc1-98f1-47e8-b1ce-9a002508bde5)

