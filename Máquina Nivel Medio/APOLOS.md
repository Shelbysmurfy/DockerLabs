# RESOLUCIÓN DE LA MÁQUINA APOLOS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/842a5eb8-1f1a-460b-b214-2436f138f683)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6e545db5-9883-49ba-a34b-f97743b2c047)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/99801049-d076-4d27-9cb2-b28a4ccfe0fe)

Abrimos la web.

![image](https://github.com/user-attachments/assets/fe56a949-59f6-4a3d-820b-e0ba9675ec9a)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/2508308c-0437-456a-828d-0bc3aefde979)

Nos registramos y nos logueamos.

![image](https://github.com/user-attachments/assets/2fb5708b-c918-40a8-b062-a9e666319b12)

Si inspeccionamos la página podemos ver nuestra cookkie de sesión.

![image](https://github.com/user-attachments/assets/a031f79c-2b47-4d2d-9757-798eaa739c39)

Enviamos una petición con sqlmap, para detectar y explotar vulnerabilidades de inyección SQL en la URL dada, usando nuestra sesión.

![image](https://github.com/user-attachments/assets/e197d54a-ae87-4adb-8a79-46044910ee7e)

Encontramos estos 4 usuarios: 

![image](https://github.com/user-attachments/assets/7a733a0e-fcda-461c-949e-5a451f70ee5b)

Con hash-identifier vemos que los dos usuarios tienen la contraseña cifrada en sha1.

Las decodificamos con john (luisillo/mundodecaramelo, admin/0844575632)

![image](https://github.com/user-attachments/assets/0106b3bd-9d2c-42e5-b703-4b6120025a6e)

![image](https://github.com/user-attachments/assets/bff2cad6-639f-4caa-8a1a-9dc08a9fb203)

Nos conectamos como admin, y vemos un panel de administración.

![image](https://github.com/user-attachments/assets/dcd09687-4270-448d-bb25-7ec277b6c2b2)

Nos encontramos con una subida de archivos.

![image](https://github.com/user-attachments/assets/46546327-393b-45cc-8609-a80189b475a7)

No nos deja subir archivos.php

![image](https://github.com/user-attachments/assets/5475372c-89bc-4f84-81b9-0a72a91f4b19)

Nos vamos a burpsuite y vemos que los archivos .phtml podemos subirlos.

![image](https://github.com/user-attachments/assets/7fb43362-62ca-4055-8296-1df3af8d14b0)

Lo subimos.

![image](https://github.com/user-attachments/assets/fe635b4c-63d5-45eb-a027-6952c9fcd110)

Vamos al /uploads, y vemos que podemos inyectar comandos.

![image](https://github.com/user-attachments/assets/3d119a7c-9fd8-4e8d-8a75-3ff13aaaaf5f)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/93ded883-462e-4298-b3dd-6cdc5cf947ca)

Encontramos el usuario luisillo_o, vamos a hacer uso de la herramienta suForce, junto con la libreria rockyou, para sacar la contraseña de este usuario "https://github.com/d4t4s3c/suForce".

Nos los traemos a nuestra máquina víctima con la herramienta wget.

![image](https://github.com/user-attachments/assets/b153ee3d-ab19-4a5d-bc23-ea43f4077c2f)

Ejecutamos el suForce y contramos estas credenciales: 

![image](https://github.com/user-attachments/assets/f6131f2c-4a76-47ee-9d56-8380950a8aa7)

Nos conectamos con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/cd2282b7-56a2-417a-ae24-018a1c9a134c)

Hacemos id y vemos esto: 

![image](https://github.com/user-attachments/assets/488b56c1-8a6c-4552-9455-12a5d1389596)

Nos vamos a nuestra máquina, guardamos la contraseña hasheada en un archivo hash, y usamos john para descifrarla.

![image](https://github.com/user-attachments/assets/421bb0bb-82b9-436f-ba5e-a2c33a0a4824)

Nos conectamos como usuario root, con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/82ddb6d5-1097-4e82-a42b-987fde0d0632)

