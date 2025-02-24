# RESOLUCIÓN DE LA MÁQUINA CINEHACK

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/687205aa-78a3-42c1-b12d-1c55dd94abcc)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/174e6a6a-e162-4e4d-a04a-d5e09551174d)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/0ed6488f-4246-4f40-b0b9-bc402cdd0f13)

Abrimos la web.

![image](https://github.com/user-attachments/assets/e2fcc184-61c1-4fe9-a241-70eb1fb08589)

Añadimos el dominio que nos dice al abrir la página en nuestro /etc/hosts, y lo abrimos.

![image](https://github.com/user-attachments/assets/fd3bb68d-cb3a-4d56-a4e7-2d2d4a2b2f88)

![image](https://github.com/user-attachments/assets/c3e646c9-f136-417f-996b-7a05ce518f70)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/c404e98f-6efd-4714-9f3c-224330146f8e)

Añadimos el /reservation.php a nuestra url.

![image](https://github.com/user-attachments/assets/261c069e-3e45-4460-bb90-599d0464eb7d)

Si nos metemos en una peli para hacer la reserva, al mirar el código fuente vemos esto: 

![image](https://github.com/user-attachments/assets/9fca8e9f-0a17-4a85-aef4-6ffe3d541002)

Intentamos hacer uso de la herramienta wfuzz, para buscar posibles comandos que añadir después del parámetro que hemos conseguido "problem_url", pero no encontramos nada.

Como el parámetro contiene "url", vamos a intentar inyectar un archivo malicioso de nuestra máquina como atacante a través de una ruta http.

Para ello tendremos que abrirnos un servidor python en nuestra máquina.

![image](https://github.com/user-attachments/assets/f39edfb0-601e-43dc-85f9-8cf62fbb4919)

![image](https://github.com/user-attachments/assets/5d3af086-e187-4cf1-8f07-7bb87a4ea5ce)

Y recibimos respuesta, eso quiere decir que se ha subido correctamente, pero no sabemos la ruta de donde se encuentra.

![image](https://github.com/user-attachments/assets/35da17e6-755f-4e4a-b16c-93f5227d4b0a)

Después de probar muchas cosas, intentamos usar como ruta los dos nombres que salen en la portada de la única película en la que podemos reservar y uno de ellos funciona correctamente.

![image](https://github.com/user-attachments/assets/761dddb7-fb8a-4be7-af98-1006857022c8)

Una vez dentro intentamos abrir nuestro archivo.php, pero no nos deja, así que nos subimos el mismo archivo con la extensión .phml

![image](https://github.com/user-attachments/assets/814cd687-90a0-422c-a808-abc2383e1e3d)

Lo abrimos y podemos ejecutar comandos perfectamente.

![image](https://github.com/user-attachments/assets/2b1e9ba5-9787-4f76-a70d-d3aceb335689)j

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/24313568-a7e3-4f09-9a08-4b0c5c929ff7)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b3029e15-deff-415a-9fe4-c195214fa976)

Nos conectamos como boss con el permiso SUDO que tenemos.

![image](https://github.com/user-attachments/assets/35de43a8-843b-4d36-a440-da1eebb3d391)

Encontramos la primera flag la del user.

![image](https://github.com/user-attachments/assets/e42f5e18-1a68-41b3-a9f5-8abf0e009e94)

En el www-data, vemos este archivo y al ver que el usuario boss tiene permisos vamos a abrirlo para ver que está ejecutando.

Hay que hacerlo rápido porque parece ser que uno de estos archivos que se ejecuta cada mínuto me está hechando del usuario boss.

![image](https://github.com/user-attachments/assets/cf1fa153-e781-4e4d-8ec5-32a9322d084f)

Está ejecutando tanto el /opt/update.sh como el /tmp/script.sh cada minuto.

![image](https://github.com/user-attachments/assets/790e5fca-b437-43d4-84ac-a9049ce1134e)

Por lo que nos salimos del usuario boss, ya que sino nos hecha, y creamos el archivo /tmp/script.sh, ya que en el usuario www-data no está. 

Esto lo usaremos para escalar privilegios.

![image](https://github.com/user-attachments/assets/c937b498-99a6-4239-99b2-b2009a1542b0)

Y ahora tendremos que esperar 1 minuto a que se ejecute el crontab para ver si he conseguido escalar privilegios.

![image](https://github.com/user-attachments/assets/2cc64457-1034-4b73-9adf-cb18c289bd16)

Y ya somos root.

![image](https://github.com/user-attachments/assets/9cc3ae34-9391-4291-b0d6-6ea89dadd22a)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/ce75d2ed-6e34-4844-949a-c24e7e5e4d49)

