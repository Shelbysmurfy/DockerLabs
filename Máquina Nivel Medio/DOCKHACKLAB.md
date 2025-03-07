# RESOLUCIÓN DE LA MÁQUINA DOCKHACKLAB

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/0063c133-0b37-4e8c-8a1e-7f93343287b1)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6a9180fa-000d-4cd3-aa25-ddab2e74ea62)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/4d51dfce-ad0e-4a34-bb6c-a1fa656c0856)

Abrimos la web.

![image](https://github.com/user-attachments/assets/90b52975-60e7-4536-b5e4-95a1db39d9e6)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/26078d18-4dae-4177-b38a-03aac8d6a92e)

En el directorio /hackademy vemos una subida de archivos.

![image](https://github.com/user-attachments/assets/8502b72d-4afb-45f7-842a-c5f6468719b8)

Subimos un archivo.php malicioso.

![image](https://github.com/user-attachments/assets/d35f4d05-dc50-4fd0-b5db-7a12f0a40b86)

![image](https://github.com/user-attachments/assets/fd0ce473-ea7c-4c64-a749-be12ccdbae57)

Como vemos nos muestra tres x delante del nombre del archivo, vamos a crear un script que busque posibles combinaciones para esto.

![image](https://github.com/user-attachments/assets/8ada6306-ef6e-407c-800d-304a073b7151)

Una vez creado lo ejcutaremos y crearemos un archivo "diccionario" con todas estas combinaciones.

![image](https://github.com/user-attachments/assets/227181a4-8f8d-4faf-908a-ddce8f2aefd8)

Y ahora usaremos la herramienta feroxbuster en busca de la ombinación correcta, y vemos que es "klp_shell.php".

![image](https://github.com/user-attachments/assets/cb2d9ed5-7e15-4b47-9083-730fd166128e)

Intentamos ejecutar comandos a partir de este archivo malicioso y funciona correctamente.

![image](https://github.com/user-attachments/assets/12a1a009-6661-4477-b816-1e9529271499)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/2ccc5d40-00ac-41b2-aaaf-2a4f1a0ba720)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/e77f0013-9acf-48cb-9afb-6919aee8d128)

Nos vamos al GTFObins y seguimos los pasos que nos dice.

![image](https://github.com/user-attachments/assets/fbe94fb9-b41d-4b4c-9c54-c5327bb094a1)

Y escalamos privilegios correctamente.

![image](https://github.com/user-attachments/assets/f185d2ca-2c23-449b-9cad-1f733c6ccb68)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/27a579dd-b78e-4700-a104-3dd6eb117a3a)

Ejecutamos el comando que indica el GTFObins para escalar privilegios pero me muestra este error.

![image](https://github.com/user-attachments/assets/af33315d-11ab-42a0-8920-bfe4ebb48f7d)

Hacemos docker run --help como nos recomienda y nos muestra una posible secuencia de puertos.

![image](https://github.com/user-attachments/assets/9637501c-7246-44b2-8b00-b8ea5d4ce2a9)

Lo miramos y efectivamente es una secuencia.

![image](https://github.com/user-attachments/assets/e6af9e3a-4f7a-4d1d-870a-7c30428ee5b0)

Vamos a ir a nuestra máquina atacante y vamos a hacer un knock con la secuencia de puertos que tenemos.

![image](https://github.com/user-attachments/assets/addfb929-73c1-41c1-9012-fb013962df50)

Y ahora si volvemos a ejecutar el comando de antes nos escala privilegios correctamente.

![image](https://github.com/user-attachments/assets/51fc2487-0e2f-4a2e-bc46-c0dd610fc6de)
