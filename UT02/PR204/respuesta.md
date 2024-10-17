# Solucion practica 204

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