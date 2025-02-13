# RESOLUCIÓN DE LA MÁQUINA 0xc0ffe

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/126406bb-5389-4a91-bd61-9e59c33fe03b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/7ce439af-b240-48a8-824b-62145c0307e2)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/5e929141-6b17-423e-9df1-8cde5d2312e5)

Entramos en la web.

![image](https://github.com/user-attachments/assets/15b8097a-41e3-431b-9d22-2cb7dea5dbd6)

Como no podemos entrar vamos a el puerto 7777, a ver si podemos encontrar información relevante.h

![image](https://github.com/user-attachments/assets/fdd9edef-0656-4094-b25d-f1c9af179f9b)

Y efectivamente, en secret/history.txt, vemos esto: 

![image](https://github.com/user-attachments/assets/66bd5b91-52d1-450a-a4b5-14fbe06acc95)

Nos conectamos con la clave "super_secure_password", que esta varias veces mencionada en el archivo.

![image](https://github.com/user-attachments/assets/e242dd65-ae60-4bb0-a0d6-dc9dc718354a)

![image](https://github.com/user-attachments/assets/e59b52cd-027b-4cbf-9dbb-caa8c14e3d7b)

Creamos un archivo hola, que se nos guarda en el puerto 7777.

![image](https://github.com/user-attachments/assets/83b45fce-e21a-46f7-ba8b-a2d5c015e52d)

![image](https://github.com/user-attachments/assets/e1046d34-a50a-4f91-a5ec-fe053a222aff)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/7a677945-03f3-432b-89ec-8e1f2d53bb49)

![image](https://github.com/user-attachments/assets/20ff6bc9-3407-4673-9e21-50fcfcc0b067)

![image](https://github.com/user-attachments/assets/b9b2a855-fe34-4461-9242-bc99b98a550f)

Encontramos una adivinanza que hace referencia a "un troyano".

![image](https://github.com/user-attachments/assets/3f629b97-700b-4a55-a4df-02cd01c44f49)

Nos intentamos conectar al usuario codebad o metadata con la contraseña troyano pero no nos deja.

También suponemos que en vez de hacer referencia a un troyano, puede hacer refencia a algun tipo de malware, intentamos poniendo esto como contraseña y conseguimos ganara acceso.

credenciales --> codebad:malware

![image](https://github.com/user-attachments/assets/507c99d8-70f2-48db-8a0d-1d1eabb3c859)

Hacemos un sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/1ac2b515-6dcf-4025-ab68-d200a4c128d3)

Intentamos diferentes comandos para poder ver el contenido de algo y encontrar alguna credencial pero no podemos.

![image](https://github.com/user-attachments/assets/ec6d5763-d0eb-4edd-bb56-001f46a82e9e)

Como el binario /code, ejecuta comandos usando la función system(), que es vulnerable a inyeccion de comandos, le hemos preguntado al chatgpt que podíamos hacer y nos ha dado esta opción: 

![image](https://github.com/user-attachments/assets/24ece4ad-696c-46e8-94d4-afa5b893c7af)

![image](https://github.com/user-attachments/assets/acbfc79e-8fa8-41ba-8f4d-5497ffd05461)

Y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/1bfbea3f-32ef-47e3-bc5a-f7d051c6d344)

Realizamos una búsqueda de archivos para metadata y encontramos varias carpetas.

![image](https://github.com/user-attachments/assets/d9ff0e11-98e8-4aca-b34f-f8b6aa6d3fd4)

Nos metemos en la carpeta /usr/local/bin, y encontramos un archivo llamado metadatosmalos.

![image](https://github.com/user-attachments/assets/310a65f6-1969-4a69-b533-48e25dc61f5c)

Probamos a hacer un sudo -l y poniendo el nombre del archivo que hemos encontrado como password y ganamos acceso.

![image](https://github.com/user-attachments/assets/96eefa1b-944a-4bda-8e7a-38d7235c21d0)

Y ya somos root.

![image](https://github.com/user-attachments/assets/afb8c94e-d98a-4d78-b97e-76e12969d19b)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/33575f9c-e8df-4ce3-acd8-989e77f90087)

