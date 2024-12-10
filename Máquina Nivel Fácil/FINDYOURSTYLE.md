# RESOLUCIÓN DE LA MÁQUINA FINDYOURSTYLE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/7addb13b-2320-416b-ab49-17f98c756808)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/8afe11aa-4dc8-497a-a2fe-84fbb283845c)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/7ab91ece-752e-416b-bb4f-80b09ce4d339)

Abrimos la web.

![image](https://github.com/user-attachments/assets/4c0dc723-d605-4c1a-8045-c3c7741f074e)

Hacemos fuerza bruta on gobuster y vemos que en el directorio /core/install.php hay la versión exacta de la web.

![image](https://github.com/user-attachments/assets/27a62903-844d-4aa0-ba8f-980da174066d)

Hacemos uso de la herramienta metasploit.

![image](https://github.com/user-attachments/assets/ff39b3b1-ea07-47d1-83d5-0caee7b3d42c)

Nos metemos en el primero, en el de RCE, y vemos que encontramos.

![image](https://github.com/user-attachments/assets/5a73692f-ae31-4570-b069-8f4abfebad54)

Abrimos el metasploit con msfconsole y buscamos por drupal.

![image](https://github.com/user-attachments/assets/3ec5a1f7-4f77-4aad-9429-ed66de50610c)

Vemos que el numero 0 es el RCE, pero lo probamos y no funciona, por tanto vamos a probar el siguiente que es el numero 1.

![image](https://github.com/user-attachments/assets/17ec05b9-6cc6-4d00-9f17-f835395f6a3e)

Ahora haremos un "set RHOSTS" para seleccionar la máquina víctima.

![image](https://github.com/user-attachments/assets/055bd3e8-c2b4-4a5b-97f2-3c11440a8bad)

Una vez hecho esto usaremos el comando run para ejecutarlo, y podemos ver como ya estamos dentro y somos el usuario meterpreter.

![image](https://github.com/user-attachments/assets/15057073-cf0f-4125-9019-2d5b0d5815d1)

Hacemos una reverse shell para poder manipular la consola de una manera más fácil.

![image](https://github.com/user-attachments/assets/1ac7af57-4476-4b9b-aa97-df8618e54ad2)

Hacemos una busqueda del archivo settings.php el cual es un archivo en Drupal de configuracion que contiene ajustes esenciales para el funcionamiento del sitio web y en el cual podemos encontrar credenciales.

En el hacemos un grep de ballenita, ya que hemos hido al directorio home y hemos visto que es el único usuario que existe.

![image](https://github.com/user-attachments/assets/064b16c7-b1e3-4235-b48a-2fd4dbd76d01)

![image](https://github.com/user-attachments/assets/464f3c4c-f723-4624-8597-3bfefd6a3d31)

Sabiendo estas credenciales ahora nos intentaremos conectar como usuario ballenita.

![image](https://github.com/user-attachments/assets/654131bb-9ce2-415e-bdbb-7eb2e0020080)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/5fcee20e-28a5-4ce1-9240-b0e6ea4126e8)

Haremos uso del comando ls para saber que hay dentro del directorio /root.

![image](https://github.com/user-attachments/assets/af9ecbd6-4636-4a4a-900d-415657f91710)

Ahora haremos un grep para ver que dentro del archivo que hemos encontrado.

![image](https://github.com/user-attachments/assets/a19e24d7-3ebe-48e9-9454-2c558846fbf5)

Sabiendo esta contraseña vamos a intentar conectarnos como root.

Y ya somos root.

![image](https://github.com/user-attachments/assets/88c7a7c8-695f-4784-b0d1-bd8d2aa5d7a5)

















