# Que es AS-REP Roasting?
AS-REP Roasting es un ataque contra `Kerberos` para cuentas de usuario que no requieran `preautentificación`, esto es el primer paso en una autentificación por Kerberos y está pensado para evitar que se aplique `fuerza bruta` con contraseñas. Durante esta fase, un usuario introduce su contraseña para encriptar un "tiket" que posteriormente el DC intentará desencriptar para validar que la contraseña es correcta. Si esta opción está desabilitada para algún usuario, un atacante podría solicitar información para autenticarse para cualquier usuario y el DC devolverá un `TGT encritado` que se puede `crackear` de forma offline.

[Ver la opción que hace a un usuario vulnerable](/Apuntes-AD/Images/2.md)

# Requisitos
Para evitar problemas debemos añadir al `/etc/hosts` lo siguiente, en el caso de este ataque con poner solo la ip y el nombre de dominio es suficiente.
```
<ip_DC> <nombre_dominio> <dominio> <nombre-DC>
```
Ejemplo:
```
192.168.214.149 wizcorp.local wizcorp DC-Company
```

# Efectuar ataque con GetNPUsers
Este ataque no suele resultar efectivo ya que en el AD el preauth viene activado de forma automática, pero si por algún casual alguna empresa tiene mal configurado su entorno pues chinpum y pa dentro con la misma.
```
GetNPUsers.py <dominio>/ -no-pass -usersfile <lista_usuarios>
```
[Ver ejemplo](/Apuntes-AD/Images/1.md)
