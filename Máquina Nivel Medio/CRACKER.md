# RESOLUCIÓN DE LA MÁQUINA CRACKER

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/57a1335d-a130-42b1-b705-0bdbefea230a)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/28a62405-59fa-4461-8cbf-6303c4ed9e45)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/9f0a2632-2d9d-417c-aa1f-6238655f49eb)

Abrimos la web.

![image](https://github.com/user-attachments/assets/1cb49a84-ceb4-420f-98a5-2b7c12b168bc)

En el código fuente encontramos un posible dominio.

![image](https://github.com/user-attachments/assets/48f56299-dab9-4bf3-86df-b75633fe2106)

Lo añadimos en el /etc/hosts

![image](https://github.com/user-attachments/assets/93e09217-8933-48a0-b817-69fe0ab2a532)

![image](https://github.com/user-attachments/assets/5f829363-47af-411a-b0ea-c2dcde301923)

Hacemos uso de la herramienta ffuf en busca de posibles subdominios.

![image](https://github.com/user-attachments/assets/0ce141d0-ca56-4b58-acce-3272349523ec)

Lo añadimos en el /etc/hosts y volvemos a abrir la web, donde encontramos un archivo que podemos descargar.

![image](https://github.com/user-attachments/assets/af84b5c0-4c80-4cf7-8fcc-c98cc496e532)

![image](https://github.com/user-attachments/assets/4bbdc1b5-8a9d-4712-a3d1-f1e09f4797d7)

Lo ejecutamos y nos pide que introduzcamos un SERIAL, vamos a usar strings para buscar posibles seriales o pistas de SERIAL dentro del archivo.

![image](https://github.com/user-attachments/assets/a84c97d8-e28e-4979-88b4-5af7e4a44f36)

Sabiendo esto vamos a usar ghidra, donde importaremos el archivo que tenemos y vamos a buscar esto que hemos encontrado.

![image](https://github.com/user-attachments/assets/b0268934-36e7-4dc7-8e3f-d716427e9ecc)

Encontramos 4 archivos, en dos de ellos encontramos un posible SERIAL.

![image](https://github.com/user-attachments/assets/88bedfc1-63c8-4192-970e-731f89f7d89a)

Lo ponemos en el formato correcto "47378-10239-84236-54367-83291-78354" y lo introducimos para poder acceder.

![image](https://github.com/user-attachments/assets/850c2ef0-6199-4960-acd9-18accb7bc172)

Accedemos y encontramos una posible contraseña "#P@$$wOrd!%#S€c7T".

![image](https://github.com/user-attachments/assets/731b5a95-6eff-4cf8-aa88-7de13303e64a)

Hacemos hydra con una lista de usuarios y la contraseña obtenida pero no funciona.

Vamos a hacer un cewl de la página web en busca de una lista de posibles usuarios.

![image](https://github.com/user-attachments/assets/1ba8a948-95e0-46a8-9eb2-0ef891b942d2)

Volvemos a hacer hydra y conseguimos unas credenciales válidas.

![image](https://github.com/user-attachments/assets/0b092990-bf0f-45aa-9b62-281f2a69a24b)

Nos conectamos al servicio ssh con las credenciales obtenidas "cracker:#P@$$w0rd!%#S€c7T".

![image](https://github.com/user-attachments/assets/c35f00f1-8b67-4a81-abee-9d54c300b167)

Hacemos ls y tenemos la primera credencial, la del user.

![image](https://github.com/user-attachments/assets/9410d90e-f92a-42be-8f58-9f5685146b72)

No encontramos nada, así que probamos la credencial que hemos usado para el user cracker, para el root, pero no nos funciona.

Pero si probamos el SERIAL como contraseña del usuario root ganamos acceso.

![image](https://github.com/user-attachments/assets/e8427040-fefc-4238-bdb6-e32fd87757b7)

Y encontramos la segunda flag, la del usuario root.

![image](https://github.com/user-attachments/assets/78238b98-803e-4508-90c9-23784b0ce530)
