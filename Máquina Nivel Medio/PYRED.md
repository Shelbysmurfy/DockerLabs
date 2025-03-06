# RESOLUCIÓN DE LA MÁQUINA PYRED

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/f977db0c-f1f7-4ea5-9f3e-2b92df32b631)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/1952d0ee-5682-4713-b3e5-417e52b1c72c)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/fe5a32e3-1218-407c-8aa5-8ed17682a27a)

Abrimos la web.

![image](https://github.com/user-attachments/assets/dad1f02f-6ca6-49e8-a598-59ca4661a3e1)

Intentamos hacer una reverse shell de inicio con python y nos deja pero seguidamente nos saca.

![image](https://github.com/user-attachments/assets/57d82602-35ca-4aa1-be71-b244f2ccff88)

![image](https://github.com/user-attachments/assets/751dcfda-d3b4-4a36-8ab3-393f47640fcb)

Nos volvemos a enviar una reverse shell, pero esta vez una bash -i, pero de esta manera: 

![image](https://github.com/user-attachments/assets/b0d8b126-24c1-4124-b467-76714e021b3a)

Y ganamos acceso a la máquina víctima.

![image](https://github.com/user-attachments/assets/62e59965-e1bc-400a-b6cc-1d8b7ffad3f9)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/53fc1998-14d2-4571-9d4c-9df0f0c14562)

NO PUEDO INSTALAR EL FPM, PASOS QUE DEBERÍA SEGUIR: 

Nos vamos a nuestra máquina y seguimos los pasos del GTFObins para poder escalar privilegios.

![image](https://github.com/user-attachments/assets/153fd96a-6358-4f39-b0a3-dc4bbe0cb5e4)

![image](https://github.com/user-attachments/assets/cc40a67a-dc53-4deb-a812-d7b4cce9f243)

Nos abrimos un servidor con python, y con wget nos traemos el archivo a nuestra máquina víctima.

![image](https://github.com/user-attachments/assets/c23ff83a-896c-4a34-b943-6743679f3ffa)

![image](https://github.com/user-attachments/assets/5bde7644-f535-4363-a837-7ccb6b68f519)

Seguidamente hacemos el último paso que es instalar el paquete maliciosos que hemos creado con dnf.

![image](https://github.com/user-attachments/assets/2d7da503-ef67-4540-8a0f-fabeb4f18cac)

Y si ejecutamos bash -p ya seríamos usuario root.

![image](https://github.com/user-attachments/assets/58dad038-6ca3-4e8d-acdc-a4ab8413d27d)
