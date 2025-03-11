# RESOLUCIÓN DE LA MÁQUINA ECLIPSE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/485377de-a928-4b85-be86-bb677026fc3f)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/95032f4f-5fe6-40bf-82ee-d8c9ee58d9f3)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3fa5edf3-89cf-4e94-bade-63e98f74b132)

Abrimos por el puerto 80 y vemos una imagen, pero no podemos sacar nada de ella.

![image](https://github.com/user-attachments/assets/3fce79ef-9178-422b-be0e-1ac81d0a7a87)

Entonces vamos a abrir por el puerto 8983.

![image](https://github.com/user-attachments/assets/63307408-62a2-45db-a300-ee7cf35c76c8)

Vemos la versión de solr, la 8.3.0, y buscamos posibles exploits.

![image](https://github.com/user-attachments/assets/dcd5f512-76c6-435d-81e1-59b3ec737a0d)

![image](https://github.com/user-attachments/assets/2752f7c0-0622-41e1-93ea-e5c5d2da078b)

Ahora vamos a usar metasploit para configurar el exploit que hemos encontrado.

![image](https://github.com/user-attachments/assets/a80063f3-475a-4ac2-85be-34c5f42dc73a)

Lo configuramos y lo ejecutamos.

![image](https://github.com/user-attachments/assets/1908708c-3c3d-49fc-a736-d7865c910bf2)
![image](https://github.com/user-attachments/assets/07fe3714-dd98-45f6-a447-8421c63c3ce6)

![image](https://github.com/user-attachments/assets/6f7e02bf-2aa8-43ce-b3b4-197349646455)

Ya que tenemos la sesión de meterpreter y podemos ejecutar comandos vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/7fe86225-2d11-423b-8f4d-e8ded713e29d)

![image](https://github.com/user-attachments/assets/cbb75449-3ada-40e1-9c83-f6fdb3b64dfd)

Listamos los permisos SUID y encontramos uno interesante "/usr/bin/dosbox".

![image](https://github.com/user-attachments/assets/a01f3382-0faa-4c83-8270-fc0c6dbbea0a)

Nos vamos al GTFObins para ver como escalar privilegios.

![image](https://github.com/user-attachments/assets/674dba03-bce3-497b-8c21-058dae075928)

Usamos este permiso para añadir a el usuario ninhack al archivo sudoers para que podamos escalar a root sin proporcionar contraseña.

![image](https://github.com/user-attachments/assets/7ff74a8c-22ed-4710-b276-8681178225aa)

Y ya somos root.

![image](https://github.com/user-attachments/assets/2fb773e8-294d-4c22-9043-9899f41045ab)
