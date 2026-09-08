# Paso para un correcto scaneo de Redes


Variantes: 
```
nmap -sn 10.10.0.0/16
```
Descubrimiento de hosts en la red, IP
## Paso 1: 
Escanear redes con comodines, asterisco 
```
nmap -sn 10.0.5.10-30 192.168.12.100-200 10.5.0.5 192.168.*.1-255
```
Explicación: 
- El comando procesa en paralelo 65,431 direcciones IP distribuidas en los siguientes rangos:

- 10.0.5.10-30: Escanea 21 direcciones IP (desde 10.0.5.10 hasta 10.0.5.30).

- 192.168.12.100-200: Escanea 101 direcciones IP (desde 192.168.12.100 hasta 192.168.12.200).

- 10.5.0.5: Escanea únicamente esta dirección IP específica.

- 192.168.*.1-255: El comodín * equivale a la red completa de clase B 192.168.0.0/16.
- Escanea todas las subredes posibles (192.168.0.x, 192.168.1.x ... hasta 192.168.255.x), evaluando los rangos .1 al .255 en cada una (un total de 256 subredes × 255 IPs = 65,280 direcciones).

Resultado final: Nmap te entregará una lista limpia mostrando únicamente las direcciones IP de los equipos activos y sus direcciones MAC (si están en la red local), omitiendo los puertos o servicios en ejecución.
* = escanea todos los valores
-sn = solo es para scaneo de redes
## Paso 2: 
IMPORTANTE: 65535 numero de todos los puertos
nmap -p1-65535 10.0.5.128
```
nmap -p- 10.0.5.128
```
-> scaneo total, es basico y es lo principal. 
Si no se colocan los puertos, automaticamente scanea los 1000 puertos
```
nmap -P0 -p- 10.0.5.128
```
-> No scanea host, solo scaneo de todos los puertos Puertos.
P0 = No haga descubrimento de redes 
Siguiente paso.
## Paso 3
Paso escaneo de Versiones 
```
nmap -P0 -p- -sV 10.0.5.128
```
-sV = scaneo de versiones
```
nmap -P0 -p- -sV -O 10.0.5.128
````
-O = Sistema Operativo 
```
nmap -P0 -p- -sV -O -sC 10.0.5.128
```
```
nmap -P0 -p- -A 10.0.5.128
```
-A = scaneo todas las 3 alternativas que hemos realizado en el paso 3
```
nmap -P0  -sS -p- -A 10.0.5.128
```
 Comando base para scanear tus objetivos 
-sS -> Utilizas el comando con altos previlegios.
## Paso 4
Comando para hacer un barrido rapido y silencioso
```
sudo namp -Pn -sS -p- 192.168.1.12 
```
Ya sabiendo los puerto que debemos analizar podemos usar este comando para verificar sus versiones. 
```
sudo nmap -Pn -A- -p 80,22 192.168.1.12
```
nota. Los puerto son elegidos por ti 
## Paso 5 
Como hacemos para guardar todos nuestro reportes con exito
- Primero creamos el archivo con la extención .xml
```
sudo nmap -Pn -sn 192.168.1.12 -oX nombre.xml
```
Nota. El comando que vayas a auditar el resultado es decicion tuya 
- Segundo descargamos la herramienta a utilizar
```
sudo apt update && sudo apt install -y xsltproc
```
- Tercero ejecutamos la herramiente
```
xsltproc nombre.xml -o reporte.html
```
nota. Recuerda saber en donde estas navegando en el terminal 
opcional:
- mv -> mueves archivos de un directorio a otro
- zip -r nombre.zip /directorio name -> Comprimes 
