# RESOLUCIÓN DE LA MÁQUINA AGUADEMAYO

![image](https://github.com/user-attachments/assets/d2c33c5d-4e80-4f87-bb3d-b90b1b5e8e55)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/17afaaa7-5a62-4bed-b8ed-47c0d9d9a632)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/a85c28e6-e29d-4aef-8cb5-f39c27120f75)

Encontramos esto en el código fuente: 

![image](https://github.com/user-attachments/assets/d574f2b8-33d1-4842-b92e-53825a811221)

Usamos brainfuck decode, para saber que información contiene.

![image](https://github.com/user-attachments/assets/d4623f14-04a2-48d2-b0e4-4d6f511ae847)

Usando gobuster encontramos una imagen, usamos herramientas de esteganografía (steghide y exiftool) y no sacamos ninguna información.

![image](https://github.com/user-attachments/assets/d8856f5f-bebf-46b9-b33e-a8e866760fab)

Como el archivo se llama agua_sshk, probando varias combinaciones, conseguimos entrar en el servicio ssh con el usuario: agua y la contraseña: bebeaguaqueessano

![image](https://github.com/user-attachments/assets/90aeed3b-d9ed-481e-b764-793b66ab7259)

Hacemos sudo -l.

![image](https://github.com/user-attachments/assets/e49265aa-a8f1-4df0-bfad-70c7f01958d0)

Ejecutamos estos dos comandos: 

![image](https://github.com/user-attachments/assets/d80f276d-6f62-4526-8564-6b36590cc9d5)

Seguidamente nos salimos de el servicio y ejecutamos bash -p y ya somos root.

![image](https://github.com/user-attachments/assets/b1be052e-2659-462f-b044-8713204f21d6)
![image](https://github.com/user-attachments/assets/9a761e93-8b1e-43b0-a2d3-da7b194605e2)




