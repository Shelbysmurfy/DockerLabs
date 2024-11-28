# RESOLUCIÓN DE LA MÁQUINA CONSOLELOG

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/5334c2fd-4277-45a2-9cb4-7442db509390)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/4e2ae5c1-3d2f-492b-9e16-7be5757d491f)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/001e1a62-3996-40bd-a35a-fce28d4df3da)

Entramos en la web.

![image](https://github.com/user-attachments/assets/9b55e046-7ae8-4e37-b016-27e05304fceb)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/e02569b0-965e-431b-ba10-594f8d7a1824)

Entramos en el directorio /backend/

![image](https://github.com/user-attachments/assets/2c64f0f0-1fcc-4e98-b17f-ff95e8b4e7ea)

Y dentro de este abrimos el server.js

Este nos da un token y una posible contraseña.

![image](https://github.com/user-attachments/assets/0a7a945f-bb63-48c7-ad2d-2a74fbbf33ac)

Hacemos uso de la herramienta hydra, para sacar el usuario de la contraseña que ya tenemos.

![image](https://github.com/user-attachments/assets/a316db06-808f-42af-a258-0cc03e99c5d6)

Ahora entraremos con el servicio, pero haciendo uso de el puerto 5000, como hemos hecho antes en el hydra.

![image](https://github.com/user-attachments/assets/e272d8f3-0ad7-4573-b33e-b3886ce4e847)

Hago sudo -l y me sale esto: 

![image](https://github.com/user-attachments/assets/88905218-53a7-4a36-8b75-0dead872d90c)

Nos vamos al GTFObins y seguimos los pasos que nos dice, para ello antes tendremos que ejecutar este comando, ya que tenemos un problema con la kitty.

![image](https://github.com/user-attachments/assets/203d823e-a3c4-419b-95fe-d5a4f5f2697f)

![image](https://github.com/user-attachments/assets/f1506a46-2b3c-403d-9f28-e8fcf1b78d40)

Y ya somos root.

![image](https://github.com/user-attachments/assets/bf30601a-9897-4c20-8c29-b8af7808660c)






