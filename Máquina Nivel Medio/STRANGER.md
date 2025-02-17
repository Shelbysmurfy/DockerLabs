# RESOLUCIÓN DE LA MÁQUINA STRANGER

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/cefd60f8-b56a-48b2-95b0-1cfeedec56b4)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/d0df29eb-da59-42a1-ba2f-0a4d1603534d)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/751435a4-cd94-4efb-abe4-82bbfa63702e)

Entramos en la web y vemos esto: 

![image](https://github.com/user-attachments/assets/b360b914-44af-4f99-a59c-e96135828528)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/40c7332c-dbda-4aed-9e18-7af3bbe60216)

Entramos en la ruta y vemos posibles usuarios o contraseñas pero no conseguimos ganar accceso en ningun servicio.

![image](https://github.com/user-attachments/assets/aa6001d3-54d9-4e8f-99d0-d2f65835825d)

Volvemos a hacer un gobuster, pero ahora con la última ruta que hemos conseguido.

![image](https://github.com/user-attachments/assets/761f7527-edd1-4191-8fe6-c71dca1d0aac)

En el /secret.html vemos esto: 

![image](https://github.com/user-attachments/assets/e0da7d55-c569-4b21-8312-9bd67db65c08)

Hacemos un hydra y sacamos las credenciales de el servico ftp.

![image](https://github.com/user-attachments/assets/c06d3dd9-7fb7-40fb-a966-8a70d0fcd345)

Nos conectamos al servicio ftp con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/0eb11ffe-4c15-4833-85fb-49130465df42)

Encontramos una posible clave privada en formato PEM (Privacy-Enhanced Mail).

![image](https://github.com/user-attachments/assets/482dfbfb-2531-4e4c-b5bd-d666df06d149)

![image](https://github.com/user-attachments/assets/19f93e40-cd01-41e8-a645-a0e4e6ce2fff)

Nos la traemos a nuestro máquina local.

![image](https://github.com/user-attachments/assets/af2be819-d2d7-4cec-8949-188fe43a5666)

Tenemos un archivo llamado private.txt con este contenido: 

![image](https://github.com/user-attachments/assets/7aa43773-bfcf-42f7-8b19-e3a7ca7c4d2f)

Utilizamos el archivo private_key.pem para intentar descifrar el contenido de private.txt.

![image](https://github.com/user-attachments/assets/291a798e-965d-4846-ae70-ee146a63fad9)

Nos conectamos al servicio ssh con las credenciales (mwheeler:demogorgon)

![image](https://github.com/user-attachments/assets/9897ba30-fc29-4ddc-8fad-583ad7d09d9e)

Nos convertimos en admin con las credenciales que hemos usado antes para conectarnos al servico ftp.

![image](https://github.com/user-attachments/assets/7f3695c3-8b5a-4e74-8f11-74f58f142f78)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/50a5ad1e-195b-4a0c-b948-25a1447dda0e)

Y ya somos root.

![image](https://github.com/user-attachments/assets/e6d1510e-a276-4fb8-b2f2-004f4ed3d247)

Y encontramos la flag del usuario root.

![image](https://github.com/user-attachments/assets/43295f9f-8123-429a-a132-14ba429b441f)

