# RESOLUCIÓN DE LA MÁQUINA SEEKER

Abrimos la máquina y vemos su IP.

![image](https://github.com/user-attachments/assets/04f078c2-2347-4a35-b79d-ea1846f2e021)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/94859db0-f1d1-4191-969f-2044b7b24d4f)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/2ac0eae5-08ce-4fb3-919c-133d3b4cbac0)

Abrimos la web.

![image](https://github.com/user-attachments/assets/938134c6-6b9b-4cd2-8cea-5c167cf5dcdc)

En el apache, en la página principal vemos una ruta, que después de intentarla poner de muchas maneras y ver para que nos podia servir he descubierto que la parte de "5eEk3r", es un dominio.

![image](https://github.com/user-attachments/assets/953ca2d1-c785-4d5e-891e-6654855039bc)

Para ello tendremos que añadirlo antes al /etc/hosts de esta manera: 

![image](https://github.com/user-attachments/assets/395cb088-f5e7-4856-9ba5-c7f6336a2c61)

Hacemos uso de la herramienta ffuf para buscar posibles subdirectorios para la ruta que tenemos.

![image](https://github.com/user-attachments/assets/c59fb251-5c8a-43eb-9242-fd67173b92d6)

Lo añadimos también en el /etc/hosts, y lo abrimos.

![image](https://github.com/user-attachments/assets/625e6f1a-7af8-497a-9481-5d33a6ebc43e)

![image](https://github.com/user-attachments/assets/97d71168-8806-467f-8b4d-ef7b9ee7eb04)

Abrimos el código fuente y vemos esta pista: 

![image](https://github.com/user-attachments/assets/e9dc2aa6-d6e3-4d6e-9bee-87c48c2c7fbd)

Intentamos inyectar código y solo nos lo codifica, no vamos a liarnos mas la cabeza ya que si el objetivo es intentar acceder al servidor la vulnerabilidad xss en principio no nos servirá para nada.

![image](https://github.com/user-attachments/assets/ed366b79-3a01-4046-a7a4-1eae30ebdaf9)

Volvemos a hacer uso de la herramienta ffuf en busca de otro subdominio.

![image](https://github.com/user-attachments/assets/4408492b-5f5e-45a2-9975-cfc880ddc30e)

Vamos a volver a añadir esta ruta en el /etc/hosts y abrir de nuevo la web.

![image](https://github.com/user-attachments/assets/6772c9a6-9e7e-4e55-b518-536bd7c3485b)

![image](https://github.com/user-attachments/assets/4fef088e-6ce9-4fb8-b4ba-f25a2f11a7f2)

Nos encontramos con una subida de archivos, subimos un archivo.phtml malicioso, ya que php no nos deja.

![image](https://github.com/user-attachments/assets/364fa67a-92e4-4d00-9e6a-6058a210104f)

Si nos vamos a la ruta sin el subdominio "admin", podemos inyectar comandos al ingresar el archivo maliciosos que hemos subido, en nuestra url.

![image](https://github.com/user-attachments/assets/112da34b-ca78-4bb4-b19a-a3e1b704d6dc)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/aa0fb868-8dee-41db-99f0-ac79e0dc8cdd)

Hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/f368d04b-8bff-49e6-b86c-ad633f643980)

Nos convertimos en el usuario astu.

![image](https://github.com/user-attachments/assets/d5ae39fb-78e1-4387-9950-f67c063d9d67)

Listamos los permisos SUID.

![image](https://github.com/user-attachments/assets/38f2dc01-1945-48c1-bd26-7d6f5a73eb78)

Nos vamos al que nos parece mas inetresante, que es el bs64 y vemos que nos codifica el código que le pasamos a base64.

![image](https://github.com/user-attachments/assets/f13ab26d-1742-4b60-8673-7c3b4da15811)

Probamos si podemos hacer un ataque de desbordaminto y vemos el "Segmentation fault" así que podremos realizar un Buffer Overflow.

![image](https://github.com/user-attachments/assets/b8e1b1bb-fe57-482f-9430-50d7ed6fa5bf)

Vamos a pasarnos el binario ejecutable a nuestra máquina para ver con ghidra que hace.

![image](https://github.com/user-attachments/assets/b07c13f2-ecb3-40c1-92e5-06d62d4bed0f)

Dentro del ghidra, encontramos una función "fire", que podemos ver que esta llamando a root por el setuid(0).

![image](https://github.com/user-attachments/assets/ee30b5a4-f619-43f6-910c-1c5126a1f17a)

Vamos a crear un patron para ingresarlo en el gdb del binario.

![image](https://github.com/user-attachments/assets/31c5649f-5bb4-49e1-abeb-39ad63071558)

Ahora ejecutaremos el gdb con el binario y lo añadiremos, cuando lo pida.

![image](https://github.com/user-attachments/assets/5f956a40-7305-4d48-bea8-26c4a79006eb)

Nos da un valor, pero tendremos que ejecutar el comado "ret", para obtener el valor que buscamos.

![image](https://github.com/user-attachments/assets/e609641d-2367-4bcd-aaf8-9a30568c1513)

Sabiendo el valor del ret, ahora sacaremos el offset con este valor, y vemos que es de 72 bytes.

![image](https://github.com/user-attachments/assets/6dec55ed-549d-4b00-b410-ceacb98eaebc)

Y ahora crearemos un script en la máquina víctima para escalar privilegios.

![image](https://github.com/user-attachments/assets/ced94ba6-4717-40a3-9924-9b4dbcfbed89)

Para este script tendremos que indicar varias cosas, una de ellas es la dirección de la función fire, para ello tendremos que ejecutar este comando en la máquina víctima.

![image](https://github.com/user-attachments/assets/cdf22c6d-6fee-47dc-8e41-f50be7e18921)

Le damos permisos al script y lo ajecutamos pero no nos va.

![image](https://github.com/user-attachments/assets/c1739ac3-248c-4474-b69b-d326d09028f8)

Tenemos que cambiar la última letra de la dirección de la función fire (la a por la b), y ya nos funcioanará.

Posible causa: Debido a la forma en que se alinean las instrucciones de la CPU o el compilador optimiza el código, la instrucción de retorno (ret) de la función fire podría estar en un byte diferente al de la dirección 0x40136a. En lugar de sobrescribir exactamente en 0x40136a, sobrescribes un byte adicional, que puede estar en 0x40136b.

Por lo tanto, en lugar de apuntar exactamente a 0x40136a, se apunta a 0x40136b y es eso lo que hace que funcione.

![image](https://github.com/user-attachments/assets/34c50c3e-0292-4e88-a5f1-a7bb3136af95)

Y ya somos root.

![image](https://github.com/user-attachments/assets/755352de-9f7b-4dd3-a567-50138577ccfe)
