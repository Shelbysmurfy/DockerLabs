# RESOLUCIÓN DE LA MÁQUINA STELLARJWT

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/ecfaf5e5-4170-4136-9c50-f0e372eb2eb4)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/dd79b43b-e7a4-46e8-9bff-b1391aa7167c)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/67bdbfaf-5412-4ef2-9b39-7efc48625c09)

Abrimos la web.

![image](https://github.com/user-attachments/assets/1eff21e7-78cf-4d62-ab0f-12ff33ba97b8)

Hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/b22f9f5c-e1c1-454d-9d95-bd10d564ec25)

Nos metemos al directorio /universe, y en el código fuente nos encontramos un texto cifrado.

![image](https://github.com/user-attachments/assets/0343d52b-2b25-42ec-993a-4dddb146045b)

Nos vamos a la web de cyberchef y lo decodificamos.

![image](https://github.com/user-attachments/assets/2b090325-6a71-4e21-b707-bcb34992a23b)

Sabiendo el usuario neptuno, intentaremos hacer hydra usando como contraseña Johann Gottfried Galle, que es el alemán que descubrió neptuno, que es la pregunta que nos sale al principio.

![image](https://github.com/user-attachments/assets/db93ac37-c4da-4598-aa52-813a5b013fdd)

![image](https://github.com/user-attachments/assets/aedb1701-3434-4b1b-bfcc-99ab2231c4d9)

Nos conectaremos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/fba809f0-6783-492f-be2e-6cf7e85000ef)

Dentro de el usuario neptuno encontramos un archivo oculto, lo abrimos.

![image](https://github.com/user-attachments/assets/013febaa-5efa-44c6-b9cd-fd11cf4e21eb)

Vemos que hay 3 usuarios, unos de ellos es nasa, que es el que se menciona en la carta.

![image](https://github.com/user-attachments/assets/d6fc02f3-732f-48dc-9840-2458a82ff69a)

Entramos como usuario nasa usando como contraseña: Eisenhower

![image](https://github.com/user-attachments/assets/f3a48f2e-31b7-4399-858e-fba26a8ed55f)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/fd72bc5e-d8bf-4621-9be1-f37fa7302f4b)

Escalamos privilegios y nos convertimos en elite.

![image](https://github.com/user-attachments/assets/03f003be-f4e5-4cd9-9045-46efefb1b381)

Volvemos a hacer sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/d2685e58-a324-458b-989a-c08b867d33a1)

Y ya somos root.

![image](https://github.com/user-attachments/assets/cdb25d79-4885-4988-97c4-464288d3c9db)



