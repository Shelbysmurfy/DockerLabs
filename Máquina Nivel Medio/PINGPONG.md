# RESOLUCIÓN DE LA MÁQUINA PINGPONG

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/24354e3c-0def-4031-8019-794038fcd1bc)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/03d0fee1-b4c4-4d4a-b7b6-27d66cf7c560)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/9ccee3e7-b4b8-4138-9198-aa0795bd050e)

Abrimos la web puerto 80 y el 443 y no vemos nada.

![image](https://github.com/user-attachments/assets/6729769c-e973-4b95-90bc-d758255123d9)

En el puerto 5000 vemos esto: 

![image](https://github.com/user-attachments/assets/15c5d203-9714-40b7-87c5-d9bba069bfba)

Hacemos fuerza bruta con gobuster tanto para el puerto 80 y el 443, pero vemos lo mismo.

![image](https://github.com/user-attachments/assets/dc834fa0-a631-42e5-85f1-7a5aaeac21a6)

Como no sacamos nada, volvemos al puerto 500 y intentamos inyectar comandos.

Si ponemos la IP o localhost nos devuelve lo mismo, es decir la barra de comandos, acepta tanto letras como números.

![image](https://github.com/user-attachments/assets/5078dac7-15b4-4b2a-8d24-b687c5552249)

Ponemos el comando localhost seguido de "&&", y introducimos otro comando, en este caso /etc/passwd, y satisfactoriamente podemos verlo.

![image](https://github.com/user-attachments/assets/a682a4fd-3d5f-4054-aa13-c0115d5a3d6c)

![image](https://github.com/user-attachments/assets/4746a8c0-d03f-4d3d-97db-f7d53e25b685)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/7fd22147-a377-40a1-97e3-94fe4b3b265c)

![image](https://github.com/user-attachments/assets/a153263e-4252-47b0-9954-7f946c765259)

Hacemos sudo -l y vemos qu7e podemos ejecutar /dpkg con el usuario bobby.

![image](https://github.com/user-attachments/assets/a81283ad-d4a3-47c0-a6b5-0f9c1c1de3fe)

Lo ejecutamos.

![image](https://github.com/user-attachments/assets/49442ea0-b670-414f-8c44-fe0b318d7e78)
![image](https://github.com/user-attachments/assets/a8321143-0c30-45b3-a9b1-cd92c7744f39)

Y nos convertimos en usuario bobby.

![image](https://github.com/user-attachments/assets/7c7de644-734b-446a-a8b8-9054c87f1e31)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/f40b4d47-26ee-4134-9f2d-741bf5f116d4)

Se me queda pillado, no puedo avanzar.

![image](https://github.com/user-attachments/assets/1a30e63c-03a5-4ac5-aefd-c1226b63ca33)

Pero es una máquina facil, todo el rato hacer sudo -l, y guiarte con GTFObins.
