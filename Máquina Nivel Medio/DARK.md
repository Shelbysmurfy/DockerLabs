# RESOLUCIÓN DE LA MÁQUINA DARK

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/98ebb602-c4b5-4e5b-911a-68c84c573bd7)

Hacemos un ping para cada una de las IP's, para saber con que IP tenemos que trabajar.

![image](https://github.com/user-attachments/assets/642d6390-8162-4e87-8517-35079507518e)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/112f901e-3837-4334-95f6-ad63568793d3)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/72ab68bf-e7e9-4418-b10c-12484446b04f)

Abrimos la web.

![image](https://github.com/user-attachments/assets/5e430b22-48cb-40f1-ad59-73b2d7ab34de)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/348fcfed-13b2-46a6-90ac-3654407ed23d)

Miramos al directorio /toni.

![image](https://github.com/user-attachments/assets/9a16e2b9-45f2-4624-b690-88e085a7b854)

Hacemos fuerza bruta con hydra para el usuario toni y encontramos credenciales válidas.

![image](https://github.com/user-attachments/assets/3030b48a-7ce4-41ba-b52b-48b1881c51a6)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/2d9a35f6-eb3b-4100-97a5-6a5893632648)

Vemos que hay una segunda máquina.

![image](https://github.com/user-attachments/assets/4daed993-c747-4515-a43d-a55f19c7296d)

Nosotros ahora lo que queremos es llegar desde la IP 20.20.20.2 a 20.20.20.3, que es donde el directorio info, nos decia que habia que ir.

Primero nos descargamos chisel, y nos creamos un server desde nuestra máquina.

![image](https://github.com/user-attachments/assets/83df93bc-ce0d-40d6-9e7a-8de6ac119660)

Y ahora hacemos nos conecatmos a ella desde la máquina víxtima.

![image](https://github.com/user-attachments/assets/bbbbc8d2-de8c-4455-a87c-e22d06fcb2ad)

Y recibimos que estamos en escucha.

![image](https://github.com/user-attachments/assets/2ab691ea-26eb-4563-ab87-9d5acaed82c9)

Nos vamos al FoxyProxy y para crear una configuración que nos permita ganar acceso a la IP a la cual nosotros queremos llegar (20.20.20.3).

![image](https://github.com/user-attachments/assets/b5b1eeed-77b4-4b67-bfc6-5188228a7ed5)

SE SUPONE, PERO NO ME VA CON EL PROCY NS PORQUE

Gano acceso a la IP desde la web, me vuelve a salir una barra de comandos, en la que puedo ejecutar comandos.

Hago una reverse shell, pero antes hay que configurar el socat, para ello tendremos que descargarlo.

Y escalo privilegios hasta root.
