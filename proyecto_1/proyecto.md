# Proyecto Primera Evaluacion
### Victor Gonzalez Suarez
## Realizacion de un script que analice la red
### Aqui tenemos el script


```bash
#!/bin/bash

# Solicitar al usuario una dirección IP con la mascara que solo puede ser de 8, 16, 24
while true; do
  read -p "Introduce la IP con la mascara: " ip
  if [[ $ip =~ ^([0-9]{1,3}\.){3}[0-9]{1,3}/(8|16|24)$ ]]; then
  
  else
    echo "Error: Solo se permiten máscaras de red /8, /16 y /24. Inténtalo de nuevo."
  fi
done

read -p "Introduce el rango de puertos (p.e. 1-1024): " puerto
read -p "Introduce el nombre del archivo de salida: " file

# Mostrar encabezado
echo "Analizando la red $ip..."
echo "Resultado del análisis de la red $ip" > "$file"
echo "Fecha: $(date)" >> "$file"
echo "----------------------------------------" >> "$file"

# Función para obtener la dirección MAC
detect_mac() {
  local ipp=$1
  macc=$(ip neigh show $ipp | grep -oE '([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}')
  if [ -z "$macc" ]; then
    macc="Desconocida"
  fi
  echo "$macc"
}

# Escanear la red
echo "Iniciando escaneo de red..."
ips_detected=()
iniciotiempo=$(date +%s)
for ippp in $(nmap -n -sn $ip | grep 'Nmap scan report for' | awk '{print $5}'); do
  echo "Equipo detectado: $ippp"
  echo "IP: $ippp" >> "$file"
  ips_detected+=("$ippp")

  # Obtener dirección MAC
  mac=$(detect_mac $ippp)
  echo "Dirección MAC: $mac"
  echo "Dirección MAC: $mac" >> "$file"

  # Detección del sistema operativo por TTL
  ttl=$(ping -c 1 -W 1 $ip | grep 'ttl=' | awk -F'ttl=' '{print $2}' | awk '{print $1}')
  echo "$ttl"
  if [ "$ttl" -lt 64 ]; then
    os="Linux"
  else
    os="Windows"
  fi

  echo "Sistema operativo detectado: $os"
  echo "Sistema operativo: $os" >> "$file"

  # Escaneo de puertos abiertos
  echo "Escaneando puertos abiertos en $ippp..."
  IFS='-' read -r port_start port_end <<< "$puerto"
  for port in $(seq $port_start $port_end); do
  if nc -zv -w 1 $ip $port &> /dev/null; then
    if [[ -f tcp.csv ]]; then
      service=$(grep "^$port," tcp.csv | awk -F',' '{print $2}')
      else
      service="Desconocido"
    fi
      echo "  Puerto abierto: $port ($service)"
      echo "  Puerto abierto: $port ($service)" >> "$file"
  fi
  done
  echo "----------------------------------------" >> "$file"
done

# Calcular el tiempo total de escaneo
end_time=$(date +%s)
elapsed_time=$((end_time - iniciotiempo))
echo "Tiempo total de escaneo: $elapsed_time segundos"
echo "Tiempo total de escaneo: $elapsed_time segundos" >> "$file"

# Finalizar y mostrar mensaje
echo "Escaneo completado. Resultados guardados en $file"
```

# PASO 1 
### En primer lugar tenemos la parte en la que se solicita la ip al usuario
```bash
while true; do
  read -p "Introduce la IP con la mascara: " ip
  if [[ $ip =~ ^([0-9]{1,3}\.){3}[0-9]{1,3}/(8|16|24)$ ]]; then
    break
  else
    echo "Error: Solo se permiten máscaras de red /8, /16 y /24. Inténtalo de nuevo."
  fi
done

read -p "Introduce el rango de puertos (p.e. 1-1024): " port_range
read -p "Introduce el nombre del archivo de salida: " file
```
## En esta parte pedimos la ip al usurio y la guardamos en una vaiable en la cual abrimos un if que compruebe si tiene todos esos parametros y solo pueda ser /8, /6 y /24. Le decimos break para que pare cuando se cumpla la condicion si no nos mostrara un mensaje de error. Despues le pedimos que nos d un rango de puertos donde va a buscar  el nombre del archivo donde redireccionaremos el resultado guardado en variables todo
# Paso 2
```bash
# Mostrar encabezado
echo "Analizando la red $ip..."
echo "Resultado del análisis de la red $ip" > "$file"
echo "Fecha: $(date)" >> "$file"
echo "----------------------------------------" >> "$file"
```
## En esta parte mostramos como queremos que se vea elencabezado del analisis los campos que va a recoger que seran los de las variables anteriores le redireccionamos para añadirlo al nombre de archivo que ha solicitado al usuario anteriormente. En cuanto a la fecha redireccionamos la funcion ```date``` en el archivo de la variable file tambien
# Paso 3
```bash
# Función para obtener la dirección MAC
detect_mac() {
  local ipp=$1
  macc=$(ip neigh show $ipp | grep -oE '([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}')
  if [ -z "$macc" ]; then
    macc="Desconocida"
  fi
  echo "$macc"
}
```
## El comando ```ip neigh``` es para la mac muestra la asociación entre direcciones IP y direcciones MAC en la red local, indicando qué equipos están alcanzables y qué interfaces están siendo utilizadas. Despues filtramos con grep y el parametro oE para que busque en la condicion que le ponemos. Por tanto en el if hacemos un comprobante si existe y va vacio lo que hemos recogido en la variable mac nos pone que es desconocida
# Paso 4
```bash
# Escanear la red
echo "Iniciando escaneo de red..."
ipsdetectadas=()
iniciotiempo=$(date +%s)
for ippp in $(nmap -n -sn $ipp | grep 'Nmap escanea for you' | awk '{print $5}'); do
  echo "Equipo detectado: $ippp"
  echo "IP: $ippp" >> "$file"
  ipsdetectadas+=("$ippp")
```
## Se hace la funcion para almacenar las ips detectadas en el escaneo. ```+%s```, Indica que date devolverá el tiempo en segundos. Este for es el inicio de un bucle for que recorre las direcciones IP detectadas por el comando nmap. ```nmap``` Herramienta para explorar redes. ```-n``` Desactiva la resolución de nombres de host para que el escaneo sea más rápido. ```-sn``` Realiza un escaneo "ping" (sin buscar puertos abiertos). El comando ```awk print $5``` selecciona el quinto campo que se le pasa a grep

