# RESOLUCIÓN DE LA MÁQUINA FOODING 

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/de246fe2-e987-4eee-83ae-8e61dd62cdb3)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/db31e7fa-b482-4b32-89bc-7893c96dd7e4)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/f9529a11-ff23-42e5-bdfc-33d15c584786)

Abrimos la web por el puerto 80 y vemos esto: 

![image](https://github.com/user-attachments/assets/3b947ef9-2832-457f-9b65-f6a83fa096bf)

Le añadimos el puerto 443, y nos muestra un mensaje.

![image](https://github.com/user-attachments/assets/c7718a3d-bb59-4692-87de-84d2c0449824)

Le añadimos el https delante de la IP, como nos menciona y vemos una web diferente, pero no vemos nada nuevo, y como estamos usando "https", no podemos hacer fuerza bruta para buscar posibles directorios.

![image](https://github.com/user-attachments/assets/a8c49e4b-86a3-4324-b31a-42c5715dc2d9)

Así que probamos con meternos al puerto 8161, nos pide unas credenciales, y si usamos unas credenciales básicas como "admin:admin" ganamos acceso.

![image](https://github.com/user-attachments/assets/4ba77ce9-0d63-4103-bdcb-70d313294a5e)

Nos metemos en "Manage ActiveMQ broker" y encontramos la versión de este.

![image](https://github.com/user-attachments/assets/541e9c0e-0771-4ca0-95ce-ff7ed994e06b)

Buscamos algún posible exploit para esta verión.

![image](https://github.com/user-attachments/assets/a2b0ba26-aa8b-49b9-b39c-9c2522984780)

Github exploit: https://github.com/evkl1d/CVE-2023-46604

![image](https://github.com/user-attachments/assets/8a66995d-3a2f-4646-b4a1-aa577d471f55)

Nos lo traemos a nuestra máquina con git clone.

![image](https://github.com/user-attachments/assets/e1a78f28-9418-4b48-9f6b-50f210b7f60f)

Para ejecutarlo antes tendremos que cambiar unas cosas del archivo poc.xml, incluiremos nuestra IP y el puerto que pondremos en escucha.

![image](https://github.com/user-attachments/assets/ae13fd8d-7429-4f62-b83f-3091046b3651)

Ahora creamos un servidor con python para pasarnos el archivo que hemos modificado por el puerto 8080.

![image](https://github.com/user-attachments/assets/494bc02e-7549-4301-9d27-e8c6775fa7bf)

Mientras también nos pondremos en escucha con netcat por el puerto que hemos indicado en el archivo poc.xml, para que cuando nos pasemos el archivo ganemos acceso a la máquina víctima.

![image](https://github.com/user-attachments/assets/7778e8a1-7f3c-450a-b01c-7c856f18abad)

Y por último ejecutaremos el exploit indicando la IP de la máquina víctima, junto a un puerto que nos dice, y la url de donde se encuentra el archivo poc.xml

![image](https://github.com/user-attachments/assets/ecd652fe-cb80-411f-9bee-c989c577edf7)

Ganamos acceso al sistema, y ya somos root.

![image](https://github.com/user-attachments/assets/6cde5b4e-9805-4592-9d95-a92e48b3c225)






