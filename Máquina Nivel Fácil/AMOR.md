# RESOLUCIÓN DE LA MÁQUINA AMOR

![image](https://github.com/user-attachments/assets/33d8470c-0414-4bcb-b1b1-dc0c3548b845)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/f9c8dbc1-b5ea-4504-b896-1333cf21ea59)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/aaaeed9a-dc0f-42e9-9125-4dd73cd448d1)

Abrimos la web y nos encontramos con esta información: 

![image](https://github.com/user-attachments/assets/ca066b71-5052-4721-9bbd-75e702ce3996)

Hacemos hydra para el usuario carlota y nos devuelve su contraseña.

![image](https://github.com/user-attachments/assets/4b1eb0c1-619d-483b-9b84-049e25aa115c)

Entramos con el servicio ssh.

![image](https://github.com/user-attachments/assets/e2caaf39-7702-47c3-8ad3-f331a231f7e5)

Nos encontramos una imagen y la traemos a nuestro equipo. Hacemos steghide y obtenemos un txt.

![image](https://github.com/user-attachments/assets/8711b60e-46ec-4bcb-95d0-b09f91c6f140)

Dentro hay un código en base64, lo decodeamos y sacamos una posible contraseña.

![image](https://github.com/user-attachments/assets/0f1df00d-3783-479e-b0f3-281b0720b025)

En el directorio home del servicio ssh hay otro usuario oscar, probamos de usar esta contraseña con el y conseguimos acceso.

![image](https://github.com/user-attachments/assets/653fef3f-74ce-4039-b0cd-dea89d22930f)

Hacemos sudo -l.

![image](https://github.com/user-attachments/assets/e90181ac-f162-4a16-aac8-c7388f6ca333)

Conseguimos acceso como root.

![image](https://github.com/user-attachments/assets/2479a3cb-57e6-4197-86be-d3299ac174d9)





