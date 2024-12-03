# RESOLUCIÓN DE LA MÁQUINA SECRETJENKINS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/c462e744-9740-4cbb-9abf-a87ae757bbcb)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/2c47f266-039b-433f-93de-7364c53ccbd4)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/e9bf1a47-803d-48a4-adf2-72d6c6faa71a)

Abrimos la web, puerto 8080.

![image](https://github.com/user-attachments/assets/ebe0d3e2-9e45-4294-9998-7c971c11fdef)

Nos metemos en el robots que nos sale que está abierto.

![image](https://github.com/user-attachments/assets/56f0bd0d-f1f5-4589-83ee-4302ffd625f0)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/d32b7a20-8e52-4ac0-be8e-74be205c186e)

En la ruta de /people/ encontramos varios usuarios: 

![image](https://github.com/user-attachments/assets/c97c7906-5238-4855-b409-17ad0f669460)

Nos metemos en la ruta /main que nos devuelve un error 500.

Un error 500 es un código de error genérico que indica que algo ha ido mal en el servidor (ordenador) en el que se alojan los archivos de tu sitio web.

![image](https://github.com/user-attachments/assets/af979e59-74f7-4fae-8b72-35059ac6ee7b)

Viendo lo que provoca un error 500, vamos a buscar vulnerabilidades o posibles exploits para la versión de jenkins.

![image](https://github.com/user-attachments/assets/c2c34d61-9fbe-4b56-92b7-92159dafbba0)

Encontramos el CVE

![image](https://github.com/user-attachments/assets/8dc1716d-8b98-46b0-8e6e-4d91d33a2a81)

![image](https://github.com/user-attachments/assets/c88cd027-bece-45d8-af8b-9b44e256de77)

Encontramos un github que nos permitirá explotar esta vulnerabilidad.

https://github.com/Maalfer/CVE-2024-23897

Lo clonamos en nuestra máquina.

![image](https://github.com/user-attachments/assets/9aecbaf4-9d36-49c1-a06d-cdc6083466f3)

Lo usamos como nos dicen y conseguimos ver el /etc/passwd

En el encontramos el usuario pinguinito y el bobby.

![image](https://github.com/user-attachments/assets/0a5b320b-5be6-4582-abd1-7ca4efd5d4ef)

Hacemos hydra y encontramos la password de el usuario bobby.

![image](https://github.com/user-attachments/assets/a0827515-b04c-4942-9f22-93e12c8f0a09)

Entramos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/05e9f024-3e3d-4cff-89cf-2536d57ccb69)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/57d19623-4153-476d-b754-a3923bc2a65b)

Nos comvertimos en el usuario pinguinito.

![image](https://github.com/user-attachments/assets/c2d54dc9-4854-4c5f-9af5-e0760b7eeb52)

Volvemos a hacer sudo -l y nos muestra esto: 

![image](https://github.com/user-attachments/assets/a9d4062c-475e-4d2a-9d26-dbffa82c6c43)

Creamos un archivo maliciosos para poder convertirnos en root desde nuestra máquina, ya que en la máquina víctima no deja.

![image](https://github.com/user-attachments/assets/90fc4888-b851-48e3-8d9f-8f07ac60a2a9)

Nos lo pasamos a nuestra máquina víctima.

![image](https://github.com/user-attachments/assets/ad2b9d7f-a72f-4b86-b1cf-76086eb1a542)

![image](https://github.com/user-attachments/assets/8801d55f-68a5-46cd-a55a-413c09209050)

Y ya somos root.

![image](https://github.com/user-attachments/assets/40e04cf8-37c3-4dcb-ab01-5836edcec2f5)








