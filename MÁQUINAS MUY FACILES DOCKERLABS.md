# RESOLUCIÓN DE LA MÁQUINA INJECTION

Hacemos SQLInjection y sacamos unas credenciales.

![image](https://github.com/user-attachments/assets/ac8f66bf-a1ac-4ab6-baf9-60d6d54e8c56)

![image](https://github.com/user-attachments/assets/d271d386-e272-464c-9164-220e1c40b3cc)

Entramos al servicio ssh y buscamos permisos SUID en el sistema.

![image](https://github.com/user-attachments/assets/bc1599ad-451c-4b38-bdc5-ee2e4f71b4be)

Vemos el "/usr/bin/env", lo buscamos en el GTFObins y escalamos privilegios.

![image](https://github.com/user-attachments/assets/a174dece-25c1-445d-85b5-07a3c339ed1a)

# RESOLUCIÓN DE LA MÁQUINA BORAZUWARAHCTF

Abrimos la web y solo vemos una imagen eso quiere decir que tenemos que hacer Esteganografía.

![image](https://github.com/user-attachments/assets/a3a5dd48-f979-40e3-81b7-12a12fd7fba1)

Hacmeos uso de la herramienta steghide.

![image](https://github.com/user-attachments/assets/84a8bc16-04f9-4f90-9fdf-d097fcab4232)

Hacemos uso de la herramienta exiftool y encontramos el usuario: borazuwarah, solo nos falta la contraseña.

![image](https://github.com/user-attachments/assets/58c7d2b8-fe10-40da-b62b-5c3c25176336)

Hacemos hydra y escalada de privilegios facil, usando sudo -l.

# RESOLUCIÓN DE LA MÁQUINA BREAKMYSSH

Solo tenemos el servicio ssh activo, hacemos hydra buscando la contraseña del usuario root.

![image](https://github.com/user-attachments/assets/f8f54618-9de6-48d8-9305-2c4099583dd6)

Y ya somos root.

![image](https://github.com/user-attachments/assets/95c24626-a810-4015-bab0-73b7f24dc267)

# RESOLUCIÓN DE LA MÁQUINA FIRSTHACKING

Solo hay el puerto 21 abierto (ftp).

![image](https://github.com/user-attachments/assets/bd2f4ff7-e4ee-4bf1-8c41-d45e74eb895d)

Hay dos maneras de explotar la versión que tiene el ftp, antes de explotarla haremos un searchsploit.

![image](https://github.com/user-attachments/assets/89cd1f1c-967f-45de-a310-519e2c4797c8)

Con msfcosole estos serías los pasos a seguir.

![image](https://github.com/user-attachments/assets/c0a5b63a-04bd-43e1-b389-7a2e69b1c900)

Y con python estos.

![image](https://github.com/user-attachments/assets/199c2681-8498-408d-a2c6-f8a8c13b5c76)

# RESOLUCIÓN DE LA MÁQUINA OBSESSION

Entramos estas dos pistas.

![image](https://github.com/user-attachments/assets/376e83cc-5523-49be-8579-d42d0077f5df)

![image](https://github.com/user-attachments/assets/f5aba399-d517-4a4d-ac00-bb8a449e79d1)

Tanto en la página web como en la conversación que hemos sacado de un archivo de el servicio ftp esta el usuario russoski.

Por tanto hacemos hydra para buscar la contraseña de este usuario.

![image](https://github.com/user-attachments/assets/2b6dbe2c-3f1f-411f-b5a0-c482388cb6c6)

Hacemos sudo -l en el servicio ssh y nos sale esto.

![image](https://github.com/user-attachments/assets/d1fb7221-0366-47dc-b0b3-f64a84d7dc8d)

Vamos al GTFObins, seguimos los pasos que nos dice y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/f831c3c5-5f5b-4fe1-8634-ab0259a35b26)

# RESOLUCIÓN DE LA MÁQUINA TRUST

No encontramos nada en la página web, hacemos fuerza bruta con gobuster.

![image](https://github.com/user-attachments/assets/186ee775-c3be-47fb-aad2-0c2db22f0a03)

![image](https://github.com/user-attachments/assets/4d9628a5-807a-429d-a08b-45a48086d3d3)

Hacemos hydra para buscar la contraseña del usuario: mario

![image](https://github.com/user-attachments/assets/c525a426-dab0-4789-9078-58a9bb46d500)

Hacemos sudo -l, nos vamos al GTFObins para buscar como escalar privilegios con vim.

![image](https://github.com/user-attachments/assets/5971ff57-ed12-46b5-9884-2c45a7531ddc)

Conseguimos acceso como root.

![image](https://github.com/user-attachments/assets/c16b7197-3864-4117-b6b9-4effd56a2bee)

# RESOLUCIÓN DE LA MÁQUINA VACACIONES

Abrimos el código fuente de la página y nos encontramos con esta pista: 

![image](https://github.com/user-attachments/assets/d270dca1-1557-4cc8-a582-ab9b001db7f2)

Hacemos hydra con los dos usuarios pero solo uno de ellos nos devuelve respuesta.

![image](https://github.com/user-attachments/assets/da3521a4-4b33-4d3c-bb78-18788dcd8fed)

En el mensaje del código fuente nos dice que ha enviado un correo al usuario camilo, así que vamos a verlo.

![image](https://github.com/user-attachments/assets/cae2f31c-8149-4808-b128-87fc041fe411)

Nos conectamos como el usuario juan con las credenciales obtenidas, hacemos sudo -l y seguimos los pasos del GTFObins.

![image](https://github.com/user-attachments/assets/0d2f53b3-07fa-40a7-b131-e2cfa9c2fd98)

![image](https://github.com/user-attachments/assets/8670767b-7935-4bb6-ab79-bfdfb87f31bc)

Y ya somos root.

![image](https://github.com/user-attachments/assets/f1620fb4-82c4-4776-ad4b-b316ecbcbbab)


