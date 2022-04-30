![ddiu](https://user-images.githubusercontent.com/91874745/166084192-96e0eaf2-11e4-4956-b58a-315003d3c534.jpeg)

#  Instalación de [***Alpine***](https://alpinelinux.org) en una máquina virtual (Virtual Box) e instalación de [***Docker***](https://www.docker.com)

## ***Primer paso:*** Intalación de [***Alpine***](https://alpinelinux.org) 

  
  1. Una vez instalada la [***VirtualBox***](https://www.virtualbox.org) descargamos [***Alpine***](https://alpinelinux.org) en su [página web](https://alpinelinux.org/downloads/) en la opción descargas. Hay varias opciones, elegimos la opción correcta para nuestro SO en el paratado ***Virtual***.


  ![Captura de pantalla 2022-04-25 072649](https://user-images.githubusercontent.com/91874745/166080546-30b47c81-0103-4ae8-afbd-a8601412b19c.png)


  2. Finalizada la descarga, abrimos ***Virtualbox*** y elegimos en el menú ***Nueva*** y le damos un nombre, en mi caso **Alpine1**. Seleccionamos **opciones avanzadas**, elegimos  el **Tipo** y la **Version** asi como el tamaño de **Memoria**, las demas opciones las dejamos como vienen por defecto. Seguidamente nos pedira que la ubicación del archivo así como el tamaño de nuestro disco virtual y damos click en **crear**.

  ![2](https://user-images.githubusercontent.com/91874745/166080711-e03c338b-1afd-44c4-b056-cb068f9e6cd5.png)



  3. Ahora nos aparecera de lado izquierdo, la elegimos y clicamos en **ajustes**,en la opcion **audio** descarmos la casilla. Dentro de **ajustes-almacenamiento**, en **IDE O SATA** insertamos nuestra imagen virtual y le damos en **aceptar** (en mi caso no aparecía la opcion IDE).
  **Iniciar**, en mi caso, me pide la imagen de disco, ya que en el paso anterior no lo registró en **SATA**.
  
  
  ![3](https://user-images.githubusercontent.com/91874745/166080736-ef46e7a3-9f90-47e9-b478-046f15f939f3.png)


  4. Confirmamos que todo está ok, aparece un mensaje **Welcome to Alpine Linux 3.15** y nos aparece `localhost login:` y escribimos `root` seguido de ***enter***, de momento no tiene contraseña. 

  ![4](https://user-images.githubusercontent.com/91874745/166080814-a8373b9a-4577-43d9-adbd-64eef2a9ebc5.png)


  5. Para empezar el Alpine setup solo hay que escribir un comando que es `setup-alpine` y ***enter***.
  
  
  ![5](https://user-images.githubusercontent.com/91874745/166080877-bfc47971-ae50-4bff-be2f-ce70953d567f.png)

  

  6. Elegimos nuestro teclado, en la opcion `Select keyboard layouts [none]:`, así como su respectiva variante en `Select variant[]:`.
  
  
  ![6](https://user-images.githubusercontent.com/91874745/166080945-4c303333-ff1a-45ea-8ff3-6b973fa937f9.png)


  7. En`Enter system hostname (short form, e.g. 'foo') [localhost]:`, escribimos `node1`

  ![6](https://user-images.githubusercontent.com/91874745/166081127-fd493361-8a51-42a6-ac94-51f9e4b177b0.png)


  8. A partir de aquí casi todo lo dejaremos con valores por **default**, con **enter** bastaría para pasar a las siguientes opciones que son:

  + `Which one do you want to initialize? (or '?' or 'done') [eth0]`

  + `Ip address for eth0 (or 'dhcp', 'none', '?') [dhcp]`

  + `Do you want to do any manual network configuration? [no]`

  9. Ahora nos pedira configurar la contraseña para ***root***
  en:
   `Changing password for root` 
    
   `New password`
   
   ![7 copia](https://user-images.githubusercontent.com/91874745/166081188-8990b00f-7063-4d5d-ad49-cd352265ac81.png)

 

  
  10. Nos pedira que configuremos nuestra zona horaria con `Which timezone are you in? ('?'  for list) [UTC]`, y para ver la lista escribimos `?` donde nos aparecera Europa y después, en `sub-timezone` seleccionamos `Madrid`.

  ![7](https://user-images.githubusercontent.com/91874745/166081341-952d9d07-6a37-4cab-a393-00b8497497f6.png)


  11. `HTTP/FTP proxy URL? (e .g. 'http://proxy_8080', or 'none')[none]` solo **enter**.

      Lo mismo para `Wich NTP CLIENTE TO RUN? ('busybox', 'openntpd', 'chrony' or 'none') [chrony]`, **enter**, ya que por defecto selecciona ***chrony***.
  
  12. En `Enter mirror number (1-72) or URL to add (or r/f/e/done) [1]` lo dejamos con la opción por default.
  
  
  ![10](https://user-images.githubusercontent.com/91874745/166081464-8846ee63-e046-4001-9b30-1cdcdce47ce2.png)

 

  13. `Wich disk(s) would you like to use? (or '?' for help or 'none')[none]`, con el signo de interrogación podemos asegurarnos de los discos que tenemos, en mi caso elijo `sda` y nos preguntará `How would you like to use it? ('sys', 'data', 'lvm' or '?' for help)[?]` y escribimos `sys` y comenzará a intalar paquetes. Nos pregunta `WARNING: Erase the above disk(s) and continue? [y/N]:` seguido de `y` para confirmar. Levará un minuto el proceso. 

  ![11](https://user-images.githubusercontent.com/91874745/166081587-638d7875-7eae-44f0-b79c-26a97ae07ae1.png)


  14. Ahora hay que hacer un `reboot` cuando aparece el mensaje `Ìnstallation is complete Please reboot`, pero no lo haremos, en lugar de eso: `node1:~# poweroff`. 
  
  15. Una vez que el sistema está apagado, seleccionamos nuestra [***Alpine***](https://alpinelinux.org) y en ajustes de red en el apartado **Conectado a:** seleccionamos **Adaptador puente**, después en **Ajustes-Sistema** desmarcamos **Disquete y Óptica** ya que ahora no necesitamos hacer el boot desde la ISO sino desde el disco duro. Ahora volvemos a iniciar nuestra [***Alpine***](https://alpinelinux.org) y nos preguntará `node1 login:` a lo que escribimos `root` y después la contraseña que habíamos creado en paso anteriores y si todo ha ido bien nos saldrá en mensaje de bienvenida (`Welcome to Alpine!`).


  ![12](https://user-images.githubusercontent.com/91874745/166081686-3f2d70c0-b5c0-44a6-8d7e-97fe07b1438e.png)
  
  ![13](https://user-images.githubusercontent.com/91874745/166081732-b7d0839e-9d0f-4dbc-86f2-6b34da929db3.png)
  
  ![15](https://user-images.githubusercontent.com/91874745/166081795-f496f9d5-6d86-4af6-8259-b93aa6d9f209.png)


  
  16. El último paso para poder acceder desde el exterior es abrir un sshd con la configuración usando el editor **vi**: `node1:~# vi /etc/ssh/sshd/_config`. Una vez dentro, buscamos la línea que contenga `#PermitRootLogin in prohibit-password`y quitaremos la el símobolo **#** y cambiaremos la línea para qque quede así: `PermitRootLogin in yes`, guardamos y salimos con **wq** para escribir y guardar. Ahora reiniciamos con `node1:~# service sshd restart`.

  

  ![20](https://user-images.githubusercontent.com/91874745/166082382-a4820476-254a-49e4-b75b-fe4b0ca22cd4.png)


  

  17. Continuamos con la línea `node1:~# ip a`
  que intentaremos loguearnos con la ip que nos muestra, en este caso la segunda, pero para este paso abriremos la consola de ***Git*** y escribiremos `$ ssh root@192.168...`. Nos preguntará si estamos seguros de continuar y confirmamos con `yes` e introducimos nuestra contraseña.
   Veremos nuevamente, pero en la `Git bash` el mensaje `Welcome to Alpine` y con esto confirmamos que no estamos usando la **VirtualBox**, sino que estamos usando un ssh client. En este punto estamos listo para instalar [***Docker***](https://www.docker.com).
   
   
  ![20 copia](https://user-images.githubusercontent.com/91874745/166082530-ca834489-7d84-4f17-a85f-9cab0500ae2e.png)
  
  
  ![21](https://user-images.githubusercontent.com/91874745/166082666-31e7a842-394d-43a8-a489-a92521fdc8e3.png)

  
 
  
  ## ***Segundo paso:*** Intalación de [***Docker***](https://www.docker.com)

  1. Ya que hemos hecho todos los pasos anteriores, para instalar la imagen de [***Docker***](https://www.docker.com) necesitamos configurar el repositorio de [***Alpine***](https://alpinelinux.org). Primero hay que editar un archivo con la siguiente instrucción: `node1:~# vi /etc/apk/repositories`.  Con el editor **vi**, veremos algunos repositorios, solo hay que quitar todos los hashtag **"#"** y guardar los cambios.


  ![24](https://user-images.githubusercontent.com/91874745/166083054-c9607552-584b-40e0-b2f6-e8a22e599f76.png)

  ![22](https://user-images.githubusercontent.com/91874745/166082892-78d165aa-09f3-4b94-9c6a-5e5d7b73da46.png)
  
  ![23](https://user-images.githubusercontent.com/91874745/166082937-d751adf3-a293-4186-a2b6-6c9fa6c7535f.png)


  2. Instalación de [***Docker***](https://www.docker.com). Con el comando `node1:~# apk add docker` y comenzará la instalación; con esto ya lo tendremos instalado una vez finalizado el proceso. 

  ![25](https://user-images.githubusercontent.com/91874745/166083187-b878e506-1947-46e9-9e5b-b7f35c0b6f97.png)
  
  ![26](https://user-images.githubusercontent.com/91874745/166083313-5f234057-9c44-4b3b-9aa6-ee05d47cb9d7.png)

  
  3. Para iniciar el **docker service**:
  `node1:~# service docker start` y podemos ver algunas opciones más como `node1:~# docker images` que estará en blanco, pero podríamos añadir.
  
  ![27](https://user-images.githubusercontent.com/91874745/166083354-a21f31f8-c266-4f21-81e8-97c5bd381100.png)


  4. Probamos con `node1:~# docker version` y ver la versión que tenemos o `node1:~# docker info`y ver la información. 
  
  ![28](https://user-images.githubusercontent.com/91874745/166083386-f32e6092-f36f-4cb2-9918-ca0e1423c181.png)
  
  
  
  ![29](https://user-images.githubusercontent.com/91874745/166083500-b9c16448-261d-4988-a28e-1bfbc8e71547.png)



  5. El último paso es ejecutar `node1:~# docker run hello-world` y hará una `Pull`, ya que en principio no tendrá la **image 'hello-world:latest'** localmente. Una vez descargada nos aparecerá el mensaje `Hello from Docker` seguido de `This message shows that your installation appears to be working correctly`; y con eso confirmamos que nuestra instalaión de 
  [***Docker***](https://www.docker.com) funciona correctamente. 
  
  
  ![30](https://user-images.githubusercontent.com/91874745/166083587-080b7237-c63a-4118-be1d-1035ba7cfd13.png)

  
  ![iu](https://user-images.githubusercontent.com/91874745/166083632-67fa81b8-356a-4990-84ee-18875512f6cc.gif)

  
