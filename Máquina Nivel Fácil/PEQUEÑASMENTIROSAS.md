# RESOLUCIÓN DE LA MÁQUINA PEQUEÑASMENTIROSAS

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/e3c14feb-1faf-4f80-921c-66bc294b38c9)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/8c2d364b-7a5c-4bdd-8b0e-2966d15871d8)

Ahora hacemos un escaneo de el puerto que hemos visto que está abierto para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/9b8c48fd-6bac-42e9-9ff7-2f0ff76ff4e4)

Abrimos la página web.

![image](https://github.com/user-attachments/assets/220dd146-58fc-46af-bcfa-250032d9b3e4)

Hacemos fuerza bruta con hydra para buscar posibles credenciales.

![image](https://github.com/user-attachments/assets/3c199699-79f5-4674-ab56-e18bb3bd52df)

Entramos al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/e71f555c-5b3d-40ab-ac25-3828718d97dc)

Recordamos que los archivos asociados con los servidores se almacenan en el directorio /srv.

![image](https://github.com/user-attachments/assets/d8d9a205-4245-44f4-b9a0-671768e6d079)

Vamos mirando todos los archivos y hay uno que dice que descubramos la contraseña, yu nosotros sabemos que este usuario existe.

![image](https://github.com/user-attachments/assets/5e94647e-12b7-424c-9bbe-de7b7a6ef578)

Nos pasamos el hash_spencer para poder ver si contiene la contraseña que buscamos.

![image](https://github.com/user-attachments/assets/834e5689-07e0-47b3-a1c9-5abeea7fe31c)

Lo decodeamos y sacamos una posible contraseña.

![image](https://github.com/user-attachments/assets/0e18d424-a3f8-4f94-b075-5b69f70cad80)

Nos conectamos como usuario spencer con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/79d6a3d1-fdb4-49d8-8e29-6ac91a16f8cf)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/666ef362-4c34-4d6e-b85d-4b1e6c14fcbe)

Y ya somos root.

![image](https://github.com/user-attachments/assets/16ef16ed-a7e7-446e-98b2-4978c4256c1a)








