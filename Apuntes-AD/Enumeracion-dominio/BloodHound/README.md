# Que es Bloodhound?
Es una herramienta que nos moestrará toda la información del dominio y vías potenciales para convertirnos en administrador del mismo de la forma mas corta posible mediante un sistema de nodos.

# Iniciar Bloodhound
```
#Iniciar consola de neo4j
neo4j console

#Iniciar Bloodhound y iniciar sesión
bloodhound &>/dev/null &
```
Ahora debemos generar un .zip con toda la información necesaria, para ello usaremos [SharpHound.ps1](https://github.com/BloodHoundAD/BloodHound/blob/master/Collectors/SharpHound.ps1), deberemos subir el recurso a la máquina víctima y ejecutar el siguiente comando
```
Invoke-BloodHound.ps1 -CollectionMethod All
```
Posteriormente nos descargamos el .zip que nos genera y lo a BloodHound para ver toda la información de forma interactiva.
