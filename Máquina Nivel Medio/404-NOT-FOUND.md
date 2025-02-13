# RESOLUCIÓN DE LA MÁQUINA 404-NOT-FOUND

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/35492a91-cfae-465d-b888-7789eba82ec6)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/0305c0af-8c3b-494e-9266-2ebf75cd6e1b)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/827c8e33-50d0-42f4-ab15-5138e6be9844)

Añadimos el dominio que nos dan y vemos la página.

![image](https://github.com/user-attachments/assets/a73b5f3e-f701-4b15-918c-71e00828cf36)

La damos a participar y vemos esto: 

![image](https://github.com/user-attachments/assets/d272e299-0382-48cd-b1de-b226a52bed8e)

La clave secreta nos da esta información: 

![image](https://github.com/user-attachments/assets/00db1297-abeb-40a5-a6f5-8796be102970)

Hacemos un wfuzz para buscar posibles subdominios en la url.

![image](https://github.com/user-attachments/assets/67ba4f7c-25e0-4e61-9735-3947f13d0936)

Entramos en la ruta y encontramos un login.

![image](https://github.com/user-attachments/assets/5e7b5e2a-c561-43bb-b295-3ea6a99a7231)

Inspeccionamos la página y encontramos una pista.

![image](https://github.com/user-attachments/assets/00f79351-669f-4301-b2eb-87b81d9810c8)

Como nos da una pista de que puede ser vulnerable con un bypass de ldap, vamos al hacktricks y buscamos la forma de hacerlo.

url: https://book.hacktricks.wiki/en/pentesting-web/ldap-injection.html#login-bypass

![image](https://github.com/user-attachments/assets/4297697b-c4d8-4c41-b4be-3ef042298887)

![image](https://github.com/user-attachments/assets/ffb9134e-5004-4cc7-bf9c-80b32b77ffb9)

Y ganamos acceso.

![image](https://github.com/user-attachments/assets/16a3d02f-e320-4f9f-9009-ca44da0b409a)

Nos conectamos al servicio ssh con las credenciales que vemos en el Panel de Administración.

![image](https://github.com/user-attachments/assets/fdd18798-2819-4591-bb31-3a541260a7f8)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b539400e-f871-4484-8472-4c2171f7dc74)

Nos convertimos en el usuario 200-ok

![image](https://github.com/user-attachments/assets/17446ea7-f0a7-41a4-9252-079dcec417d9)

Encontramos la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/b27b404d-7b2f-44ab-bc44-338c4990f847)

En ese directorio encontramos otro archivo con una posible credencial.

![image](https://github.com/user-attachments/assets/00b12fd8-2fa5-4187-a77f-5dbd26f47ff9)

La usamos para el usuario root, y nos funciona.

![image](https://github.com/user-attachments/assets/a9337d7a-f125-4270-8a43-65afc16331ad)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/9e071f46-23fb-4fe5-b975-68859a641d1e)
