# RESOLUCIÓN DE LA MÁQUINA MOVE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/68a99ae3-62cd-4687-b240-05e734aee63d)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/4fe4404b-7ebc-4229-9dba-ae19e8d119e9)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

El puerto 3000 no lo ponemos porque da problemas.

![image](https://github.com/user-attachments/assets/e4e7e7a6-96f9-463f-97f3-e8eea53ff981)

Abrimos la web y no hay nada.

![image](https://github.com/user-attachments/assets/961af34e-8ce4-415c-ae6a-d54f2fd48e19)

Hacemos fuerza bruta con dirsearch y encontramos un archivo .html

![image](https://github.com/user-attachments/assets/efd0fbbc-f5c9-4ceb-b462-fc9d4c5f051c)

Entramos en el archivo y nos da una pista sobre una posible pass.

![image](https://github.com/user-attachments/assets/22fcb911-d02a-4d5e-9e4f-6830c140ee2c)

Nos conectamos al servicio ftp con el usuario anonymous.

![image](https://github.com/user-attachments/assets/907f4e46-2679-4f30-a468-104ddefaa388)

Encontramos un archivo cifrado y nos lo descargamos para tenerlo en nuestra máquina.

![image](https://github.com/user-attachments/assets/7db0eceb-c0fe-49a3-baa4-7d4b5270617a)

Usamos keepass y nos da error por la versión del archivo.

![image](https://github.com/user-attachments/assets/a605ef08-5d55-40a5-ac48-489068c41028)

En el puerto 3000 tenemos este login.

![image](https://github.com/user-attachments/assets/281e552c-8195-41ce-b42d-161c8a07e83d)

Usamos las credenciales default admin:admin y ganamos acceso.

![image](https://github.com/user-attachments/assets/f08b38fe-a8c6-4f26-8148-665041c54bb7)

Dentro parece que no podemos hacer nada.

Hacemos whatweb.

![image](https://github.com/user-attachments/assets/aa03ac1c-5756-4fdf-83ff-de2b3a89799d)

Vemos que está utilizando Grafana[8.3.0]. Vamos a buscar algún exploit que podamos utilizar.

![image](https://github.com/user-attachments/assets/52064ec4-2477-4362-b78e-6fcce84290dd)

Este script nos permite ver archivos internos del servidor.

Para ello primero tendremos que descargarlo.

![image](https://github.com/user-attachments/assets/c8b0d8dc-9a82-45f5-bfc4-794962394d8a)

Y luego lo ejecutamos y leemos el archivo /etc/passwd para ver si hay algun usuario.

![image](https://github.com/user-attachments/assets/29e5ca66-2024-4000-8529-6efc2161b92f)

También miramos el directorio /tmp/pass.txt, que es la pista que nos habían dado antes.

![image](https://github.com/user-attachments/assets/f10cc466-8c42-4229-a542-bc7227810280)

Y entramos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/6bb7bfc1-7e94-47b8-91c7-4d60a5951ba2)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/bedde4b6-5a74-44ce-95b0-7cb04c8dc2f7)

Nos vamos al archivo maintenance.py y le cambiamos el contenido, ya que pertenece al usuario freddy.

![image](https://github.com/user-attachments/assets/daa60924-1908-4d3c-9605-58f1ab31d7b1)

![image](https://github.com/user-attachments/assets/5882fe67-e94e-440f-a550-54dbdbda64b4)

Y ya somos root.

![image](https://github.com/user-attachments/assets/8396fcf5-d0f4-49ed-bb2b-f6059651fae3)






