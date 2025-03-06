# RESOLUCIÓN DE LA MÁQUINA STRONGJENKINS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a069b367-e476-407d-a433-9bbe203fb24b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/fdfe01f3-9f1f-4424-acd9-6e656f67e7fa)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/d600a5c5-92c3-4436-b0c1-e3ce3e0f5188)

Abrimos la web y vemos un login.

![image](https://github.com/user-attachments/assets/7e373bbd-40c9-4871-ab05-cf1a4ff8ae9d)

Abrimos el robots.

![image](https://github.com/user-attachments/assets/70d60ad4-07d3-4db1-a654-e07159c963ca)

Como no encontramos nada, intentamos hacer hydra con un usuario default como es admin pero no funciona.

Nos vamos a burpsuite y vamos a intentar hacer el ataque desde el intruder, para ello tendremos que seleccionar la contraseña, que es lo que buscamos.

![image](https://github.com/user-attachments/assets/7c183b93-8e19-422f-a4c7-d71d6c7618b3)

Seguidamente cargaremos el rockyou.

![image](https://github.com/user-attachments/assets/3f12274c-5398-4d1a-bf73-3e9d5ffd43ef)

Y por último nos iremos al Grep - Extract y marcaremos el logionError para determinar si las credenciales són válidas.

![image](https://github.com/user-attachments/assets/a19dbcf2-366d-40ee-90ec-730acaea782d)

Filtramos por los que no devuelven "loginError", y vemos que la contraseña es "rockyou".

![image](https://github.com/user-attachments/assets/51d52232-fb3f-4e77-a798-d36cca8dbfb8)

Nos conectamos por el login del jenkins con las credenciales obtenidas "admin:rockyou".

![image](https://github.com/user-attachments/assets/b6e8883b-e4f5-4711-8dc2-cb9727f0d58b)

Una vez dentro encontramos una consola que permite la ejecución de scripts de Groovy.

![image](https://github.com/user-attachments/assets/4310dc16-7038-4549-8bfd-20e0a455ee0e)

Vamos a hacer una reverse shell con groovy.

![image](https://github.com/user-attachments/assets/cedf48b1-d881-453b-8960-dccda0f6c4f7)

![image](https://github.com/user-attachments/assets/7222282d-9fb8-4b77-b31b-2291ae953507)

Ganamos acceso correctamente.

![image](https://github.com/user-attachments/assets/23e358f2-123f-4fb7-b2a1-bf877e5f8d61)

Miramos los permisos SUID y encontramos uno con el que provablemente podamos escalar privilegios "python".

![image](https://github.com/user-attachments/assets/b73fa634-ed3b-42d0-aa93-1d4c1841c50c)

Y efectivamente ya somos root.

![image](https://github.com/user-attachments/assets/c51e33b0-703a-40bd-8ab4-001c2512252a)

