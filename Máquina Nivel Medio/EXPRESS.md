# RESOLUCIÓN DE LA MÁQUINA EXPRESS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/cd8504ae-a938-4db4-a4bf-7041ca8ec4a2)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/5dd0fff5-440d-4738-a472-f2722fcde652)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/de611db0-d845-4e89-ad56-9185b0dddbde)

Abrimos la web, pero no encontramos nada.

![image](https://github.com/user-attachments/assets/0b5f8588-a9d0-4671-8295-d43ad5ad9306)

Probamos a mirar si hay algún puert UDP abierto y encontramos el puerto 161.

![image](https://github.com/user-attachments/assets/d0085677-d68d-430b-920e-f64a8517c2bd)

![image](https://github.com/user-attachments/assets/2fd1aa91-4592-49ce-b3f5-052f85b2db53)

Gracias a este puerto, vamos a realizar una consulta SNMP (161), para obtener información sobre los objetos del dispositivo.

Encontramos un posible dominio "express.dl".

![image](https://github.com/user-attachments/assets/795678b9-6573-4011-ac07-15deda967e57)

Vamos a añadirlo al /etc/hosts y lo abrimos.

![image](https://github.com/user-attachments/assets/7d8135f0-a9cd-4916-88fc-33c8b9226eca)

![image](https://github.com/user-attachments/assets/56cc4edf-5265-487a-93c9-ca7c4abc670d)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/677206cf-0339-4dca-9dc0-7f420910e348)

En el directorio /binary encontramos un archivo "game", nos lo descargamos.

![image](https://github.com/user-attachments/assets/8a7f62b0-3180-4406-828f-65f369142e0b)

Lo ejecutamos y nos pide que adivinemos 100 numeros, y como tardaríamos demasiado, vamos a hacer un strings para ver si vemos algo.

Vemos una posible contraseña, pero cuando la probamos no funciona.

![image](https://github.com/user-attachments/assets/f396eed1-dc93-40a1-890e-93102e393658)

Miramos en el ghidra y en el encontramos la función "hidden_key", que contiene esta información: 

![image](https://github.com/user-attachments/assets/3da8bab6-8e68-46d0-b33c-5d5085af29b9)

Vamos a convertir cada uno de los valores hexadecimales que tenemos a ascii.

![image](https://github.com/user-attachments/assets/23c3b8bf-ef57-4147-a232-bd2857439917)

![image](https://github.com/user-attachments/assets/c9529162-50bc-4817-9279-be7fb741b718)

![image](https://github.com/user-attachments/assets/9d97b945-3fc3-4ba0-9511-6b6abfc782ad)

![image](https://github.com/user-attachments/assets/416690b6-6395-493c-aa8a-dffd7c3278ac)

![image](https://github.com/user-attachments/assets/db5c7fbf-2b04-4f9f-b313-7f289ec60768)

Si nos fijamos bien se parece mucho a la posible contraseña que habíamos encontrado antes, pero cada una de estas está al revés.

La giramos y nos podemos dar cuenta que es un poco diferente a la de antes.

ANTES: P@ssw0rdH!#--0251H--025163HfhusGNFEH

AHORA: P@ssw0rd!#--025163fhusGNFE

Hacemos fuerza bruta con hydra y encontramos unas credenciales válidas "admin:P@ssw0rd!#--025163fhusGNFE".

![image](https://github.com/user-attachments/assets/04d13bfa-de8f-4a99-87ce-50c797aae0d7)

Nos conectamos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/1842f9c7-6b4e-44ef-bf01-38e3b96dd1af)

Hacemos ls y encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/89cbf8b4-5115-43b2-bff3-c9a3ff9d9d24)

Miramos los permisos SUDO y vemos esto: 

![image](https://github.com/user-attachments/assets/83127bb6-5af3-49ff-b263-4dc14b735954)

Miramos el archivo script.py y en el vamos una libreria un tanto rara, pytest.

![image](https://github.com/user-attachments/assets/e220749f-eb88-4467-bc43-afaeca5142a3)

Buscamos su ubicación con find.

![image](https://github.com/user-attachments/assets/0ff20124-ba27-4d12-b840-c4f68ce6db9c)

Y ahora miramos a ver que contiene el archivo, pero parece que esta vacío.

![image](https://github.com/user-attachments/assets/2caa51e0-691a-4a08-aff2-16258fee683c)

Por tanto vamos a añadirle unos comandos que nos permitan escalar privilegios al ejecutar el permiso SUDO.

![image](https://github.com/user-attachments/assets/b05b8c0c-b239-4b0d-877d-6a9e0dc9e7f3)

Ejecutaremos el permiso SUDO que tenemos junto al archvio que nos menciona.

![image](https://github.com/user-attachments/assets/89aa0d4b-fd4a-4739-ab20-192676472f9d)

Nos salta una animación ilimitada, la pararemos con Ctrl + c, haremos un bash -p, y ya seremos root.

![image](https://github.com/user-attachments/assets/84a594a3-8df6-4318-aa16-53f49aeb59f3)

Encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/00e9e57e-562b-4be6-b72f-dd3a728a0f53)
