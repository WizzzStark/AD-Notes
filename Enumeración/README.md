# Formas de enumerar el dominio

## Enumerar los usuarios del dominio con rpcclient
Para hacer esto debemos conocer unas credenciales de usuario válidas, no hace falta que sean privilegiadas.
```
rpcclient -U "<nombre_dominio>\<usuario>%<contraseña>" <IP_DC> '<enumdomusers>'
```
[Ver ejemplo](Images/users/README.md)

## Listar información de usuarios mediante el rid.
Hay veces que enumerando los usuarios podremos encontrar información valiosa en sus descripciones
```
for rid in $(rpcclient -U "<nombre_dominio>\<usuario>%<contraseña>" <IP_DC> '<enumdomusers>' | grep -oP '\[.*?\]' | grep '0x' | tr -d '[]'); do echo -e "\n[+] Para el RID $rid:\n"; rpcclient -U "<nombre_dominio>\<usuario>%<contraseña>" <IP_DC> "queryuser $rid" | grep -E -i "user name|description";done
```
[Ver ejemplo](Images/rid/README.md)

## Usar ldapdomaindump para representar la información en HTML
Para hacer esto debemos conocer unas credenciales de usuario válidas, no hace falta que sean privilegiadas.
```
service apache2 start
```
```
python3 ldapdomaindump.py -u '<nombre_dominio>\<usuario>' -p '<contraseña>' <IP_DC>
```
[Ver ejemplo](Images/ldap/README.md)
