# Password Spraying 
Este es un ataque que podemos realizar después de compremeter un equipo, en él trataremos de reutilizar las credenciales que tenemos para ver si son privilegiadas sobre otros equipos del dominio para conectarnos a ellos o simplemente validar si son credenciales válidas aunque no tengamos permiso para conectarnos.

# Efectuar ataque
Para relizar este ataque recomiendo la herramienta `crackmapexec`, podemos saber si podemos autenticarnos si el crackmapexec nos da un `Pwn3d!` para ese equipo.
```
crackmapexec smb <target> -u 'USUARIO' -p 'CONTRASEÑA'
```
[Ver Ejemplo](/Apuntes-AD/Images/9.md)

# Otras herramientas
[Domain Password Spray](https://github.com/dafthack/DomainPasswordSpray)
[Invoke-CleverSpray](https://github.com/wavestone-cdt/Invoke-CleverSpray)
