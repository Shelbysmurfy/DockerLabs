# RESOLUCIÓN DE LA MÁQUINA WALKINGCMS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a82e4dfe-ef93-474c-b15c-72077723ea98)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/ca2af160-4f95-4a3e-848d-16266360ce1e)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a59ed65b-92d3-4374-a3f5-f2db84ccd9c8)

Abrimos la web, y no hay nada.

![image](https://github.com/user-attachments/assets/a9f337b1-785c-4562-9c4e-a99ad8a1cad2)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/50e1bb58-be00-4085-9b25-808d68ca0dd0)

Hacemos otra vez gobuster pero con la ruta nueva.

![image](https://github.com/user-attachments/assets/e07d4b94-8668-49cd-b84e-6ffebdcad6f1)

Tenemos un login de wordpress.

![image](https://github.com/user-attachments/assets/83c34e26-1aa0-4c6f-a96a-8f90c222be27)

Haremos uso de la herramienta wpscan para buscar posibles usuarios y información extra de la ruta dada.

![image](https://github.com/user-attachments/assets/0d7cbb8e-9cf2-4646-ba7a-7536b4ff319b)

Encontramos el usuario Mario.

![image](https://github.com/user-attachments/assets/2ae879ef-e549-4253-982c-0077ecc7fe88)

Ahora hacemos un wpscan indicando que el usuario es Mario y en la contraseña ponemos el diccionario rockyou.

![image](https://github.com/user-attachments/assets/426a003c-4c28-4078-8ca8-8ee99a1bf94f)

Y encontramos la contraseña del usuario Mario.

![image](https://github.com/user-attachments/assets/daea1bda-5a88-41bb-a1c6-581dbd5cc259)

Nos logueamos en el login de wordpress con las credenciales obtenidas y ganamos acceso.

![image](https://github.com/user-attachments/assets/2dccecae-ade9-47fb-b971-eb8d4560ea6e)

Instalamos el pluggin File Manager.

![image](https://github.com/user-attachments/assets/d9212ed5-c876-4a77-8058-75b858902e40)

Añadimos un archivo php malicioso.

![image](https://github.com/user-attachments/assets/deba345d-8845-47c2-8afa-e936f1d83d07)

Nos vamos a la ruta donde lo hemos metido y ya lo vemos.

![image](https://github.com/user-attachments/assets/3c00adb1-39cb-42ee-9f4c-b0bad5fc68c8)

Lo abrimos y vemos que podemos inyectar código.

![image](https://github.com/user-attachments/assets/2f627668-b479-4af6-9b25-281602d7882c)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/5b43f082-9038-41de-9a55-b559eb48e505)

Vemos los permisos SUID que hay disponibles y nos encontramos el /env.

![image](https://github.com/user-attachments/assets/62bdf260-ce17-4d03-869e-59067cd7a898)

Nos vamos al GTFObins seguimos los pasos que nos dice y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/db027b37-ec33-442f-95e1-bbdff5e2d46e)









