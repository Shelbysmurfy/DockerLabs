# RESOLUCIÓN DE LA MÁQUINA HACKMEDADDY

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/f34755a7-9f75-4263-a231-23e777024031)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/b9ab29bf-12ab-413d-b676-581c7dc7e0e7)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/ae40384d-3b49-4185-8174-ab1e577258ae)

Abrimos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/589d3883-ce7b-41fd-ae65-7ca49b21eb7f)

Nos metemos en el robots y vemos 3 posibles rutas, pero ninguna de ellas funciona.

![image](https://github.com/user-attachments/assets/b1b0d425-d7ff-4560-af1d-08ed92131cd4)

Vamos a hacer fuerza bruta con gobuster en busca de posibles directorios que nos habiliten lo que hemos visto en el robots.

![image](https://github.com/user-attachments/assets/79281202-9fb0-4774-8593-7cb44d495530)

Encontramos la primera flag en /flag.txt

![image](https://github.com/user-attachments/assets/f5036feb-17f6-430f-9cf3-4da5a6e20a04)

Nos vamos al directorio /info.txt y encontramos esta pista: 

![image](https://github.com/user-attachments/assets/7e9322d3-f830-4db8-92c0-ba04ac49ac50)

Nos vamos al archivo index.html, que lo habíamos visto antes al hacer gobuster y que nos ha mencionado la pista que hemos visto.

![image](https://github.com/user-attachments/assets/2252b814-1d1e-4175-8547-28517e0775c8)

Tenemos un botón de que nos va ejecutando comandos, y si le damos varias veces nos hace un cat del "README.txt".

![image](https://github.com/user-attachments/assets/0ebbdd08-ba58-4a32-81dc-700d81b90cb9)

Miramos el código fuente y podemos ver todos los comandos que se ejecutan y nos muestran en la página.

![image](https://github.com/user-attachments/assets/26adc686-3aba-43c8-827e-14270ee481db)

Intentamos aprovechar la información que nos da el README.txt, y probando cosas vemos que "d05notfound" es un directorio.

Si nos metemos vemos otro archivo igual dentro pero con la extensión php, y este nos muestra esto: 

![image](https://github.com/user-attachments/assets/61fef21f-1491-4597-999a-41d926080f4c)

La única parte de esta web que parece ser funcional es la de Comprobación de Ping.

![image](https://github.com/user-attachments/assets/7f64e3a0-115e-4410-baa7-2adad799be5b)

Cogemos la petición con BurpSuite, y ponemos como comando la IP víctima.

![image](https://github.com/user-attachments/assets/53603e82-3775-432c-b480-ff267080f432)

Al ver que esto funciona, intentamos añadir una pipe y seguidamente un comando y vemos que nos muestra resultado "www-data".

![image](https://github.com/user-attachments/assets/eb18ef04-7b2d-48ff-ad8a-4502fa66c0b8)

Miramos el /etc/passwd y vemos dos usuarios.

![image](https://github.com/user-attachments/assets/20dbf373-0413-499d-ad07-394d2d3666ef)

Intentamos hacer fuerza bruta con hydra para encontrar posibles contraseñas de estos dos usuarios pero no encontramos nada.

Intentamos hacer una reverse shell descargando un archivo php pero no nos deja.

![image](https://github.com/user-attachments/assets/442f7cb7-77c8-4c7d-8c99-1bc81f0e78db)

Probamos descargando un archivo en el directorio /tmp y si podemos.

![image](https://github.com/user-attachments/assets/82d02b9e-5d55-4306-bd5a-1ffaee056983)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/264115eb-c73a-4838-b6f5-9b9dedc1de2b)

![image](https://github.com/user-attachments/assets/5fc80e6f-4263-4668-956f-fd22a831779a)

![image](https://github.com/user-attachments/assets/9bd734fe-b495-4c40-ba20-b725ac5b8139)

![image](https://github.com/user-attachments/assets/1820aeed-8c81-4d16-bd34-e315b8c99a75)

Y nos conectamos correctamente.

![image](https://github.com/user-attachments/assets/436ea680-a445-4556-88ba-0203751628c0)

No vamos al directorio /home y en el usuario eliot encontramos una nota.

![image](https://github.com/user-attachments/assets/0d95af9b-b83d-4199-8220-3e9d646da315)

Sabemos que tenemos un diccioanrio de posibles credenciales, vamos a traernos la herramienta suForce y vamos a hacer fuerza bruta para encontrar posibles contraseñas para el usuario eliot.

![image](https://github.com/user-attachments/assets/43b8665c-ef69-4709-ac48-396e93dabe83)

Encontramos la contraseña del usuario eliot en el diccionario agenda.txt

![image](https://github.com/user-attachments/assets/981da002-68ce-4097-8811-fcc64bb79616)

Nos conectamos al servicio ssh con las credenciales obtenidas "e1i0t:eliotelmejor".

![image](https://github.com/user-attachments/assets/5aa82e58-75da-4473-a10c-c1d62582e92b)

Hacemos ls y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/4918c05a-249a-4978-af53-cc6b52ae1cad)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/e0b6ded1-c544-415c-9a35-78232ef272b5)

Escalamos privilegios correctamente a el usuario anOn1mato.

![image](https://github.com/user-attachments/assets/d3ec7a92-356e-4587-bf08-1489dba5d4ec)

Volvemos a hacer ls y vemos la flag del user2.

![image](https://github.com/user-attachments/assets/c4d71b5e-54e9-4fb1-81b3-79ff7ecbcb9e)

Y si miramos la nota que tenemos encontramos otra pista.

![image](https://github.com/user-attachments/assets/5e6ccbb9-4dda-4b50-baf9-929e71ff8be2)

Vamos a la raiz y vemos el directorio /secret que parece ser que es, de lo que nos hablaba la nota.

![image](https://github.com/user-attachments/assets/ab4f8b74-82c2-4a25-a4ce-9441e0f2aad0)

Buscamos con find donde se encuentra este archivo.

![image](https://github.com/user-attachments/assets/f215064a-28a5-49e7-b7c0-b39466bd15c1)

Y en el encontramos diferentes credenciales.

![image](https://github.com/user-attachments/assets/9706e82f-744b-43bb-a934-6dda5e26dccb)

Probamos a conectarnos como root, pero parece ser que es la que está descatualizada.

Hacemos uso de la herramienta crucnh para crear un diccionario con todas las posibilidades que hay para encontrar las dos primeras letras de "XXyanonymous".

![image](https://github.com/user-attachments/assets/6053ce3c-1654-4819-b0b5-db59968b1df7)

Y ahora hacemos hydra con el usuario "an0n1mat0" y el diccionario que acabamos de crear "passwords.txt".

![image](https://github.com/user-attachments/assets/bd3e0560-436d-438b-a6ee-9dd3ee573288)

Nos conectamos al servicio ssh con las credenciales obtenidas "an0n1mat0:soyanonymous"

![image](https://github.com/user-attachments/assets/077282c9-584f-49dc-ae25-6b0eb68b6d98)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/7b2b100e-d7f4-4648-941f-c3637e801b8e)

Ya somos root.

![image](https://github.com/user-attachments/assets/d65969c2-2933-4a24-917f-1fbeaf21f567)

Y encontramos la flag del usuario root.

![image](https://github.com/user-attachments/assets/c26e049f-00c3-439c-91d7-2abf472d2ff1)


