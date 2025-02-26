# RESOLUCIÓN DE LA MÁQUINA MEMESPLOIT

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/a428dd4a-fc37-4be0-91b2-53e10c8000e2)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/93e15835-286e-4f32-8ea9-580ae50f81d7)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/0cd1b400-a81d-4fc1-8051-3c1f86ee97cb)

Abrimos la web.

![image](https://github.com/user-attachments/assets/6fecea8c-c210-4852-95b9-bfc354c247e8)

En elñ código fuente nos encontramos tres cosas que nos estaban ocultando en la página pero que aquí podemos verlas.

![image](https://github.com/user-attachments/assets/a9942985-bf74-487a-878f-0aaefe6ae0f2)

Hacemos uso de la herramienta enum4linux en busca de posibles recursos compartidos, usuarios...

![image](https://github.com/user-attachments/assets/581446fb-8ad6-4ca8-8ccb-a46bacce40b7)

![image](https://github.com/user-attachments/assets/cc452b04-2492-477f-8e34-e302f2fa307e)

Encontramos dos usuarios que coinciden con lo que hemos visto en el código fuente de la página web (memesploit, memehydra)

![image](https://github.com/user-attachments/assets/e88dbd3a-68bf-49c2-a749-7456e81a826d)

Intentamos hacer fuerza bruta para los dos usuarios y no conseguimos nada.

Intentamos usar como usuario "memehydra" y contraseña "fuerzabruta", que es lo que hemos visto antes en el código fuente y nos funciona.

Nos conectamos al recurso compartido "share_memehydra", con smbclient y las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/fe597efa-a33a-4203-a460-c3f12d0ceeb8)

Nos traemos el archivo.zip a nuestra máquina.

![image](https://github.com/user-attachments/assets/00c6a6f5-0cad-4f87-9bcc-664ebe76d958)

Con zip2john vamos a obtener el hash, y con john lo vamos a romper con el rockyou, para obtener el txt. Pero parece que no funciona.

![image](https://github.com/user-attachments/assets/4636f218-7ffd-4ca6-a474-17906e237470)

Después de un buen rato intentando cosas volvemos a usar alguna de las tres cosas que habíamos visto en el código fuente de la página web y la que funciona es "memesploit_ctf".

![image](https://github.com/user-attachments/assets/f99129af-1974-45ad-9133-7d32e69f8f17)

En el archivo.txt encontramos unas posibles credenciales "memesploit:metasploitelmejor"

![image](https://github.com/user-attachments/assets/da5c78bd-0cef-4a62-9444-e3fb8ad6ba4a)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/6e47001b-3a5e-4007-a105-7d277905d83c)

Encontramos la primera flag, la del user.txt

![image](https://github.com/user-attachments/assets/0e792ff1-5557-465d-b34d-062ee7192654)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/147e6571-ec9f-4815-afbb-ed5ebe6c3874)

No podemos escalar privilegios desde aquí, vamos a ir al directorio login_monitor, para ver que hay.
![image](https://github.com/user-attachments/assets/02203d24-68ad-427a-8f3a-c72f81e0c30a)

El archivo actionban.sh simula un bloqueo.

![image](https://github.com/user-attachments/assets/9aa16b2d-0c96-41d4-8431-af54f1d9ee7a)

![image](https://github.com/user-attachments/assets/1ba3e886-39cd-4a73-a8fd-d6df4e38881f)

Nos abrimos el archivo y añadimos un "chmod u+s /bin/bash", al final del archivo para que cuando se ejecute escale privilegios automáticamente.

Pare ello tendremos que borrar el archivo existente y crear otro igual, ya que no nos deja editarlo.

![image](https://github.com/user-attachments/assets/6b639f92-4a66-4835-8cfe-9ca4ec6adc53)

Ahora para que esto funcione tendremos que darle permisos de ejecución al archivo y iniciar otra vez el servicio ssh.

![image](https://github.com/user-attachments/assets/0c974ec4-edd0-4318-a02f-0c676565850c)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/86f38c4f-4ba9-41bf-8208-7f2057dc1d84)

