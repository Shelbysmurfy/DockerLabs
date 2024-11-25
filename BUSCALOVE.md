# RESOLUCIÓN DE LA MÁQUINA BUSCALOVE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/67e72fa8-8c6a-437b-aacc-39458ef73194)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/adcd543d-5e38-4bac-8828-52ecfec760b2)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/95d2135d-5d99-4bd5-86b5-9e5feaf1eea6)

Hago fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/52fc2554-0f59-4920-8537-21eaab07744d)

Abrimos el código fuente y me encuentra con esta información: 

![image](https://github.com/user-attachments/assets/e16b8c44-2ffd-4e14-a358-ff5a56a2216b)

Probamos a poner ?love, gracias a la pista que nos da, junto al /etc/passwd, para ver si nos lo muestra.

![image](https://github.com/user-attachments/assets/ff47132c-6675-4903-b012-c4160ecea9ed)

Haremos fuerza bruta para los dos usuarios que hemos encontrado, pedro y rosa.

Para el usuario rosa encontramos estas credenciales: 

![image](https://github.com/user-attachments/assets/8551c4e9-0ae9-4746-8fdb-051030e6af40)

Vamos a entrar al servicio ssh con las credenciales que hemos encontrado. 

![image](https://github.com/user-attachments/assets/84ed9dc9-83ce-438f-b2dd-b7a3df2d7ce5)

Hacemos sudo -l y nos econtramos con esto: 

![image](https://github.com/user-attachments/assets/88ceeff3-fd52-494d-aa0f-a74666cfd09c)

Hacemos ls para ver que hay dentro del usuario root y luego cat para ver el archivo que hemos visto dentro.

![image](https://github.com/user-attachments/assets/c9e0e95c-dd66-425b-8d18-2d7f7081e83d)

Nos vamos a la web de cyberchef y lo decodificamos.

![image](https://github.com/user-attachments/assets/0df1248a-cec1-4bed-81e7-94a766c5873a)

Sabiendo esta credencial vamoa a intentar entrar con el usuario pedro y la contraseña: noacertarasosi

![image](https://github.com/user-attachments/assets/d8e94753-fceb-48ba-a087-f1b91d03410d)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/dfd0a44d-597e-4904-9eea-0246234ad000)

Vamos al GTFObins seguimos los pasos que nos dice y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/4f3415ea-2977-498a-8c25-9ba062b0e781)


