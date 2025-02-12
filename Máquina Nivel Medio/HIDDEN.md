# RESOLUCIÓN DE LA MÁQUINA HIDDEN

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/91e522ff-7ae5-4814-bda0-4186370327c8)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/0963bee7-9301-418d-863f-4f86638f9583)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/4157eb4a-2e55-4a3c-9f79-a11155d138a8)

Abrimos la web, pero antes tenemos que añadir el dominio "hidden.lab" en el /etc/hosts

![image](https://github.com/user-attachments/assets/37d3a9df-be19-4d11-99ef-51d3e33db86c)

Buscamos subdominios con wfuzz, ya que no hemos encontrado directorios con gobuster.

![image](https://github.com/user-attachments/assets/506e8cf2-082b-4deb-a162-89c008c5ca83)

Añadimos el nuevo dominio en el /etc/hosts y lo abrimos.

![image](https://github.com/user-attachments/assets/c19c528d-97d0-454b-8c93-9dd20cac3140)

Como no deja subir archivos .php, subimos una extensión parecida .phtml, para ello creamos un archivo malicioso.

![image](https://github.com/user-attachments/assets/329a11c8-887e-49c0-a033-f2d9784e98dd)

![image](https://github.com/user-attachments/assets/c921ebdd-d9d7-4cfe-ac58-d520413af18d)

Abrimos el directorio uploads, y si accedemos al artchivo vemos que podemos inyectar comandos correctamente.

![image](https://github.com/user-attachments/assets/2df02446-0bb9-4fb6-bdf9-f527fec5a973)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/bdc29995-8c48-4efd-8846-459dd160fa59)

Encontramos tres usuarios, pero como no encontramos nada mas,  vamos a hacer uso de la herramienta suForce, junto con la libreria rockyou, para sacar la contraseña de estos usuarios "https://github.com/d4t4s3c/suForce".

Nos los traemos a nuestra máquina víctima gracias a la subida de archivos, para ello el rockyu vamos a coger solo las primeras 500 filas, ya que sino no me deja subirlo.

![image](https://github.com/user-attachments/assets/5288ce94-2122-4e8b-b669-97288d66de3d)

![image](https://github.com/user-attachments/assets/0914782f-2aa4-4371-abd3-0b2e0274c98a)

Nos movemos los archivos al directorio /tmp

![image](https://github.com/user-attachments/assets/82c52e53-fc40-460a-8ea9-f48e90ac2025)

Le damos permisos de ejecución y buscamos posibles para cada uno de los usuarios, pero solo la encontramos para uno de ellos.

![image](https://github.com/user-attachments/assets/f37c7fc8-f553-4fea-9afe-07997cca0f9f)

Nos conectamos con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/0aab60ad-9af8-4075-ba33-97188391d738)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/b94a78a8-12a0-415b-9562-963c449bc051)

Nos conectamos como usaurio john siguiendo los pasos que nos indica el GTFObins.

![image](https://github.com/user-attachments/assets/11373888-5ab1-4a4e-aa00-64735ef5f0db)

![image](https://github.com/user-attachments/assets/88d38029-17c4-451d-bcab-7f582c57d909)

Volvemos a hacer sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/09f92c07-7ae9-4e1b-8dc5-6732fd90f93f)

Nos conectamos como usuario bobby.

![image](https://github.com/user-attachments/assets/eb5f6466-b703-459a-bb09-0b5c538931bc)

![image](https://github.com/user-attachments/assets/3142387e-ae51-477f-a76e-4353f2b86591)

Y volvemos a hacer sudo -l.

![image](https://github.com/user-attachments/assets/b6e8f940-1d52-486a-bfb0-dcca01d88e4e)

Y ya somos root.

![image](https://github.com/user-attachments/assets/14f1f23c-6510-4bbb-b0ad-01d833b5db38)

