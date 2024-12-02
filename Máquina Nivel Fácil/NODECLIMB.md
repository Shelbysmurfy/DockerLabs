# RESOLUCIÓN DE LA MÁQUINA NODECLIMB

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/d6e10bef-51eb-4709-954a-20f401dee976)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/d37beb9c-993b-40e9-918c-a3ebf687c8dc)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/169faa33-0bf0-42ad-b0ef-34543773881a)

Entramos al servico ftp con el usuario anonymous y nos traemos un .zip a nuestra máquina.

![image](https://github.com/user-attachments/assets/9c5de31c-d08d-4f83-9915-99af0057f23b)

Haremos un zip2john para poder extraer el hash.

![image](https://github.com/user-attachments/assets/9bca167b-5422-4f22-94d6-f386f2635976)

Y ahora con john obtendremos la password del archivo.

![image](https://github.com/user-attachments/assets/e915fa55-4eba-44b3-8e47-34c81efe4743)

Una vez hecho esto, hacemos un unzip del archivo para saber el contenido que hay dentro.

![image](https://github.com/user-attachments/assets/5dcd409f-12f4-46bc-b5c0-1ee2b984433c)

Entramos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/bca8fff8-521b-4660-9c09-05db1156e630)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/97208802-5aeb-48e1-bb4b-cf7560ae56d3)

Nos vamos al directorio /home/mario y abrimos el script.js, y introducimos lo que nos dice el GTFObins.

![image](https://github.com/user-attachments/assets/6cc7068d-eba6-418b-9af8-3042ac2344a1)

Solo hace falta que pongamos el require.

![image](https://github.com/user-attachments/assets/752a855d-019a-483e-b3ce-ebcd8e5b1475)

Y ya somos root.

![image](https://github.com/user-attachments/assets/cf5efad4-9c26-48b7-871c-1a6dbcc82451)



