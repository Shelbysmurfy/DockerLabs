# RESOLUCIÓN DE LA MÁQUINA ASUCAR

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/594b310c-24e0-474e-adb6-edd42b583624)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/799472a0-022e-4077-ab5b-5a9f4d274e7d)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/19c04d71-f6a3-4f19-ac4e-9658632ec19b)

Añadimos en el /etc/hosts el dominio asucar.dl y abrimos la página.

![image](https://github.com/user-attachments/assets/a49ba292-c160-4951-8478-56326caa8de9)

![image](https://github.com/user-attachments/assets/2a429662-0215-4ff7-b97d-9b038a8e9ae5)

Vemos que seguramente haya un wordpress y que el posible usuario sea wordpress.

![image](https://github.com/user-attachments/assets/4ef09e5f-e5f1-4173-9ea9-18c9192ce100)

Vamos a hacer fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/5a2f392c-6983-49b8-ab1b-f609aa163e7d)

Nos vamos al panel del login de wordpress, y si ponemos el usuario wordpress, nos dice que el usuario es correcta pero la contraseña no.

![image](https://github.com/user-attachments/assets/6e5e9184-8af8-4ee1-bb25-be83333fe0cc)

Hacemos uso de la herramienta wpscan en busca de la contraseña, pero no encontramos nada.

Vamos a hacerle un curl a la página principal para ver si se llama a algun plugin, y efectivamente vemos que está llamando al plugin site editor.

![image](https://github.com/user-attachments/assets/08cdd361-3740-456a-81f5-c7017887e6be)

Buscamos exploits para ese plugin.

![image](https://github.com/user-attachments/assets/9a7d30fe-4ca7-4631-998f-b5585aae08d8)

Miramos el contenido de este y encontramos un posible LFI.

![image](https://github.com/user-attachments/assets/3f00b0a0-c893-4926-920e-93812571b9a9)

![image](https://github.com/user-attachments/assets/910c91d6-2579-42ce-bb26-9b52ecc87892)

Lo usamos con nuestro host y podemos ver el /etc/passwd, en el encontramos un posible usuario "curiosito".

![image](https://github.com/user-attachments/assets/551d4a6a-87ff-4137-b512-41b682f59df5)

Usamos hydra para encontrar la contraseña de este usuario para el servicio de ssh.

![image](https://github.com/user-attachments/assets/08b9a7f6-58c9-4cc3-a383-1924e263e26c)

Vamos a conectarnos al servicio ssh con las credenciales obtenidas "curiosito:password1"

![image](https://github.com/user-attachments/assets/2969e895-85fd-40e3-913c-5058322ba89a)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/3fb0cfa4-f182-41f0-87ca-a4f3c55c2ce6)

Viendo esto, lo primero que hacemos es crear una clave SSH utilizando puttygen, una herramienta diseñada para gestionar claves SSH en diferentes formatos. Esto genera una nueva clave privada RSA, que se almacena en el archivo id_rsa.

![image](https://github.com/user-attachments/assets/ed479bdf-65e3-47eb-b8ef-fd281968b13b)

Con la clave privada generada, el siguiente paso es crear la clave pública correspondiente y agregarla al archivo authorized_keys del usuario root. Esto permitirá el acceso SSH sin necesidad de contraseña desde el usuario curiosito.

![image](https://github.com/user-attachments/assets/db49da94-39ce-42bc-b4bc-2840ab6c2e85)

Y por ultimo, antes de conectarnos por el servicio ssh al usuario root, modificamos los permisos de la clave privada para garantizar que solo el usuario tenga acceso de lectura.

![image](https://github.com/user-attachments/assets/a65d3d99-0e43-4ad9-847f-bc3412878a49)

Y si ejecutamos el servicio ssh con la clave id_rsa ya somos root.

![image](https://github.com/user-attachments/assets/da03b8c6-0cf6-4880-a0ae-7aaf5d274145)
