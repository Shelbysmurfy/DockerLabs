# RESOLUCIÓN DE LA MÁQUINA HACKTHEHEAVEN

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/263f9405-2dbc-483a-8e78-e6cedce8edfb)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/e8c55064-2d97-4a83-a4a3-022e3fc6d406)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/bb3b10f4-e95f-49c7-956a-59d1a862cee6)

Abrimos la web.

![image](https://github.com/user-attachments/assets/88f6da66-4901-47ad-ade9-9f0c992f0909)

Vamos a hacer fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/7852d5c8-b4ce-47d6-8979-42bbab8eccd7)

Nos vamos a "idol.html" y vemos esto: 

![image](https://github.com/user-attachments/assets/f69aaa40-0a0d-4a01-afa7-a6ac9e20f625)

Le damos click al botón rojo y nos muestra un archvivo php con un mensaje.

![image](https://github.com/user-attachments/assets/bc33d270-714c-4005-9cb7-9bc6590d274f)

Vamos a hacer uso de la herramienta de wfuzz para ver si podemos encontrar algún parámetro para ejecutar comandos.

![image](https://github.com/user-attachments/assets/d0528a8e-bbae-4757-a46d-923ce1951fcd)

Intentamos visulaizar el /etc/passwd pero nos muestra esto: 

![image](https://github.com/user-attachments/assets/b33f681b-d39c-412b-8fdf-4ce6c08eee27)

Hacemos un wfuzz con un diccionario de LFI, en busca de algun que me funcione.

![image](https://github.com/user-attachments/assets/b585ecb5-66ef-4032-b6a0-8a05d0221426)
![image](https://github.com/user-attachments/assets/3ac5a1fc-208d-4742-bf01-464cfa07bd22)

Finalmente podemos ver el /etc/passwd, y vemos 3 usuarios: s4vitar, xerosec y mario.

![image](https://github.com/user-attachments/assets/ab156a58-9189-4d54-9fbf-adc1e677abc8)

Nos vamos al info.php y vemos que la función de subir archivos esta activa, así que seguramente tengamos que hacer algon con esto.

![image](https://github.com/user-attachments/assets/6b016262-6f68-4c1c-8902-aefda834c91e)

Nos vamos a hacktricks en busca de un LFI via info.php y encontramos esto: 

![image](https://github.com/user-attachments/assets/44463391-9972-45b6-b6f4-1525cecf557c)

Nos descargamos el archivo que nos dan y le cambiamos varias cosas: 

  1. El payload pondremos la reverse shell

      ![image](https://github.com/user-attachments/assets/c8da1f3f-122d-4157-8c5b-e6d4178447a2)

      ![image](https://github.com/user-attachments/assets/4f704bb5-d3a0-43d0-8389-a5f117268744)

  2. En la variable REQ1, tenemos que cambiarle la ruta

      ![image](https://github.com/user-attachments/assets/9baf5c15-35f0-4ba5-9756-0e55f98019b1)

      ![image](https://github.com/user-attachments/assets/199eec3b-3f33-4b37-8a0e-13fe216f4b01)

  3. En la variable LIFREQ también le cambiaremos la ruta

      ![image](https://github.com/user-attachments/assets/636e13f6-4567-4e2f-8039-c788ac0ac2b6)

      ![image](https://github.com/user-attachments/assets/0541dc18-2cd0-48d9-9e49-be3a846e2f73)

Una vez hecho esto, lo guardamos y ejecutamos el siguiente comando en nuestra terminal.

![image](https://github.com/user-attachments/assets/4a7bc1d5-cb81-47b6-83f9-be9a6c6afddb)

Y seguidamente ejecutamos el script de esta manera, mientras estamos en escucha con netcat para ganar acceso a la máquina.

![image](https://github.com/user-attachments/assets/a6efd307-939c-4abe-960a-e0524fd8a40d)

![image](https://github.com/user-attachments/assets/d83cfba5-616b-4383-8650-32bfdf9b33a9)

Una vez dentro nos vamos al directorio /home y vemos una nota para el usuario Mario.

![image](https://github.com/user-attachments/assets/8f36558f-f732-460a-aae9-50b3c22e5fad)

En ella hay una posible contraseña, que si la usamos para el usuario xerosec nos funciona "xerosec:megustaelfallout".

![image](https://github.com/user-attachments/assets/8b880431-bbcf-47e7-b1f3-f6f070a1c90c)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b0979957-00ba-4abf-b226-9608684e3391)

Nos vamos al directorio /tmp y vemos el archivo.py

![image](https://github.com/user-attachments/assets/580296ea-d613-484c-b5a8-491688ab6a2b)

En este vemos una librería "hashlib", vamos a crearnos un archivo llamado "hashlib.py" para que cuando se ejecuta el script nos coja nuestro archivo hashlib que hemos creado, ya que es el que tendrá mas cerca.

![image](https://github.com/user-attachments/assets/2921406d-f90a-417a-80e6-36553f613e4e)

Seguidamente ejecutamos el permiso SUDO que tenemos y nos convertimos en mario.

![image](https://github.com/user-attachments/assets/6091b6e8-8568-4fca-aea3-733e299ca6ce)

Nos vamos al usuario mario y vemos un archivo.txt con una pista.

![image](https://github.com/user-attachments/assets/ca5347a6-c939-4434-b723-d07c6275d1e9)

Miramos los procesos con ps -faux, y al final del todo vemos que se está ejecutando un servicio php de manera local por el puerto 9999.

![image](https://github.com/user-attachments/assets/a78763c1-1151-43d7-888d-10a81229a67d)

Ejecutamos con curl y vemos resultado.

![image](https://github.com/user-attachments/assets/537ac900-c184-4618-a9fb-cb03443543d0)

Vamos a tirarnos una reverse shell url encodeada y ganamos acceso correctamente.

![image](https://github.com/user-attachments/assets/91663e2e-f543-4c19-92aa-aab3ea0ae5b9)

Hacemos sudo -l, vemos el permiso xargs, nos vamos al GTFObins.

![image](https://github.com/user-attachments/assets/dda79908-114c-4695-ba7c-0ede54129e39)

Ejecutamos lo que nos dice y nos convertimos en root.

![image](https://github.com/user-attachments/assets/4c7d2f76-e1bb-4b5c-b457-8846977ff673)


