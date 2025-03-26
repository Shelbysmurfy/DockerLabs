# RESOLUCIÓN DE LA MÁQUINA SUMMERVIBES

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/d1b258c0-12ac-4636-b87d-682b03fccd0f)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/bc37053b-bd22-4642-a5a8-909ddd2ca3be)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/5c4698f0-68f4-4318-bfcb-5a69c9ff01f0)

Abrimos la web.

![image](https://github.com/user-attachments/assets/08fc2add-2778-4cdb-86ef-467520a33cb6)

Nos metemos en el código fuente y vemos esta pista.

![image](https://github.com/user-attachments/assets/4ca93b65-c64b-41fd-a6a8-402b3b6bf93f)

La añadimos en la url y vemos esta web.

![image](https://github.com/user-attachments/assets/9c7fa96c-bd7c-4d6c-92ac-be8e0356b230)

Realizamos un gobuster para ver los directorios disponibles.

![image](https://github.com/user-attachments/assets/1659d0fa-ac22-4351-bb42-9264d2ad2f8c)

Encontramos un login, pero no tenemos credenciales válidas para este.

![image](https://github.com/user-attachments/assets/737f333c-ba84-4fa2-91eb-8fbb939cc3da)

Capturamos la petición del login con el burpsuite.

![image](https://github.com/user-attachments/assets/55f9a726-291b-4a8b-9c48-d10fe93aeb38)

A partir de esto hacemos un hydra en busca de credenciales válidas, donde si probamos un usuario básico como admin, encontramos una contraseña válida.

![image](https://github.com/user-attachments/assets/c2a85569-4263-46f7-870c-f760b759e3b7)

Nos conectamos con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/6cec560b-4879-49a7-8dd3-1e54e62cd7b0)

Encontramos una subida de archivos.

![image](https://github.com/user-attachments/assets/275cda78-092b-49b5-a200-81c367f745ff)

Sbubimos un archivo malicioso y nos vamos al directorio uploads y lo vemos subido correctamente.

![image](https://github.com/user-attachments/assets/f7e38a58-1cd6-4538-ae68-55e69cac98bb)

![image](https://github.com/user-attachments/assets/7eed94f3-dc68-4bde-8d00-5825f9972257)

Lo abrimos y si probamos a ejecutar comandos funciona correctamente.

![image](https://github.com/user-attachments/assets/86c0a679-7d62-4e1f-bfb3-a01ea73d6c9d)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/f816bdc5-d20f-46c7-97a0-3b019c187fbb)

No encontramos nada, solo sabemos que tenemos el usuario cms y el root.

Vamos a traernos la herramienta suForce junto al rockyou, para hacer fuerza bruta en busca de contraseñas.

![image](https://github.com/user-attachments/assets/e8ef206d-695a-4ebb-82e7-580a9dfbce9c)

Probamos para el usuario cms pero no encontramos nada.

Pero si probamos con el usuario root encontramos la contraseña.

![image](https://github.com/user-attachments/assets/b9a17f45-ec08-4929-b31a-f7b21a222d3e)

Y si introducimos las credenciales obtenidas ya somos root.

![image](https://github.com/user-attachments/assets/23b44d4a-afa7-4bab-845d-7df1d9f9a776)
