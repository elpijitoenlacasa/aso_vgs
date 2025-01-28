## Realiza las siguientes tareas que se te piden utilizando Powershell. Para contestar lo mejor es que hagas una captura de pantalla donde se vea el comando que has introducido y las primeras líneas de la salida de este.

### 1.- El comando Get-Date muestra la fecha y hora actual. Muestra por pantalla únicamente el año en que estamos.

![1](capture1.png)

### 2.- Uno de los requisitos de Windows 11 es que es procesador tenga TPM habilitado. Powershell dispone del comando Get-TPM que nos muestra información sobre este módulo. Muestra por pantalla, en formato tabla, las propiedades TpmPresent, TpmReady, TpmEnabled y TpmActivated.

![alt text](image.png)
### En los siguientes ejercicios trabajaremos con los ficheros devueltos por el comando Get-ChildItem C:\Windows\System32.

### 4.- Muestra por pantalla el número de ficheros y directorios que hay en ese directorio.

![alt text](image-1.png)

### 5.- Los objetos devueltos por el comando anterior tienen una propiedad denominada Extension, que indica la extensión del archivo. Calcula el número de ficheros en el directorio que tienen la extensión .dll.

![alt text](image-2.png)

### 6.- Muestra los ficheros del directorio con extensión .exe que tengan un tamaño superior a 50000 bytes.

![alt text](image-3.png)

### 7.- Muestra los ficheros de este directorio que tengan extensión .dll, ordenados por fecha de creación y mostrando únicamente las propiedades de fecha de creación (CreationTime), último acceso (LastAccessTime) y nombre (Name).

![alt text](image-4.png)

### 8.- Muestra el tamaño (Length) y nombre completo (FullName) de todos los ficheros del directorio ordenados por tamaño en sentido descendente.

![alt text](image-5.png)

### 9.- Muestra el tamaño y nombre completo de todos los ficheros del directorio que tengan un tamaño superior a 10MB (10000000 bytes) ordenados por tamaño.

![alt text](image-6.png)

### 10.- Muestra el tamaño y nombre completo de todos los ficheros del directorio que tengan un tamaño superior a 10MB y extensión .exe ordenados por tamaño.
![alt text](image-7.png)