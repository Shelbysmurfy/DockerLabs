# RESOLUCIÓN DE LA MÁQUINA ANONYMOUSPINGU

![image](https://github.com/user-attachments/assets/88d6cf8c-7f6b-4ca2-b247-502438d93406)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/9346903e-af54-4992-bc9e-f3b474afe3ab)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/8899abdc-cf77-4e81-82f5-e79ef3fe546b)

Entramosn en el servicio ftp.

![image](https://github.com/user-attachments/assets/b02c4e3a-69c2-4233-8958-39c6c8bbf2f1)

El directorio upload permite subir archivos, nos creamos un archivo maliciosos php.

![image](https://github.com/user-attachments/assets/05d14fdd-f79b-415d-9503-6901671da7fb)

Lo subimos al servicio ftp.

![image](https://github.com/user-attachments/assets/1be797a4-6c29-49ff-bd5e-6d36991d8029)

Abrimos el navegador y entramos al archivo desde el directorio upload.

![image](https://github.com/user-attachments/assets/244409fe-199e-46fb-aebe-27cf5ddb01fe)

Vamos a hacer una revershell.

![image](https://github.com/user-attachments/assets/f26dde0d-2145-4570-b567-8d3f388615e0)

Hacemos un sudo -l y nos sale esto: 

![image](https://github.com/user-attachments/assets/e135309b-baf1-45b5-9eb2-a9bf9681152c)

Nos vamos al GTFObins y seguimos los pasos que nos dice para elevar privilegios como usuario pingu.

![image](https://github.com/user-attachments/assets/6e9a7920-69fa-4071-9fc7-2a8f6b562076)

![image](https://github.com/user-attachments/assets/2f3ccc7b-a558-4e20-88c6-b74d2668138c)

Escalamos privilegios para ser el usuario gladys.

![image](https://github.com/user-attachments/assets/b8afebb8-1602-4103-9cea-3e51134acb35)

![image](https://github.com/user-attachments/assets/55cf5d71-25d5-46d5-ab36-c4cd57a47ef0)

Y volvemos a escalar privilegios para ser usuario root.

![image](https://github.com/user-attachments/assets/0c7be553-d222-4ac9-bb13-f39c683de3ba)








