# RESOLUCIÓN DE LA MÁQUINA VULNERAME

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/256ee7fd-6d3d-46df-94b1-e866b1f4836c)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/0da05f66-139c-40ed-90c1-36823daed037)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/913afccb-c750-4cb1-ac3d-ba3a5682543b)

Miramos la web y no vemos nada.

![image](https://github.com/user-attachments/assets/2dccdc73-1516-46c5-9e43-8a170a4994ce)

Nos vamos al puerto 3306 y vemos esto: 

![image](https://github.com/user-attachments/assets/b0b876ba-59d6-4f02-b0a0-646a22a8c1ba)

Como no sabemos que hacer con esto vamos a hacer fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/b4488a08-71a9-4479-aa2e-25a18ba55792)

Vamos al directorio /wordpress

![image](https://github.com/user-attachments/assets/63b91703-0775-4c12-955a-98b9c7a689a2)

En este encontramos un posible usuario.

![image](https://github.com/user-attachments/assets/a949d700-3cd6-4624-ac39-db19d0a4a49c)

Volvemos a hacer un gobuster, pero esta vez añadiendo el directorio /wordpress a la ruta.

![image](https://github.com/user-attachments/assets/84eb662f-d74c-400b-bdd3-661f85f3364a)

En el directorio /administrator tenemos un login, pero no conseguimos loguearnos.

![image](https://github.com/user-attachments/assets/529fce7b-04ed-46aa-a2df-5fe9f457ef73)

Miramos en hacktricks y vemos donde podemos encontrar la versión de el joomla, y entonces poder ver si podemos vulnerarla.

hacktricks: https://book.hacktricks.wiki/en/network-services-pentesting/pentesting-web/joomla.html

![image](https://github.com/user-attachments/assets/cf383e25-0cf1-456a-9f1c-29e1b7b3c2e7)

Nos metemos y vemos la versión 4.0.3

![image](https://github.com/user-attachments/assets/6a4b34ad-09d8-465c-a1d6-efdbaf6659c7)

En esa misma página del hacktricks vemos esto: 

![image](https://github.com/user-attachments/assets/c64e86dd-ba63-42e3-8fe5-f6eba78f28e6)

Y como la versión de nuestro joomla esta en el intérvalo que nos dan vamos a usar lo que nos dicen, una de ella nos funciona.

En esta encontramos unas posibles credenciales "joomla_user:vuln" y una base de datos "joomla_db".

![image](https://github.com/user-attachments/assets/047c4600-c2f8-401f-a343-01c68727643f)

Nos conectamos a la base de datos con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/1fc88a48-97c8-4706-be3d-1c0d8ad6e8c1)

Miramos las bases de datos que hay.

![image](https://github.com/user-attachments/assets/9c05adb9-c0b1-4c73-8193-6379639928cc)

Seleccionamos la base de datos "joomla_db", y miramos las tablas de esta.

![image](https://github.com/user-attachments/assets/1594d963-c72d-40f8-aeab-8f456880b634)

Encontramos varias tablas relacionadas con usuarios.

![image](https://github.com/user-attachments/assets/05e8946e-2caf-4dbd-9738-043a32108f70)

En la tabla "ffsnq_users" podemos encontrar unas credenciales.

![image](https://github.com/user-attachments/assets/6badaaeb-cf23-4da0-abb4-4c779e5f7071)

Tenemos un hash, nos lo guardamos en un archivo y lo explotamos con john.

![image](https://github.com/user-attachments/assets/7a4a71b4-3b4e-48e9-85da-04a7d80e697d)

Nos conectamos en el login de joomla con las credenciales obtenidas "firstatack:tequieromucho".

![image](https://github.com/user-attachments/assets/3f5bd891-41f9-40a1-84ab-edca1b9567a7)

Una vez dentro vamos a System y vemos todo esto: 

![image](https://github.com/user-attachments/assets/8bb416d4-5054-46fc-ab58-19a18f3541d5)

Tenemos que ir a "Site Templates" y luego darle a "Cassiopeia Details and Files", entonces veremos diferentes archivos.php donde podremos añadir código malicioso.

![image](https://github.com/user-attachments/assets/92217b17-0409-472d-9b8c-0a9aefb97fda)

Usaremos el index.php ya que es el único que anteriormente al hacer gobuster hemos visto.

![image](https://github.com/user-attachments/assets/76b261b5-444d-4360-903e-0c4ee9d3dc56)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/dfe345f4-c384-49b7-969d-32ca04d397bf)

![image](https://github.com/user-attachments/assets/952553cf-c778-4c59-a616-39308e334d6e)

En el directorio home encontramos dos usuarios, en uno de ellos encontramos una contraseña que está codificada en base64.

![image](https://github.com/user-attachments/assets/9f849d94-2def-4411-93d4-94525283f314)

Lo decodeamos pero no nos sirve para nada.

![image](https://github.com/user-attachments/assets/555fa65d-f1f5-4697-a38d-749f7aae4108)

Vamos a hacer fuerza bruta con hydra para los dos usuarios y a ver si encontramos algunas credenciales válidas.

![image](https://github.com/user-attachments/assets/39d2d1bb-8ca8-4bdf-be54-365d52312ef1)

Nos conectamos al servicio ssh con las credenciales obtenidas "ignacio:gateway".

![image](https://github.com/user-attachments/assets/d726436d-05db-4bc0-9eca-4c3d40c7f6fa)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/90146485-87f2-4780-982c-986d93ca9aa5)

Nos vamos al archivo saludos.rb y le añadimos este código para poder escalar privilegios.

![image](https://github.com/user-attachments/assets/7e48fc92-09fe-476c-8658-4cd53c677cc3)

Y ahora nos guiamos del GTFObins y ejecutamos el permiso SUDO que tenemos junto al archivo.rb y ya somos root.

![image](https://github.com/user-attachments/assets/3191c05a-30ab-40a6-bddd-8deee5e552bd)

