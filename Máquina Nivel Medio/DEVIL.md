# RESOLUCIÓN DE LA MÁQUINA DEVIL

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/ca3be0ff-7e5c-4e00-8b3a-e27a46727e84)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6036ac38-70ec-46f6-bada-b0c7c4cef616)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/c77f27fb-0c5c-4a4f-a7da-cab1ccb119d5)

Abrimos la web.

![image](https://github.com/user-attachments/assets/25b36301-9ff2-42d3-9078-0eebeafc15b1)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/b5fa5994-d501-4d7c-aace-55738e8834d4)

Nos menciona un dominio "devil.lab", así que vamos a meterlo en el /etc/hosts.

![image](https://github.com/user-attachments/assets/4c32c454-00df-4d43-97e7-46b4a49e5443)

De todos los dircetorios que hemos encontrado cuando hemos hecho gobuster, el único de wordpress que funciona es el wp-content, pero no muestra nada, así que vamos a volver a hacer gobuster pero con la ruta entera.

![image](https://github.com/user-attachments/assets/a01771fa-0c59-42e3-bf19-9ee0457b08dc)

![image](https://github.com/user-attachments/assets/de02b74f-8ce6-4388-bd2e-079499985534)

En /uploads encontramos un archivo curioso.

![image](https://github.com/user-attachments/assets/9753e9b3-cb90-4cfd-ad62-6d084dc1e9b7)

Entramos y encontramos un archivo.txt con un código cifrado.

![image](https://github.com/user-attachments/assets/548ea62e-b582-4de9-addf-0a1bd35a778f)

![image](https://github.com/user-attachments/assets/b03f5ddb-9e76-44c4-bdab-30604be26690)

Desciframos el mensaje que esconde.

MENSAJE: MEJOR PRUEBA HA HACER FUZING PERO NO EN ESTE DIRECTORIO PRUEBA CON UN DIRECTORIO ATRAS.

![image](https://github.com/user-attachments/assets/f2addeeb-d9a3-4c26-8d2f-174b893b0164)

Después de estar un buen rato probando diferentes directorios, ya que la pista no se a cual se refería, encontramos que el directorio /plugins, puede contener lo que buscábamos.

![image](https://github.com/user-attachments/assets/94fb8825-a42e-4fb5-a52b-46fe136f97b8)

Y efectivamente, al ingresar /bakdoor, tenemos una subida de archivos.

![image](https://github.com/user-attachments/assets/7674dbd2-a53c-46bd-a25d-1c95e369d5cc)

Subimos un archivo.php malicioso.

![image](https://github.com/user-attachments/assets/b9d52ed6-d654-4770-9a70-337dc3050cd0)

Pero como no sabemos donde se ha subido, vamos a hacer fuerza bruta del directorio actual para ver si hay algun uploads, y lo encontramos.

![image](https://github.com/user-attachments/assets/f0916427-a6ad-42aa-acf1-2fd10703a2e4)

Nos metemos y vemos nuestro archivo malicioso.

![image](https://github.com/user-attachments/assets/050099c0-8e47-4cbd-a883-b6531cdabfde)

Comprobamos que podemos inyectar comandos correctamente.

![image](https://github.com/user-attachments/assets/f7f5ff3e-ea6a-4feb-8ccc-d17c3fc67838)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/2a9b3486-8634-49dc-858f-383c2640be6b)

Nos vamos al directorio /home y encontramos el usuario andy que tiene una password cifrada, pero no sabemos en que esta cifrada.

![image](https://github.com/user-attachments/assets/bef6ebd5-b36d-4c04-81a2-598e1a1af4c3)

Si hacemos un ls -la, un directorio mas para atrás encontramos un archivo llamado pista.txt, que tiene un texto cifrado.

![image](https://github.com/user-attachments/assets/461c4bab-9b11-4bdd-a198-29c24413b2df)

Nos vamos a cybverchef para descifrarlo.

![image](https://github.com/user-attachments/assets/d3e41251-001a-4b74-9994-faa22ab0b3fb)

Vemos que el contenido es rot8000, así que vamos a intentar descifrar el contenido de antes con esto, pero seguimos sin obtener nada.

![image](https://github.com/user-attachments/assets/b11ba83e-88e1-4373-a093-8dadbc358d96)

Antes también podíamos ver un directorio llamado secret que contiene un archivo llamado escalate.c con este contenido: 

![image](https://github.com/user-attachments/assets/5616cf39-c9e5-4fab-8c89-89471f2dee5e)

Nos dice que el script cambia el UID y el EUID al de lucas actual (1001), y de esta manera invoca una shell con sus privilegios.

Sabiendo esto ejecutamos el script, y nos convertimos en lucas.

![image](https://github.com/user-attachments/assets/5dc0487d-5c2b-4f60-902e-51943e557998)

Nos vamos al directorio de /home/lucas y vemos un archivo con una pista.

![image](https://github.com/user-attachments/assets/b194c685-9752-4228-917a-f73b20675ec1)

Encontramos ese juego del que hablaba.

![image](https://github.com/user-attachments/assets/537383f7-fdf1-4806-a065-960a4550d974)

Entramos al directorio y vemos dos archivos, uno de ellos parece ser un script y el otro si lo abrimos nos muestra esto: 

![image](https://github.com/user-attachments/assets/2e0d4579-3727-4e80-b045-882b3b9cb3a3)

Nos dice que el número correcto es el 7, y que si lo indicamos cuando nos lo pregunte nos invocará una shell como usuario root.

Ejecutamos el script y nos convertimos en root.

![image](https://github.com/user-attachments/assets/2fe95a58-a10f-493e-91ff-5cf0afa642e8)



