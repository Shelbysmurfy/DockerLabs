# RESOLUCIÓN DE LA MÁQUINA LITTLEPIVOTING

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/899ff52b-c0cd-4018-9d78-8f4c058fc04e)

Hacemos un arp-scan sobre la IP 10.10.10.1/24

![image](https://github.com/user-attachments/assets/bd4a7504-a446-42bb-9f6e-eff21065ee65)

De esta manera vemos a que máquina tenemos acceso.

![image](https://github.com/user-attachments/assets/44a81862-a972-40bd-96dc-a602f4e96149)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/13b1e41c-fa33-42f5-975a-151a32592ddb)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/87ba7d37-a1cd-4d6b-8218-7426487afb53)

Abrimos la web y vemos una subida de archivos.

![image](https://github.com/user-attachments/assets/4ec5bb2c-ee41-4a41-8e00-8f8adf614719)

Subimos un archivo malicioso.

![image](https://github.com/user-attachments/assets/3f90306f-886b-45a6-a717-5199aacaff7c)

Nos vamos al directorio /uploads, lo abrimos y vemos que podemos ejecutar comandos correctamente.

![image](https://github.com/user-attachments/assets/c1949d88-5365-4ceb-92e7-b4e73eb8f6e0)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/10ac144b-7fc6-4ba8-8b9a-0b25b54445b0)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/d28ba933-6def-4b5e-aa6f-f2c62c774c0c)

Y ya somos root.

![image](https://github.com/user-attachments/assets/050c7b51-03d7-4579-add6-7b5e4aef6f5b)

Hacemos hostname -i y vemos otra IP de otra máquina.

![image](https://github.com/user-attachments/assets/bc3421bd-c36a-4065-9541-ac1776bd7081)

Nos vamos a nuestra máquina, nos habrimos un servidor con python, y nos traemos la herramienta chisel a nuestra máquina víctima.

![image](https://github.com/user-attachments/assets/b163ed7c-c656-4d69-b736-c995000d6cb0)

Desde la máquina atacante indicamos chisel como un servidpr con un túnel inverso.

![image](https://github.com/user-attachments/assets/e37a95f4-92a8-4b64-86ea-bc675fcafcd6)

Y desde la máquina víctima indicamos chisel como client, junto a la direccción del servidor y el puerto que hemos puesto en escucha antes.

![image](https://github.com/user-attachments/assets/b506944f-68d4-407c-8317-162caa9d4a97)

De esta manera habremos crado un túnel de una máquina a otra que corre por el puerto 9090.

![image](https://github.com/user-attachments/assets/f388569a-35a0-4866-a5f1-556bf29eb3ed)

Nos vamos al archivo proxychains y hacemos 3 cosas: 

![image](https://github.com/user-attachments/assets/44376d10-8920-4252-8472-fd64d9283e1c)

![image](https://github.com/user-attachments/assets/967e7321-4a1f-439e-9da2-e56564ea440e)

Esto le indica a proxychains que utilice un proxy SOCKS5 en 127.0.0.1 (localhost) y en el puerto 9090, que es donde chisel está escuchando.

![image](https://github.com/user-attachments/assets/4986ff66-1090-41e8-b9e5-fc9deb61ca6a)

Y ahora hacemos uso de proxychains para hacer un nmap pero no nos funciona.

![image](https://github.com/user-attachments/assets/20d51f65-8267-4e70-b241-a4bf5b5a943e)

LLevo mucho rato intentando cosas y mirando writeups pero no encuentro la solución.

Esta máquina solo se trata de esto, las tres máquinas a resolver ya las he hecho y son muy sencillas.

