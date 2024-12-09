# RESOLUCIÓN DE LA MÁQUINA PARADISE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/153682ad-146f-46cd-9074-fbff4e578a67)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/d589e207-666a-49f6-9666-4afd69a71f11)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/b5da516f-a5db-44e1-b8d2-0eca852603e2)
![image](https://github.com/user-attachments/assets/86c7a344-eeff-423f-a7f8-1285695fed9a)

Abrimos la web.

![image](https://github.com/user-attachments/assets/c5ee107b-1850-4aed-a2ec-ac5d8be46a50)

En el código fuente del boton "Go to paradise", encontramos una pista cifrada.

![image](https://github.com/user-attachments/assets/6a831237-9490-41af-83b1-e90241777a4a)

Lo desencriptamos y nos devuelve esto: 

![image](https://github.com/user-attachments/assets/95bbfec9-fb9c-44f6-92e3-2b8915007007)

Lo usamos como directorio.

![image](https://github.com/user-attachments/assets/db847d9e-7bda-43ec-9988-48660142d26f)

Y vemos un archivo llamado mensaje_para_lucas.txt

![image](https://github.com/user-attachments/assets/9eee20da-840c-4b2f-89a6-62dd9203e391)

Ahora sabiendo que estamos tratando con sistemas SMB, usaremos enum4linux para recopilar información sobre estos.

![image](https://github.com/user-attachments/assets/ed565173-89c9-4c65-8d03-73ada2112342)

Nos encontramos tanto directorios como usuarios, volvemos a ver el usuario lucas.

![image](https://github.com/user-attachments/assets/387bc17d-31a7-41d2-8234-ace6561b1985)

![image](https://github.com/user-attachments/assets/f49047ed-0c25-4b24-bf7a-e0ed184ba1c7)

Anteriormente nos habían dado una pista, diciendo que la contraseña de lucas era débil, así que haremos fuerza bruta con hydra.

![image](https://github.com/user-attachments/assets/fad2711f-4493-4a42-bca0-d6d186682416)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/0f577efb-f0be-4582-9ff6-dc394cd75148)

Hacemos sudo -l y vemos esto:

![image](https://github.com/user-attachments/assets/1f0523ef-401a-4c6a-af6c-1520a68ec99c)

Escalamos privilegios y nos convertimos en andy.

![image](https://github.com/user-attachments/assets/2c938bed-4644-48db-a06f-4df10a200263)

No tenemos permisos sudo, probamos a buscar los permisos SUID.

![image](https://github.com/user-attachments/assets/4e330ed6-b81e-483d-a501-f022bfa6ef42)

Vemos que tenemos uno que se llama "privileged_exec", probamos a ejecutarlo y nos convertimos en root.

![image](https://github.com/user-attachments/assets/5bd2ebdc-d126-45c4-b9c3-77f187af6146)
