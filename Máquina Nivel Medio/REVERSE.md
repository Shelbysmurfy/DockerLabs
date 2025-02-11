RESOLUCIÓN DE LA MÁQUINA REVERSE

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/4d8a9b18-dd28-4816-9cfe-96dfa09c510a)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6880a1e5-5088-41b6-a06e-110a2cedea2f)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/fb876932-f0b5-407c-b53c-bd11b39e6d9c)

En el código fuente vemos un archivo script.js

![image](https://github.com/user-attachments/assets/df849e38-6de2-44e2-b1d1-b8f82089f442)

Dentro de el encontramos una ruta que contiene un archivo.

![image](https://github.com/user-attachments/assets/e63ce6aa-56bd-4787-a9cd-806e4d6f1575)

![image](https://github.com/user-attachments/assets/b54a99ad-65b2-4352-a0b0-4b568cced97f)

Si hacemos uso del parámetro file y el nombre del archivo vemos que es un archivo ejecutable, le damos permsisos, lo ejecutamos, pero vemos que es necesaria una contraseña.

![image](https://github.com/user-attachments/assets/67cab5fa-8280-4b20-ad32-e01b3d32f05f)

Como puede tratarse de Ingeniería inversa, vamos a descargar ghidra para sacar información.

![image](https://github.com/user-attachments/assets/dd927c52-2703-4dc1-9f23-10965a5aaa0a)

Lo ejecutamos y vemos una función que puede ser interesante dentro del archivo main.

![image](https://github.com/user-attachments/assets/deae849f-b8bf-4fd6-aabb-62378190281c)

![image](https://github.com/user-attachments/assets/15ee332b-c68c-4855-8878-70a79a7a0e73)

La abrimos para ver que contiene.

![image](https://github.com/user-attachments/assets/9d445edf-4386-4d21-af38-1addeeeb8a2b)

Vemos tres palabras entre comillas que pueden ser una contraseña (@MiS3cRetd00m)

![image](https://github.com/user-attachments/assets/00d138c6-aa11-4f07-a70e-204f10e8ed25)

Ejecutamos el archivo secret con la contraseña obtenida.

![image](https://github.com/user-attachments/assets/b008bf66-3a60-4b26-a0c4-42619352e0ec)

La contraseña está cifrada en base64, la decodeamos.

![image](https://github.com/user-attachments/assets/4043789f-3b34-4d22-80df-be8d88504ace)

Parece ser un dominio, así que nos vamos al /etc/hosts y lo ponemos para la IP que tenemos.

![image](https://github.com/user-attachments/assets/b47f51bb-9d72-4941-9244-7c6ae12bfad8)

Abrimos la web.

![image](https://github.com/user-attachments/assets/ac836d99-cc05-4718-a49c-cf9d16c57d6d)

Nos metemos en el apartado de experimentos activos y vemos esto: 

![image](https://github.com/user-attachments/assets/7d44d2c9-4193-422a-86fc-75ba2246d7b9)

Aprovechamos la url con el parámetro module y ejecutamos un /etc/passwd, y vemos que es vulnerable a LFI.

![image](https://github.com/user-attachments/assets/074f12b5-9c87-4d24-9ea4-b9c9a7a5d77b)

No consigo que los logs me muestren nada (/var/log/apache2/access.log), y por tanto no puedo continuar.
