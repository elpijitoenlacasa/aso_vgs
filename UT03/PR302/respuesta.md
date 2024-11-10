### Crea un script que presente un menú con las operaciones básicas (suma, resta, multiplicación, división) y solicite al usuario que elija una operación. El script debe ejecutar la operación seleccionada utilizando case.
```bash
echo "Menu de operaciones: Suma, Resta, Multiplicacion, Division"
read -p "dame un numero: " num1
read -p "dame otro: " num2
read -p "escoge una operacion  marcando su simbolo: " operacion
case $operacion in
        +)
                res=$(( $num1+$num2 ))
                echo "$res";;
        -)
                res=$(( $num1-$num2 ))
                echo "$res";;
        *)
                res=$(( $num1*$num2 ))
                echo "$res";;
        /)
                res=$(( $num1/$num2 ))
                echo "$res";;
esac
```
### Haz un script que solicite al usuario un nombre de archivo y, usando case, determine si es un archivo de texto (.txt), un archivo comprimido (.zip o .tar.gz), o cualquier otro tipo de archivo.
```bash
read -p "Dime nombre de archivo " archivo
read -p "dime la extension" ext
case $ext in
        txt)
                echo "$archivo es un fichero de texto";;
        zip)
                echo "$archivo es un zip";;
esac
```
### Crea un script que ofrezca un menú para convertir entre diferentes unidades de longitud (metros a kilómetros, pies a metros, etc.) utilizando case para gestionar las conversiones.
```bash
read -p "cuanta distancia es " num
read -p "que son " dis
case $dis in
        m)
                res=$(( $num / 1000 ))
                echo "$res";;
        km)
                res=$(( $num * 1000 ))
                echo "$res";;
        pies)
                res=$(( $num * 0.30 ))
                echo "$res";;
esac
```
### Realiza un script que presente un menú con varias opciones de configuración del sistema: por ejemplo, apagar, reiniciar o cerrar sesión. Usa case para gestionar las opciones seleccionadas.
```bash
while true; do
    echo "Seleccione una opción:"
    echo "1) Apagar el sistema"
    echo "2) Reiniciar el sistema"
    echo "3) Cerrar sesión"
    echo "4) Salir"

    read -p "Ingrese su opción: " opcion

    case $opcion in
        1)
            echo "Apagando el sistema..."
            sudo shutdown now
            ;;
        2)
            echo "Reiniciando el sistema..."
            sudo reboot
            ;;
        3)
            echo "Cerrando sesión..."
            gnome-session-quit --logout --no-prompt
            ;;
        4)
            echo "Saliendo..."
            exit 0
            ;;
        *)
            echo "Opción no válida. Por favor, intente de nuevo."
            ;;
    esac
done
```
### Haz un script que solicite un número entre 1 y 7 al usuario y muestre el nombre del día correspondiente (1 para lunes, 2 para martes, etc.) utilizando case.
```bash
read -p "Dime un numero del 1 al 7 " num
case $num in
        1)
            echo "Es lunes";;
        2)
            echo "Es martes";;
        3)
            echo "Es miercoles";;
        4)
            echo "Es jueves";;
        5)
            echo "Es viernes";;
        6)
            echo "Es Sabado";;
        7)
            echo "Es Domingo";;
esac
```
### Realiza un script que solicite una calificación numérica y, usando case, la clasifique como "Sobresaliente", "Notable", "Aprobado", o "Suspenso" según el rango de valores.
```bash
read -p "Ingrese una calificación numérica (0-10): " calificacion
case $calificacion in
    10)
        echo "Calificación: Sobresaliente"
        ;;
    9)
        echo "Calificación: Sobresaliente"
        ;;
    8)
        echo "Calificación: Notable"
        ;;
    7)
        echo "Calificación: Notable"
        ;;
    6)
        echo "Calificación: Aprobado"
        ;;
    5)
        echo "Calificación: Aprobado"
        ;;
    4)
        echo "Calificación: Suspenso"
        ;;
    3)
        echo "Calificación: Suspenso"
        ;;
    2)
        echo "Calificación: Suspenso"
        ;;
    1)
        echo "Calificación: Suspenso"
        ;;
    0)
        echo "Calificación: Suspenso"
        ;;
    *)
        echo "Entrada no válida. Por favor, ingrese un número entre 0 y 10."
        ;;
esac
```
### Haz un script que solicite un número y lo clasifique como "Positivo", "Negativo" o "Cero".
```bash
read -p "Dime un numero " num
case $num in
       -*)
            echo "Es negativo";;
        0)
            echo "Es cero";;
        *)
            echo "es positivo";;
esac
```
### Crea un script que pregunte por el nombre de un servicio y luego presente un menú para iniciar, detener o reiniciar un servicio en Linux (como apache2 o nginx). Usa case para gestionar las opciones y los comandos correspondientes (systemctl start, stop, restart).

Después de realizar la operación solicitada comprueba su código de estado de finalización (recuerda que puedes obtener el estado de finalización de un comando con la variable $? tras ejecutarlo) y muestra un mensaje indicando si la operación se ha realizado correctamente o no.
```bash
#!/bin/bash


read -p "Ingrese el nombre del servicio (ej. apache2, nginx): " servicio

while true; do
    echo "Seleccione una opción:"
    echo "1) Iniciar el servicio"
    echo "2) Detener el servicio"
    echo "3) Reiniciar el servicio"
    echo "4) Salir"

    read -p "Ingrese su opción: " opcion

    case $opcion in
        1)
            echo "Iniciando el servicio $servicio..."
            sudo systemctl start "$servicio"
            if [ $? -eq 0 ]; then
                echo "El servicio $servicio se ha iniciado correctamente."
            else
                echo "Error al iniciar el servicio $servicio."
            fi
            ;;
        2)
            echo "Deteniendo el servicio $servicio..."
            sudo systemctl stop "$servicio"
            if [ $? -eq 0 ]; then
                echo "El servicio $servicio se ha detenido correctamente."
            else
                echo "Error al detener el servicio $servicio."
            fi
            ;;
        3)
            echo "Reiniciando el servicio $servicio..."
            sudo systemctl restart "$servicio"
            if [ $? -eq 0 ]; then
                echo "El servicio $servicio se ha reiniciado correctamente."
            else
                echo "Error al reiniciar el servicio $servicio."
            fi
            ;;
        4)
            echo "Saliendo..."
            exit 0
            ;;
        *)
            echo "Opción no válida. Por favor, intente de nuevo."
            ;;
    esac
done
```