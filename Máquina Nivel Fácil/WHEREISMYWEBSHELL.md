# RESOLUCIÓN DE LA MÁQUINA WHEREISMYWEBSHELL

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/f4d2a3ca-b4b1-42d0-a34a-41e47ca0ff91)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/c44804ee-0411-49e7-a5b9-cc38de7831b2)

Abrimos la web.

![image](https://github.com/user-attachments/assets/bf5fa61c-c955-4ac2-9844-683070164f66)

En la web vemos esta pista que seguramente nos sirva para más adelante.

![image](https://github.com/user-attachments/assets/1a12e700-68ae-4ad0-b563-9553fbf2484a)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/f87f8384-e2ad-424e-a0ae-2274b81d325a)

El warning.html nos muestra esto: 

![image](https://github.com/user-attachments/assets/f7b78e1d-2de3-4e05-adc3-e03f2d1ff6f9)

Y el shell.php no muestra nada, ni tampoco deja ejecutar una terminal con el parámetro que hemos usado.

![image](https://github.com/user-attachments/assets/0208544e-6c35-40c4-9110-64ec9e9b8c75)

Usamos la herramienta wfuzz para saber el posible parámetro que está usando este archivo php para ejecutar comandos.

![image](https://github.com/user-attachments/assets/8f046428-d10b-496a-8b7f-c27a231603c6)

Probamos el parámtero "parameter" y efectivamente nos deja ejecutar comandos.

![image](https://github.com/user-attachments/assets/4f4ae27b-5449-4646-9416-f681782cb33b)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/1479661f-ef0f-40ca-936b-aed949a944d3)

Nos vamos al directorio /tmp, y encontramos una posible contraseña del usuario root.

![image](https://github.com/user-attachments/assets/8e32899e-6288-44d5-9e6d-909518a21236)

Y ya somos root.

![image](https://github.com/user-attachments/assets/1dbd48f4-5bb3-4b57-8974-37990aee953c)


