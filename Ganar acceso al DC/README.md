# Requisitos
Para ganar acceso al `Domain Controller` debemos disponer de credenciales válidas de un `Administrador` del `dominio`.

# Realizar Autenticación
Para ello utilizaremos psexec
```
psexec.py <dominio>/<usuario>:<contraseña>@<ip_DC> cmd.exe
```
Ejemplo:
```
psexec.py wizzz.local/Administrador:Passw0rd@192.168.45.130 cmd.exe
```
