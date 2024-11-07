# PR0303: Ejercicios sobre los comandos while, until y for
## Realiza los siguientes ejercicios en Bash. Es necesario entregar por lo menos 12 ejercicios de los propuestos para que la práctica pueda ser evaluada.

### 1. Contar hasta 10 con for
### Usa un bucle for para contar del 1 al 10 e imprimir cada número en una línea nueva.
```bash
for num in {1..10}
do
    echo "$num"
done
```
### 2. Sumar los primeros 50 números
Usa for para sumar los primeros 50 números naturales y muestra el resultado.
```bash
num=0
for numeros in {1..50}
do
    resultado=$(($num + $numeros))
    echo $resultado
done
```

### 3. Tabla de multiplicar
Pide un número al usuario y usa for para imprimir su tabla de multiplicar del 1 al 10.
```bash                     #!/bin/bash
read -p "Dame un numero " numero
for num in {1..10}
do
        resultado=$(( $numero * $num ))
        echo $resultado
done   
```
### 4. Imprimir cada letra
Pide una palabra al usuario y usa for para imprimir cada letra en una línea nueva.
```bash
no hay que hacerlo
```
### Contar números pares del 1 al 20 con while:
Usa while para mostrar los números pares entre 1 y 20.
```bash
#!/bin/bash
n=1
while [ $n -le 20 ]
do
        if [ $((n % 2)) -eq 0 ];
        then
                echo "$n"
        fi
n=$(( n + 1 ))
done
```
### 6. Suma de dígitos
Pide un número al usuario y usa while para sumar todos sus dígitos. Por ejemplo, 123 debería devolver 6.
```bash
no hay que hacerlo
```
### 7. Cuenta regresiva
Pide al usuario un número inicial y usa until para hacer una cuenta regresiva hasta llegar a cero.
```bash
read -p "dame un numero " numero
until [ $numero -eq 0 ]
do
        echo "$numero"
        numero=$(( $numero - 1 ))
done

```
### 8. Imprimir solo archivos .txt
Usa for para iterar sobre todos los archivos en un directorio y mostrar solo aquellos que terminen en .txt.
```bash
!/bin/bash
for fichero in *
do
        if [[ $fichero == *.txt ]]
        then
                echo "$fichero"
        fi
done
```
### 9. Factorial de un número
Solicita un número al usuario y calcula su factorial usando un bucle for.
```bash
read -p "introduce un numero " num
fact=1
for i in $(seq 2 $num)
do      fact=$(( fact * 1 ))
done
echo el factorial de $num es $facto
```
### 10. Verificar contraseña
Usa until para pedir al usuario que ingrese una contraseña correcta, y repite hasta que la acierte.
```bash
read -p "Introduce la contraseña: " pass
until [ $pass = 1234 ]
do
        echo "no es correcto continua"
        read -p "Introducela otra vez: " pass
done
```
### 11. Adivinar un número
Crea un juego con while en el que el usuario intenta adivinar un número entre 1 y 10. Repite hasta que lo adivine.
```Bash
#!/bin/bash
read -p "Adivina un numero del 1 al 10 dime uno: " num
while [ $num != 5 ]
do
        echo "No es ese "
        read -p "Dame otro " num
        echo "correcto" 
done
```
### 12. Mostrar la fecha n veces
Pide al usuario un número n y usa for para mostrar la fecha y hora actual n veces.
```bash
fecha=$( date )
read -p "Introduce un numero: " num
for fechuni in $(seq 1 $num)
do
        echo "$fecha"
        
done
```
### 13. Promedio de números ingresados
Usa while para pedir números al usuario hasta que ingrese “fin”, luego muestra el promedio.
```bash
suma=0
count=0
read -p "introduce un numero " num
while [ $num != "fin" ]
do
        suma=$(( $suma + $num ))
        count=$(( $count + 1 ))
        read -p "introduce un numero: " num
done
echo Has introducido $count numeros
echo su suma es $suma
echo y su promedio $(( $suma / $count))
```
### 14. Contar palabras en una cadena
Pide al usuario una frase y usa for para contar y mostrar el número de palabras en ella.
```bash
contador=0
read -p " escribe una frase " frase
for num in $frase
do
        contador=$(( $contador + 1 ))
        
done
        echo "$contador"
```
### 15. Juego de adivinar con límites dinámicos
Genera un número aleatorio entre 1 y 100 y pide al usuario que adivine. Usa while y da pistas de si el número es mayor o menor, terminando cuando acierte.
```bash
if [ $num -gt $numero ]
        then
                echo "uno mas pequeño"
        else
                echo "uno mas grande"
        fi
read -p "dame otro" num
done
```
### 16. Archivo con nombres de directorios
Usa for para listar todos los directorios en la ruta actual y escribe sus nombres en un archivo directorios.txt.
```bash
ruta=$(pwd)
for f in $ruta/* 
do
        if [ -d $f ]
        then
                echo $f >> ./directorios.txt
        fi
done
```
### 17. Generar archivos de texto numerados
Pide al usuario un número n y usa for para generar n archivos con nombres como archivo1.txt, archivo2.txt, etc.
```bash

```
### 18. Conteo de vocales en una cadena
Pide al usuario una cadena y usa for para contar el número total de vocales que contiene.
```bash
no se tiene q hacer
```
### 19. Validación de entrada
Usa until para pedir un número entre 1 y 10. Repite hasta que el usuario ingrese un número válido en ese rango.
```bash

```
### 20. Script de copia de seguridad
Crea un script que recorra un directorio y copie todos los archivos .txt a una carpeta backup. Usa for para la iteración y if para verificar el tipo de archivo.
```bash

```