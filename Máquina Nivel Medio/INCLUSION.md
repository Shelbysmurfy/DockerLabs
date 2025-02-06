# RESOLUCIÓN DE LA MÁQUINA INCLUSION

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/4ca0cddd-0f50-4b75-ad47-ee0c8d080433)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/f2205e91-6509-412c-a6f5-e671ac15daf6)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/269508f8-4051-441f-aa8a-26d4e776fd43)

Abrimos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/9766e3f3-5212-4b9f-8ccc-27c2b3473ae3)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/f30187b9-aabf-43ed-b32c-4a78f2cdedec)

Nos metemos en el directorio /shop y vemos esto: 

![image](https://github.com/user-attachments/assets/679860d8-78e2-4319-b365-6c5079bbc27c)

Al ver ese error podemos saber que muy provablemente podamos hacer LFI.

Hacemos uso de la herramienta wfuzz para ver si hay algun parámetro que me permita ejecutar comandos, y coincide con el que nos mostraba la web.

![image](https://github.com/user-attachments/assets/ae05bfdb-26eb-40f4-a41a-fe9bfac593e4)

Hacemos un /etc/passwd y podemos ver varios usuarios (seller, manchi).

![image](https://github.com/user-attachments/assets/de721765-1252-4a8e-a318-7070a4b998d1)

Hacemos un hydra para los usuarios existentes que hemos visto con el /etc/passwd y sacamos unas credenciales.

![image](https://github.com/user-attachments/assets/bae6e667-6157-4ca4-97e7-9aaf145e62d8)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/5ed2c6ed-3cca-4eeb-84c0-b851fb62d4af)

Como no encontramos nada, nos transferimos un script para hecer fuerza bruta en busca de la contraseña del usuario seller.

Para ello necesitaremos este script y el diccionario rockyou, nos los pasamos con scp, wget y curl no podemos.

![image](https://github.com/user-attachments/assets/1bbd5e0c-c271-42ad-a2b9-e36d587b1422)

![image](https://github.com/user-attachments/assets/fda2ff2a-ee25-478f-8b0d-63f8808d061f)

Le damos permisos al suForce, lo ejecutamos y encontramos estas credenciales:

![image](https://github.com/user-attachments/assets/28350db5-3315-4b8d-a661-3f85bb5305f4)

Nos conectamos con las nuevas credenciales.

![image](https://github.com/user-attachments/assets/284157ab-6960-43ea-948a-c571463fb5a9)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/8d2c170f-b309-4f1b-9e19-c9dd6cea69df)

Y ya somos root.

![image](https://github.com/user-attachments/assets/44c2ef7f-ead6-4f26-9d75-7acad5bba16b)
