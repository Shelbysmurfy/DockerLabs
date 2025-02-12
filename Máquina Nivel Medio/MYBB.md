# RESOLUCIÓN DE LA MÁQUINA MYBB

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a77c163f-75b0-49a1-8a7e-e74b7bf460bc)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/bffb33fd-8263-4449-b60c-2da4e2cc6eee)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/5e3540e7-e207-48a9-8a3d-ee2a23240704)

Abrimos la web.

![image](https://github.com/user-attachments/assets/a8f91429-bf45-48bf-abad-f4e64db8e1a2)

Cambiamos el dominio y podemos meternos en el foro.

![image](https://github.com/user-attachments/assets/310e6f66-99dc-421c-8308-9c014425e3e5)

Hacemos fuerza bruta con gobuster, con el dominio que hemos encontrado. 

![image](https://github.com/user-attachments/assets/adda9914-4cea-4525-8cb6-836e2480f57d)

Como no encontramos nada vamos a ver la petición y seguidamente vamos a hacer un hydra con la información que tenemos.

![image](https://github.com/user-attachments/assets/fc35f46f-2853-4dfc-b697-10d32d85aa4e)

![image](https://github.com/user-attachments/assets/9ef0109f-11a7-4126-a1a0-e83aebf0a6c0)

Nos conseguimos loguear con las credenciales (admin:babygirl).

![image](https://github.com/user-attachments/assets/5f0c1419-5cae-467e-9027-1916a8db2764)

Vemos una posible versión que está desactualizada, y que por tanto puede tener vulnerabilidades.

![image](https://github.com/user-attachments/assets/91b52a96-7108-4edc-abd9-0d406c6ee9b4)

Buscamos por el CVE y encontramos este github "https://github.com/SorceryIE/CVE-2023-41362_MyBB_ACP_RCE"

![image](https://github.com/user-attachments/assets/28c67f7c-04ec-4449-a356-6b9222d92729)

Nos lo traemos a nuestra máquina y lo ejecutamos.

![image](https://github.com/user-attachments/assets/32f32111-8b64-47f0-8555-e38d897bd023)

Como podemos ejecutar comandos vamos a tirar una reverse shell.

![image](https://github.com/user-attachments/assets/19f6092f-968c-4a13-9ac7-0a10b1768e02)

Encontramos una posible clave cifrada del usuario alice.

![image](https://github.com/user-attachments/assets/c2599f6b-f1a2-4670-ac6b-5d9134904797)

Nos la traemos a nuestra máquina y la desciframos con john.

![image](https://github.com/user-attachments/assets/5c25e748-af5f-4183-8a52-dc9d5e046697)

Nos conectamos como usuario alice con las credenciales obtenidas (alice:tinkerbell)

![image](https://github.com/user-attachments/assets/6f9786b2-8839-4249-a858-cc623107bca2)

Hacemos sudo -l y vemos que el usuario alice tiene permisos para ejecutar cualquier script en ruby.

![image](https://github.com/user-attachments/assets/1a4ff6b6-cf11-42d2-9491-8ee7052da9bf)

Nos creamos un archivo ruby malicioso y le damos permisos de ejecución.

![image](https://github.com/user-attachments/assets/bf84c288-e29a-49d8-9d14-5960a2d74756)
![image](https://github.com/user-attachments/assets/51e652f6-4b01-4131-b19e-e91da23dcd9d)

Y ya somos root.

![image](https://github.com/user-attachments/assets/5cd1c423-23c5-4091-aab4-8e5c69ef4d56)








