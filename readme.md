1. Paso
Escanear redes con comodines, asterisco 
nmap -sn 10.0.5.10-30 192.168.12.100-200 10.5.0.5 192.168.*.1-255
* = escanea todos los valores
-sn = solo es para scaneo de redes
2. Paso
- 65535 numero de todos los puertos
nmap -p1-65535 10.0.5.128
nmap -p- 10.0.5.128 -> scaneo total, es basico y es lo principal. 
Si no se colocan los puertos, automaticamente scanea los 1000 puertos
nmap -P0 -p- 10.0.5.128 -> No scanea host, solo scaneo de todos los puertos Puertos. 
Siguiente paso.
3. Paso escaneo de Versiones 
nmap -P0 -p- -sV 10.0.5.128 ->
-sV = scaneo de versiones
nmap -P0 -p- -sV -O 10.0.5.128 ->
-O = Sistema Operativo 
nmap -P0 -p- -sV -O -sC 10.0.5.128
nmap -P0 -p- -A 10.0.5.128 ->
-A = scaneo todas las 3 alternativas que hemos realizado en el paso 3
nmap -P0  -sS -p- -A 10.0.5.128 -> Comando base para scanear tus objetivos 
-sS -> Utilizas el comando con altos previlegios.
