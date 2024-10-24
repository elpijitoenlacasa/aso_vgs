# Solucion practica 204
### 1.- Orden Crontab
1.- ¿Qué orden pondrías en crontab en los siguientes casos?

- La tarea se ejecuta cada hora: 
```
Pondria los minutos a la que quiero que se reproduzca por ejemplo el 15 y lo demas todo asteriscos
```
- La tarea se ejecuta los domingos cada 3 horas:
```
0 */3 * * 0
```
- La tarea se ejecuta a las 12 de la mañana los días pares del mes:
```
0 12 */2 * *
```
- La tarea se ejecuta el primer día de cada mes a las 8 de la mañana y a las 8 de la tarde:
```
0 8,20 1 * *
```
- La tarea se ejecuta cada media hora de lunes a viernes:
```
*/30 * * * 1-5
```
- La tarea se ejecuta cada cuarto de hora, entre las 3 y las 8, de lunes a viernes, durante todo el mes de agosto:
```
*/15 3-8 * 8  1-5
```
- La tarea se ejecuta cada 90 minutos:
```
0 */3 * * 0
```

# 2 .-¿Cómo compruebas si el servicio cron se está ejecutando?
```
systemctl status cron

```

# 3.-¿Cuál es el efecto de la siguiente línea crontab? 
    */15 1,2,3 * * * who > /tmp/test
```
La línea de crontab ejecutará el comando who cada 15 minutos durante las horas 1, 2 y 3 de cualquier día, y guardará la salida en /tmp/test, sobrescribiendo el contenido del archivo cada vez que se ejecute.

```

# Indica la ruta del fichero crontab del sistema
```
/etc/crontab

```
# ¿Qué ficheros controlan los usuarios que pueden utilizar el crontab?
```
/etc/cron.allow
/etc/cron.deny

```
# Excepcionalmente se debe iniciar una tarea llamada script.sh todos los lunes a las 07:30h antes de entrar en clase ¿Cómo lo harías?
```
30 7 * * 1 ruta/script.sh

```
# Se ha cancelado la tarea. ¿Cómo listar y luego, suprimir la tarea?
```
Listar tareas: crontab -l
Eliminar una tarea específica: crontab -e
Eliminar todas las tareas: crontab -r

```
# Ejecuta el comando ps -ef para el usuario root cada 2 minutos y redirecciona el resultado a /tmp/ps_result sin sobrescribir los antiguos.
```
sudo crontab -e
*/2 * * * * ps -ef >> /tmp/ps_result

```

# Verifica la lista de tareas en crontab
```
crontab -l    

```


# Crea el usuario asir2 y prohíbele utilizar el crontab.
```
sudo adduser asir2
sudo nano /etc/cron.deny
(Agregar "asir2" en una nueva línea)
```


# Programa crontab para que cada día a las 0:05 se eliminen todos los ficheros que se encuentran en el directorio /tmp.
```
bash

Copiar
5 0 * * * rm -rf /tmp/*
```

# Programa una tarea en el sistema que se lance de lunes a viernes a las 9 de la mañana durante los meses de verano (julio, agosto y septiembre) que escriba en un fichero la hora actual (comando date, aunque tienes que mirar la ayuda para elegir un formato comprensible) seguido del listado de usuarios que hay conectados en ese momento en el sistema (comando who)
```
0 9 * 7,8,9 1-5 (date '+\%Y-\%m-\%d \%H:\%M:\%S' && who) >> /ruta/al/fichero.log
```
# El servicio cron se ayuda de una serie de ficheros y directorios que se encuentran en el directorio /etc. Explica la función de cada uno de los siguientes ficheros/directorios:

- cron.d
- cron.allow
- cron.deny
- cron.daily
- cron.hourly
- cron.monthly
```
- cron.d: Archivos de configuración para tareas programadas a nivel de sistema.
- cron.allow: Lista de usuarios permitidos para usar crontab.
- cron.deny: Lista de usuarios prohibidos de usar crontab.
- cron.daily: Scripts que se ejecutan diariamente.
- cron.hourly: Scripts que se ejecutan cada hora.
- cron.monthly: Scripts que se ejecutan mensualmente.
Compartir

```