# Paso 5
```bash
 # Obtener dirección MAC
  mac=$(detect_mac $ippp)
  echo "Dirección MAC: $mac"
  echo "Dirección MAC: $mac" >> "$file"
  ```
## LLamamos a la funcion anterior para que se muestre en pantalla junto a la ip ya escaneada

# Paso 6
```bash
# Detección del sistema operativo por TTL
  ttl=$(ping -c 1 -W 1 $ippp | grep 'ttl=' | awk -F'ttl=' '{print $2}' | awk '{print $1}')
  echo $ttl
  if [ "$ttl" -lt 64 ]; then
    os="Linux"
  else
    os="Windows"
  fi

  echo "Sistema operativo detectado: $os"
  echo "Sistema operativo: $os" >> "$file"
  ```
  ## Definimos la variable ttl y le metemos un subshel con el comando ```ping``` y ```-c``` 1: Indica que solo se enviará 1 paquete. ```-W``` 1: Define el tiempo de espera (en segundos) para recibir una respuesta antes de que se dé por concluido el intento. En las condiciones ponemos que si el resultado de ttl es 64 sera linux y si es 128 es windows todo lo demas desconocido.

  # Paso 7
  ```bash
   # Escaneo de puertos abiertos
  echo "Escaneando puertos abiertos en $ippp..."
  IFS='-' read -r port_start port_end <<< "$puerto"
  for port in $(seq $port_start $port_end); do
    nc -zv -w 1 $ippp $port &> /dev/null
    if [ $? -eq 0 ]; then
      service=$(grep "^$port," tcp.csv | awk -F',' '{print $2}')
      echo "  Puerto abierto: $port ($service)"
      echo "  Puerto abierto: $port ($service)" >> "$file"
    fi
  done
  echo "----------------------------------------" >> "$file"
done
```
## Aquí, el valor de la variable $puerto se espera que sea un rango en el formato x-y (por ejemplo, 80-443). Esta línea usa el delimitador - para dividir el valor en dos partes: el puerto inicial ($port_start) y el puerto final ($port_end).Escaneo de puertos:
```for port in $(seq $port_start $port_end); do```
### Este ciclo for recorre todos los puertos dentro del rango especificado, desde $port_start hasta $port_end. La función seq genera una secuencia de números, que corresponden a los puertos.
Escaneo de cada puerto con nc
```nc -zv -w 1 $ip $port &> /dev/null```
### Para cada puerto en el rango, el script ejecuta nc (Netcat) con las siguientes opciones:
- -z: Realiza un escaneo sin enviar datos (solo para comprobar si el puerto está abierto).
- -v: Modo verbose, para mostrar más detalles de la conexión.
- -w 1: Establece un tiempo de espera de 1 segundo.
### El comando se ejecuta de manera que toda la salida se redirige a /dev/null (es decir, no se muestra en la pantalla).

### ```if [ $? -eq 0 ]; then```
### El código if verifica el valor de retorno del comando nc ($?). Si es 0, significa que el puerto está abierto, ya que Netcat retornó un éxito.

Identificación del servicio en el puerto:

## service=$(grep "^$port," tcp.csv | awk -F',' '{print $2}') Si el puerto está abierto, el script busca el puerto en un archivo CSV llamado tcp.csv, y extrae el servicio asociado al puerto. Se asume que el archivo tcp.csv tiene un formato con el puerto seguido por el nombre del servicio, separados por comas. awk extrae el nombre del servicio.

Mostrar y guardar el resultado

### echo "  Puerto abierto: $port ($service)"echo "  Puerto abierto: $port ($service)" >> "$file" Imprime en pantalla el puerto abierto y el servicio asociado, y también guarda esta información en un archivo cuyo nombre está almacenado en la variable $file.

# Paso 8
## 
```bash
# Calcular el tiempo total de escaneo
end_time=$(date +%s)
elapsed_time=$((end_time - iniciotiempo))
echo "Tiempo total de escaneo: $elapsed_time segundos"
echo "Tiempo total de escaneo: $elapsed_time segundos" >> "$file"

# Finalizar y mostrar mensaje
echo "Escaneo completado. Resultados guardados en $file"
```
## Se le pasa en la variable endtime la funcion date que hicimos antes y hacemos otra variable pasanadole un subshel que este recogida la dicha funcion y el inicio del tiempo como rangos se redirecciona el resultado al fihero recogido en la variable ```$file``` Finalmente imprimimos que todos ha sido completado con exito y donde se guardara los resultados.



