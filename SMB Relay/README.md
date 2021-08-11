# Qué es SMB Relay?

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

```
sudo nano /usr/share/responder/Responder.conf
```
<img src="https://i.imgur.com/XypgqGB.png" />
