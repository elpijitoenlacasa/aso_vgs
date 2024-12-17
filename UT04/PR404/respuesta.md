# Paso 1.- Configuramos la red de la maquina y la cambiamos el nombre para que se vean entre ellas
![1](captura1.png)
![2](captura2.png)
### Desactivamos el firewall y comprobamos que se ven entre ellas haciendo ping
![3](captura3.png)
### Cambiamos tambien el hostname
![4](captura4.png)

# Paso 2.- Configuracion de acceso remoto al equipo
### Desde el equipo core nuevo habilitamos el remoting
![5](captura5.png)
### Vamos ahora al equipo desde el que gestionaremos (winserver de escritorio)
### vemos primero el archivo trusted host y comprobamos que falta la ip que tenemos que meter
![6](captura6.png)
### Añadimos dicha ip
![7](captura7.png)
### comprobamos q se añadio bien
![8](captura8.png)
# Ahora ya se pueden enviar comandos a esa ip tambien

# Paso 3.- Creacion de usuarios de manera remota
### Usamos el invoke command para crear los usuarios primero en una ip y luego en otra
![9](captura9.png)
![10](captura10.png)
### Ahora lo mismo en la otra ip
![11](captura11.png)
![12](captura12.png)
# Paso 4.- HTTPS
### Configuramos el certificado
![13](captura13.png)
![14](captura14.png)
![15](captura15.png)
![16](captura16.png)
### Aqui comprobamos que escucha en el listener creado por https con su certificado
