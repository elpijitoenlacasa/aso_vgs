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