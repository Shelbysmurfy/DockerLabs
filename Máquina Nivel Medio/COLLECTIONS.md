# RESOLUCIÓN DE LA MÁQUINA COLLECTIONS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/b53c46ee-14ef-42fd-9b5d-596599d9ab7e)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/3f40bf9e-b830-46b4-82c9-99cb269f6b55)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/5c80ad31-2edc-4019-ba6c-7ad0a0596c0a)
![image](https://github.com/user-attachments/assets/4021bfc5-a47d-4970-bc10-75b8d0ee657c)

Abrimos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/57cd1afe-6d48-45b4-847f-a4fc5d6597fd)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/03358587-50d0-4bbc-b7eb-0d9daf31b135)

Abrimos el wordpress y vemos esto: 

![image](https://github.com/user-attachments/assets/eb795da9-e3af-4626-bc5a-acf8db7f448d)

Volvemos a hacer gobuster.

![image](https://github.com/user-attachments/assets/7763a3e6-fde7-4586-9527-15305e14b912)

En la web encontramos un posible usuario.

![image](https://github.com/user-attachments/assets/2d8c0a01-9094-4edf-b8b0-b7ee51810970)

Descubrimos su contraseña con wpscan.

![image](https://github.com/user-attachments/assets/4bb15f08-88f4-486a-9092-0bdc763ee554)

![image](https://github.com/user-attachments/assets/f231d3ea-c37b-44e9-acbe-815488dde695)

Nos conectamos al wordpress con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/1940bc89-9da5-4353-9842-51b8440d0256)

No vemos nada, hacemos hydra también al usuario chocolate para el servicio ssh, y nos devuelve esto: 

![image](https://github.com/user-attachments/assets/d642162d-9ba0-4903-b797-e348a9d9e534)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/d83597b8-cbd8-4ba0-b8c2-5922c12bbb66)

Hacemos ls en el directorio raiz y vemos un archivo interesante.

![image](https://github.com/user-attachments/assets/44783e92-3661-4da0-88a4-dae34046f98a)

Nos lo intentamos pasar con scp, ya que hemos visto que esta disponible pero no me deja.

![image](https://github.com/user-attachments/assets/7ba4461e-2cb6-4da7-a950-b6771b24c67b)

Nos vamos al directorio /tmp, vemos un archivo, y al ejecutar ps -e -f, observamos que el proceso mongod está ejecutándose con la opción –bind_ip_all, lo que significa que está escuchando en todas las interfaces de red. Esto es un riesgo de seguridad.

![image](https://github.com/user-attachments/assets/faf4de74-4007-48fb-b188-8c29c54763c8)

Así que vamos a intentar conectarnos a MongoDB.

Para ello he tenido que crear un docker ya que he tenido problemas para instalarlo.

![image](https://github.com/user-attachments/assets/4705c3ff-906b-43b7-8216-893691d6f9e4)

![image](https://github.com/user-attachments/assets/cea9272c-1a40-4188-b5f3-c31e5f63d01c)

Y finalmente nos podemos conectar.

![image](https://github.com/user-attachments/assets/05ef841e-69be-4199-af90-b24ea57b7bf6)

Encontramos unas posibles credenciales.

![image](https://github.com/user-attachments/assets/a7110b26-fa5f-4b5e-8d17-1948fd03d759)

Nos conectamos con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/865e307d-4930-4fa7-a6f1-56035480b471)

Como no encontramos nada, intentamos usar las misma credencial para el usuario root, y escalamos privilegios.

![image](https://github.com/user-attachments/assets/ef482d94-c3d6-4c45-8526-e9b1332ab5f3)
