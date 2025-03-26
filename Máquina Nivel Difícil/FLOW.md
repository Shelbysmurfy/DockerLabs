# RESOLUCIÓN DE LA MÁQUINA FLOW

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/737052c9-4932-4b28-9644-5be536105de0)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/0ab5c217-8eaa-48b7-ae56-6afa143defc7)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/6d2e513e-fe62-404a-8ec8-d51b9e02a16f)

Abrimos la web y vemos un login.

![image](https://github.com/user-attachments/assets/c099e556-98ef-46ce-b959-558b7e6406a7)

Nos vamos al código fuente y encontramos una posible credencial "d1se0".

![image](https://github.com/user-attachments/assets/e87e1f6f-5a8d-4a37-a69a-246351469876)

Abrimos el burpsuite para ver la petición.

![image](https://github.com/user-attachments/assets/24a1a969-1246-408e-9350-2ec9e082de43)

Hacemos fuerza bruta con hydra para buscar posibles credenciales válidas.

![image](https://github.com/user-attachments/assets/04ec21c4-c380-4fd5-a835-dd36af44584f)

Nos conectamos con las credenciales encontradas y vemos un panel de admin.

![image](https://github.com/user-attachments/assets/c24ab57b-9819-4f89-9781-56f958ff5b21)

Cogemos la petición con burpsuite y si en el apartado de "User-Agent", ejecutamos comandos recibimos respuesta.

![image](https://github.com/user-attachments/assets/e72229f6-67c7-4715-a0bd-76243a1fa5d3)

Miramos el /etc/passwd, y vemos el usuario "flow".

![image](https://github.com/user-attachments/assets/846d4efd-53b0-4f7f-96c7-1916428adea0)

Intentamos hacer un hydra para este usuario y el servicio ssh pero no encontramos nada.

Así que volvemos a burpsuite y si hacemos un find de el usuario flow encontramos dos rutas donde aparece.

![image](https://github.com/user-attachments/assets/a25384c8-dd3c-4fc9-a7ee-e04ddd41d122)

Vamos a la de /usr/bin/secert, y encontramos una posible credencial codificada.

![image](https://github.com/user-attachments/assets/665c68d3-3a30-4f60-8563-0220f2878047)

Vamos a cyberchef y desencriptamos el código que hemos obtenido.

![image](https://github.com/user-attachments/assets/1588aa23-471b-49a0-bbfc-4df9a9bdebfc)

Nos conectamos al servicio ssh con las credenciales obtenidas "flow:d1se0isthebest@$$!".

![image](https://github.com/user-attachments/assets/9f1d108e-9f1d-490f-8a8c-b0620eff741f)

Hacemos ls y vemos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/739f6670-bdc2-400d-823a-402567056233)

Hacemos un sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/3c1aad7d-0920-47ca-a08a-b6d2c8eb999e)

Lo ejecutamos y vemos esto: 

![image](https://github.com/user-attachments/assets/3750594d-97f6-4e3e-8f87-4b6cb6c5646b)

Nos traemos el archivo manager a nuestra máquina.

![image](https://github.com/user-attachments/assets/e32e149f-b629-4818-920e-813695072a6b)

Lo abrimos con ghidra.

![image](https://github.com/user-attachments/assets/58f721a4-1417-4554-839a-0c83b2e401b4)

Vemos que en la función main(), se crea un buffer de 76 bytes, y luego se nos pide un input que luego se almacena en ese buffer. Para almacenarlo se usa fgets(), pero no se usa de forma segura, ya que se le pasa como máximo de bytes 80, por lo que podemos sobrescribir 4 bytes en el stack.

Luego, local_c, que es un int, se compara con 0x726f6f74, que en ASCII es "root". Si es igual, se llama a una función que escribe datos en un archivo, y luego se llama a otra función que nos va a permitir ejecutar comandos.

El buffer de nuestro input está abajo del todo, y encima esta local_c, que es un int de 4 bytes. Entonces si escribimos 76 bytes, los siguientes 4 bytes sobrescriben local_c, ya que está encima. Si sobrescribimos local_c con 0x726f6f74, ganamos la ejecución de comandos.

Creamos la cadena de 80 carácteres con los 4 últimos con la palabra root, pero al ejecutarlo no funciona.

![image](https://github.com/user-attachments/assets/2d878e05-d6eb-4e98-8115-0b267bf3622d)

![image](https://github.com/user-attachments/assets/1918f2f8-fd3e-4d1f-b2e4-6a88ea4d32a6)

Probamos a poner root al revés ya que se trata de un archivo LSB y nos funciona correctamente.

![image](https://github.com/user-attachments/assets/e320003e-67bf-4042-97dc-3aafe088c9a6)

![image](https://github.com/user-attachments/assets/0590be0d-753f-4037-9eb9-5844f0038103)

Una vez dentro encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/c18e3b38-16eb-4e70-a825-e4c07f183209)
