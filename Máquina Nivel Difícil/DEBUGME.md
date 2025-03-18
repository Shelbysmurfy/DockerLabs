# RESOLUCIÓN DE LA MÁQUINA DEBUGME

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/43550753-28dc-42a0-92ec-014133465b51)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/9f348853-e733-4774-a14e-587a11d01847)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/7eae686e-6781-4693-b72a-c5418671327e)

Abrimos la web y vemos una subida de archivos.

![image](https://github.com/user-attachments/assets/b66df8af-7a7b-443d-a525-3d30be9cbe69)

Subimos una imagen, ya que cumple con las extensiones que nos menciona que podemos subir pero no vemos nada interesante.

![image](https://github.com/user-attachments/assets/2b3885ed-0f55-464a-9663-7c27a05870db)

Intentamos subir un archivo malicioso pero no nos deja.

![image](https://github.com/user-attachments/assets/89e6984f-f433-45d2-8814-9a367ea76880)

Capturamos la petición con burpsuite y intentamos si podemos bypassear la extensión, y así poder cargar el código malicioso, pero nos muestra esto: 

![image](https://github.com/user-attachments/assets/389c0b5d-e2d1-4100-81a3-7b90c7ebb2a2)

Buscamos el error y nos habla del "imagick", que hemos buscado información y nos ha mostrado esto: 

![image](https://github.com/user-attachments/assets/aacb99d6-3dd6-4679-a454-41a36b43bce9)

![image](https://github.com/user-attachments/assets/0b930025-ff71-4452-a4ba-eff2bf146867)

Hacemos fuerza bruta con gobuster, utilizando la cookie de sesión que tenemos.

![image](https://github.com/user-attachments/assets/5c6a153f-3a97-4a3f-b20b-e964d11f29ba)

Nos metemos en el directorio /info.php

![image](https://github.com/user-attachments/assets/2df94d2f-1f0b-4551-b56c-a406a6f29169)

Buscamos por imagick y encontramos información interesante.

![image](https://github.com/user-attachments/assets/1fca2f5a-48c2-43bd-9f3f-56e49d362c8f)

Encontramos un exploit para la versión de imagick que nos muestra "ImageMagick 6.9.7".

![image](https://github.com/user-attachments/assets/be18ccff-ea4a-4120-870f-7c01c85b07ad)

Encontramos un github, con el que podemos explotarlo correctamente.

Github: https://github.com/voidz0r/CVE-2022-44268

Primero nos traemos el proyecto a nuestra máquina con git clone.

![image](https://github.com/user-attachments/assets/e96ffad8-2002-4d39-8be9-c1e0d6d0ba33)

Seguidamente runeamos el proyecto.

![image](https://github.com/user-attachments/assets/837e45b6-8a47-4d35-abc1-e58e2fab8797)

Si hacemos ls del proyecto vemos una imagen.

![image](https://github.com/user-attachments/assets/81d06f54-942b-43ed-af68-6f91b8d71030)

Vamos a subirla en nuestra web con el tamaño "500,500", y vamos a guardarla de nuevo.

![image](https://github.com/user-attachments/assets/e90c7ab1-9731-497f-b95c-a4304372114f)

![image](https://github.com/user-attachments/assets/65be8223-1e47-4629-af0d-96730f47ec7d)

Y ahora por último vamos a ejecutar este comando.

![image](https://github.com/user-attachments/assets/d1eba000-7f05-49a5-8814-71d93c966f79)

Y podemos ver este código que está en hexadecimal pero que se supone que es el /etc/passwd

![image](https://github.com/user-attachments/assets/f6c0af09-0fa3-44a9-9556-45b74348c1c2)

Entonces lo que vamos a hacer es pasarlo a ascii con xxd, para ello tendremos que guardar lo que tenemos en un archivo.txt

![image](https://github.com/user-attachments/assets/ca0a84c6-02f9-4b0a-b424-0628838f1a71)

Encontramos dos usuarios: application y lenam. Vamos a intentar hacer fuerza bruta con hydra para buscar posibles credenciales válidas.

![image](https://github.com/user-attachments/assets/e5bcc24e-6476-4e8f-84e7-3f2d18668e90)

Nos conectamos al servicio ssh con las credenciales obtenidas "lenam:loverboy".

![image](https://github.com/user-attachments/assets/59ee9e85-80cb-4155-b35f-183d5199f919)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/53631745-71e3-418a-b9f3-3f391ec4d61b)

Vamos a buscar en hacktricks información sobre este binario ya que en GTFObins no hemos encontrado nada.

Hacktricks: https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/linux-capabilities.html?highlight=kill#cap_kill

Encontramos que se podria escalar privilegios si existe un proceso de node js ejecutandose como root o de otro usuario.

![image](https://github.com/user-attachments/assets/d72260c3-0802-4301-81d4-2d06deab75c7)

Buscamos si esto sucede con el comando "ps aux", y encontramos uno que cumple con lo que buscamos "PID:58".

![image](https://github.com/user-attachments/assets/4aa3d150-d5b1-4531-9e0d-704d7bc8c25d)

Por tanto vamos a seguir los pasos que nos dicen em hacktricks.

![image](https://github.com/user-attachments/assets/55969419-5896-4ea9-8429-f60db1c7bc9c)

Enviamos la señal SIGUSR1 al proceso con PID 58.

![image](https://github.com/user-attachments/assets/792a1cff-4704-42a0-a263-85522f29c57a)

Seguidamente nos metemos en el link de abajo y vamos a seguir los pasos que nos dice.

![image](https://github.com/user-attachments/assets/68e72c33-066b-447f-96d7-051323798ab2)

![image](https://github.com/user-attachments/assets/086028f8-3bbe-41dd-bd06-8ecf3ff50506)

Ejecutamos los dos comandos que nos dice, pero en el segundo en la parte de exec, ejecutamos "chmod u+s /bin/bash", para poder escalar privilegios.

![image](https://github.com/user-attachments/assets/a797f422-08f7-498d-9cdd-52f8a298e21a)

Nos salimos del debugger y si hacemos "bash -p" ya somos root.

![image](https://github.com/user-attachments/assets/fcfc2337-ea42-4816-b7ae-54e67f8dc6a1)




