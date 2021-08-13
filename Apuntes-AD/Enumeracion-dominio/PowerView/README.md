# PowerView
PowerView es una herramienta que debemos subir a la máquina víctima para poder enumerar el dominio y nos permitirá ejecutar algunos comandos.
## Dominios
```
#Ver dominio actual
Get-Domain

#Ver otros dominios
Get-Domain -Domain <nombre>
```
## Domain Policy
```
Get-DomainPolicy
Get-DomainPolicy | Select-Object -ExpandProperty SystemAccess
Get-DomainPolicy | Select-Object -ExpandProperty KerberosPolicy
```
## Usuarios del dominio
```
#Exportar todos los usuarios a un archivo
Get-DomainUser | Out-File -FilePath .\usuarios.txt

#Devuelve propiedades de un usuario concreto
Get-DomainUser -Identity [usuario] -Properties DisplayName, MemberOf | Format-List
```
## Enumerar grupos y miembros
```
#Exportar todos los grupos a un archivo
Get-DomainGroup | Out-File -FilePath .\groups.txt

#Mostrar miembros de un grupo en específico
Get-DomainGroup -Identity '<nombre_grupo>' | Select-Object -ExpandProperty Member 
Get-DomainGroupMember -Identity '<nombre_grupo>' | Select-Object MemberDistinguishedName
```
## Enumerar grupos y miembros
```
#Exportar todos los grupos a un archivo
Get-DomainGroup | Out-File -FilePath .\groups.txt

#Mostrar miembros de un grupo en específico
Get-DomainGroup -Identity '<nombre_grupo>' | Select-Object -ExpandProperty Member 
Get-DomainGroupMember -Identity '<nombre_grupo>' | Select-Object MemberDistinguishedName
```
## Recursos compartidos
```
#Enumaración
Find-DomainShare

#Enumerate recursos del usuario actual
Find-DomainShare -CheckShareAccess

#Enumerar elementos interesantes a los que podemos acceder
Find-InterestingDomainShareFile -Include *passwords*
```
## Enumerar OUs
```
Get-DomainOU -Properties Name | Sort-Object -Property Name
```
## Enumerar ACLs
```
#Devolver ACLs de una cuenta
Get-DomaiObjectAcl -Identity <nombre_cuenta> -ResolveGUIDs
```
## Enumerar Trust del dominio
```
Get-DomainTrust
Get-DomainTrust -Domain <nombre_dominio>
```
