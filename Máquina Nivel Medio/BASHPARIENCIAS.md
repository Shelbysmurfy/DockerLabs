# RESOLUCIÓN DE LA MÁQUINA BASHPARIENCIAS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/95663303-902e-4a43-97c5-2579199d81b5)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/476a4624-4d3c-46d1-95f1-108874247095)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/b6605d23-394c-431d-bd50-0bcfe39c99b1)

Abrimos la web y vemos este mensaje, donde nos menciona un posible usuario.

![image](https://github.com/user-attachments/assets/0ebff90c-494c-4638-a3a7-f7fb741fc05a)

Vamos al código fuente y vemos una posible pista pero que no llego nada con ella.

![image](https://github.com/user-attachments/assets/61c7bab7-781d-4d74-ae42-a39ae0979baf)

![image](https://github.com/user-attachments/assets/3b4e3d1a-e044-4f16-9d7b-f98f1af59db6)

Probamos a hacer fuerza bruta con gobuster para ver que encontramos.

![image](https://github.com/user-attachments/assets/5adb015e-e8a7-4442-b9d0-56c7c6ea5224)

Encontramos un archivo.php con el que no podemos hacer nada, pero finalmente encontramos algo, en form.html vemos unas credenciales en el código fuente.

![image](https://github.com/user-attachments/assets/80c9b424-915a-4d9d-8921-1ceb6dfd03fa)

Nos conectamos al servicio ssh, por el puerto 8899, con las credenciales obtenidas "rosa:lacagadenuevo".

![image](https://github.com/user-attachments/assets/789e5e8f-505d-4593-a51f-8dad943a461f)

Nos metemeos en el directorio /rosa/-/, y vemos este mensaje junto a un archivo.zip

![image](https://github.com/user-attachments/assets/9cb85b92-d913-46d3-9712-05bade12c7c2)

Nos traemos el archivo.zip a nuestra máquina atacante.

![image](https://github.com/user-attachments/assets/f1937f44-ca53-4274-b0f9-aafb7621f6ac)

![image](https://github.com/user-attachments/assets/c1735cd6-ba56-45a2-a86c-95ccd4d9ecbc)

Hacemos zip2john para extraer el hash, luego john para encontrar la password, y finalmente podemos hacer un unzip del archivo.

![image](https://github.com/user-attachments/assets/3649e4e5-1f98-4e52-aeba-2b148824ab9b)

Abrimos el archivo.txt que hemos conseguido y vemos una posible credencial "hackwhitbash".

![image](https://github.com/user-attachments/assets/6520da52-01d6-4a7e-8d60-d6d7f0269532)

La probamos para los dos usuarios que tenemos, y ganamos acceso con uno de ellos, juan.

![image](https://github.com/user-attachments/assets/8bc59dd0-de3d-4277-9187-779937190264)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b07b4e26-5944-45c7-a36b-8116ec4d4e5f)

Hacemos uso tanto de tree como de cat y encontramos una contraseña dentro del directorio carlos.

![image](https://github.com/user-attachments/assets/15b6f042-a10a-4797-838c-3cca7795ebc2)

Nos conectamos con las credenciales obtenidas "carlos:chocolateado".

![image](https://github.com/user-attachments/assets/34e1a582-bc8d-4933-ad90-e7e546e0b00f)

Volvemos a hacer sudo -l y ahora vemos esto: 

![image](https://github.com/user-attachments/assets/b412726c-2da4-488d-878f-d94fe462029e)

Como podemos usar tee como root vamos añadir a carlos al archivo sudoers para que podamos escalar a root sin proporcionar contraseña.

![image](https://github.com/user-attachments/assets/2002df0c-dd1e-412a-abbb-2243bf474a46)

Y ya somos root.

![image](https://github.com/user-attachments/assets/88819456-8e70-40a6-929d-8bfe53785a6d)

