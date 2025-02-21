# RESOLUCIÓN DE LA MÁQUINA FILECEPTION

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/26ec823c-5a03-41ce-9c43-de182f88e267)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/37c9a29c-f683-46dd-b6c0-882ff13942b9)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/99a2da63-e5e2-4613-8162-39d59d096363)

Entramos en la web.

![image](https://github.com/user-attachments/assets/7ae5e92c-bb42-4d00-a2e8-93a7e0011035)

Abrimos el código fuente de la máquina y encontramos esta pista: 

![image](https://github.com/user-attachments/assets/dc20b708-75f9-4366-ad86-301e429521bb)

Vamos a cyberchef para descifrar la clave cifrada que nos han dado.

![image](https://github.com/user-attachments/assets/6a1088d5-5198-4f13-9ce1-aa5128390393)

Como no encontramos mas información nos conectamos al puerto 21 con el usuario anonymous y nos traemos a nuestra máquina una imagen.

![image](https://github.com/user-attachments/assets/8e270d0d-13b0-41c6-ba7e-952a1a103331)

Extraemos información de la imagen, gracias a la herramienta steghide y usando como passphrase: "base_85_decoded_password"

![image](https://github.com/user-attachments/assets/efd15363-6145-4afd-8ba6-535ed6697850)

Decodeamos el código que tenemos que esta utilizando el código Ook!

![image](https://github.com/user-attachments/assets/0a9a8649-0c6f-40e6-be2c-42f218320b78)

Al intentarnos conectar al servicio ssh, solo nos dejara si le quitamos el 3 del final, ya que no hace referencia al código.

![image](https://github.com/user-attachments/assets/436353b2-6ebe-46bf-9164-fdb16e173cd1)

Encontramos una pista en el directorio /home/peter

![image](https://github.com/user-attachments/assets/196b64d2-463a-4e15-9bc9-a7c96705f399)

Nos vamos al directorio /tmp, y vemos dos archivos, donde uno de ellos esta codificado y el otro nos da esta información.

![image](https://github.com/user-attachments/assets/2ec9280c-156a-4cab-a33b-de6b27a83352)

Si convertimos nuestro archivo.odt a un archivo.txt vemos información relevante.

![image](https://github.com/user-attachments/assets/48d822ec-6138-4a0b-a952-ac63d89faa1e)

Probamos a convertirlo a .zip y al descomprimirlo nos devuelve este archivo, lo abrimos y vemos unas credenciales.

![image](https://github.com/user-attachments/assets/6d4214b7-4490-4714-85b1-14987cedb475)

![image](https://github.com/user-attachments/assets/f8758b0e-059b-4556-baa3-3c5ccfbf41ae)

La clave parace estar en base64, así que la desciframos.

![image](https://github.com/user-attachments/assets/21b4b9a7-feda-4ab6-8cf9-3e72946814b2)

Nos conectamos al servicio ssh con las credenciales obtenidas "octopus:80h2380h34uouo3h4"

![image](https://github.com/user-attachments/assets/22f43c71-40da-4c9c-b611-976ff216308b)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/bccb0bf9-c131-42d5-99cd-5f37fe50dc7b)

Y ya somos root.

![image](https://github.com/user-attachments/assets/3d26b3ed-2497-4262-b3b6-53fb9f62f048)



