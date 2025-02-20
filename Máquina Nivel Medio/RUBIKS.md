# RESOLUCIÓN DE LA MÁQUINA RUBIKS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/cc8e356f-94e1-4ca6-852d-b18338c486a6)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/a15ceefa-29c4-42ae-85b4-38616696c3db)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/af16cee4-8de0-4b88-9656-3316592ee8f0)

Añadimos el dominio que nos dan en el /etc/hosts

![image](https://github.com/user-attachments/assets/e2b33274-511b-4bf2-b87b-833e1c1294dd)

Abrimos la web.

![image](https://github.com/user-attachments/assets/0a6fc5fc-b5f4-4fc1-b90d-a4d2487bc7cd)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/dd010ccc-494f-4ed0-b3c4-7e94b41eca19)

Podemos ver un Panel de Administración en el que encontramos dos usuarios.

![image](https://github.com/user-attachments/assets/7fa5725e-756a-44ab-9a95-dbcb41fee66e)

Entramos en el apartado de configuraciones y vemos varios elementos en el lateral.

![image](https://github.com/user-attachments/assets/7f615def-a4f6-4941-b7be-dcd0e9ae8e7b)

El único que funciona es el console, pero no nos muestra una página válida.

![image](https://github.com/user-attachments/assets/5488bee8-6ee1-4adc-96cc-d174eb0777f3)

Si nos fijamos en la url, /administration desaparece cuando le damos a console, por tanto lo añadimos y la página funciona.

![image](https://github.com/user-attachments/assets/c1bbce2a-b7d3-4343-a5d0-77124dcb8c58)

Probamos difrenetes codificaciones, para ver cual nos devuelve resultado, base 32 es la correcta.

Hacemos un /etc/passwd para ver posibles usuarios.

![image](https://github.com/user-attachments/assets/f6d7bb17-7165-4230-ad5f-bf059fd16474)

Ejecutamos el comando ls -la y encontramos esto: 

![image](https://github.com/user-attachments/assets/ad7a1d1a-23c2-41bb-b9ea-c2ba861d0237)

Vamos a observar el archivo id_rsa con el comando "cat id_rsa"

![image](https://github.com/user-attachments/assets/865f9569-fbc9-4c50-ba15-f20a96e83a16)

Nos vamos a nuetsra máquina, creamos un archivo "id_rsa", con este contenido, le damos permisos y nos conectamos al servicio ssh con el usuario luisillo, que es el que hemos visto antes en el /etc/passwd

![image](https://github.com/user-attachments/assets/ef6baa70-5588-4b94-82a9-06f7198e5f86)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/376be362-4582-46a6-adf6-d21799f00fdc)

Vamos a leer el archivo para ver que se ejecuta por detrás.

![image](https://github.com/user-attachments/assets/a0d5ff5a-0357-4718-a158-818fe133dd40)

Y si pongo el número 666, me devuelve "correcto", pero no me permite escalar privilegios.

![image](https://github.com/user-attachments/assets/28ca4449-6a1f-4a2c-b0b4-f97cecd971f7)

Para ello agregaremos el comando "a[$(/bin/bash >&2)]+42" para poder ejecutar código arbitrario.

Esto lo encontramos aquí: https://www.vidarholen.net/contents/blog/?p=716

Y ya somos root.

![image](https://github.com/user-attachments/assets/915d745d-0cc1-4afe-839e-88cbf6125a7b)




