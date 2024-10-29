# Ejercicio 1: Comprobación de número par o impar
### 1.- Escribe un script que solicite al usuario un número y determine si es par o impar utilizando una estructura if.

```bash
read -p "Dame un numero: " num
if [ $((num % 2)) -eq 0 ]  
then
        echo "El numero es par"
else
        echo "El numero es impar"
fi
```
# Ejercicio 2: Verificación de archivo
### Crea un script que compruebe si un archivo (cuya ruta pedirá al usuario por teclado) existe y si tiene permisos de lectura. Muestra un mensaje adecuado para cada caso.

```bash


read -p "Dime tu ruta: " ruta
if [ -f $ruta ] && [ -r $ruta ]
then
        echo "El fichero existe y tienes permisos de lectura"
else
        echo "El fichero ni existe ni tienes permisos"
fi
```
# Ejercicio 3: Comparación de dos números
### Realiza un script que solicite dos números al usuario y los compare, mostrando cuál es mayor, o si son iguales.
```bash
read -p "Dime un numero :" num1
read -p "Dime otro :" num2

if [ $num1 -gt $num2 ]
then
        echo "El $num1 es mayor que $num2"
else
        echo "El $num1 es menor que $num2"
fi
if [ $num1 -eq $num2 ]
then
        echo "El $num1 es igual que el $num2" 
fi
```
# Ejercicio 4: Validación de contraseña
### Escribe un script que solicite al usuario una contraseña y verifique si coincide con una contraseña predefinida (que estará almacenada en una variable de tu script). Si es correcta, muestra un mensaje de éxito, de lo contrario, indica que es incorrecta.
```bash
read -p "Contraseña :" pass
contra=1234

if [ $pass -eq $contra ] 
then
        echo "Contraseña correcta, Bienvenido"
else
        echo "Contraseña incorrecta, Lárgate"
fi
```
# Ejercicio 5: Comprobación de directorio
### Crea un script que compruebe si un directorio existe y si tiene permisos de escritura. Si el directorio no existe, crea uno nuevo.
```bash
if [ -d ~/directorio ]&&[ -w ~/directorio ]
then
        echo "El directorio no existe, pero lo voy a crear"
else
        mkdir ~/directorio
fi
```
# Ejercicio 6: Verificar si el usuario es root
### Haz un script que verifique si el script está siendo ejecutado por el usuario root, mostrando un mensaje diferente si no lo es.
```bash
USER_NAME=$(whoami)

if [ "$USER_NAME" != "root" ]; then
    echo "Este script debe ser ejecutado como usuario root."
else
    echo "El script se está ejecutando como usuario root."
fi
```

### Realiza un script que pida una nota numérica y determine si es “Aprobado” (5 o más) o “Suspenso” (menos de 5).

```bash
read -p "Dame un numero " num
contra=1234
if [ $num -ge 5 ]
then
        echo "Aprobado"
else
        echo "Suspenso"
fi
```
### Crea un script que compruebe el espacio libre en disco. Si el espacio es inferior al 10%, muestra un mensaje de advertencia.
```bash
libre=$(df)
if [ $libre -lt 10% ]
then
        echo "Es inferior al 10 %"
else
        echo "No es inferior"
fi
```
### Haz un script que solicite al usuario su edad y determine si es menor, adulto o mayor de edad, según un umbral predefinido (por ejemplo, menor de 18, entre 18 y 65, y mayor de 65).
```bash
read -p "Dime tu edad: " num
if [ $num -lt 18 ]
then
        echo "Es menor de edad"
fi
if [ $num -gt 18 ] && [ $num -lt 65 ]
then
        echo "Mediana edad"
fi
if [ $num -gt 65 ] 
then
        echo "Muy mayor"
fi
```
### Escribe un script que solicite el nombre de un archivo y luego imprima cuántas líneas tiene ese archivo. Verifica que el archivo exista antes de contar las líneas.
```bash
contador=$(wc -l)
read -p "Nombre de archivo " nombre
if [ -e $nombre ]
then
        $contador
        echo "El archivo $nombre tiene $contador"
fi
```