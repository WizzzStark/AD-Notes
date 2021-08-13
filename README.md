# Técnicas de explotación de AD
Recopilación de técnicas de explotación de AD

## Información
- Servicio creado por `Microsoft` para gestionar en Windows `redes de dominio`.
- Se almacena información relacionada con objetos como ordenadores, usuarios, etc..
- `Autentificación` mediante tickets de `Kerberos`. 
- Otros dispositivos que no son Windows también se pueden autenticar al AD con `RADIUS` o `LDAP`.

- [Técnicas de explotación de AD](#Técnicas-de-Explotación-de-AD)
  - [Información](#Información)
  - [Herramientas](#Herramientas)
  - [Enumración del dominio](#Enumeración-del-dominio)
    - [Usando PowerView](#Usando-PowerView)
    - [Usando BloodHound](#Usando-BloodHound)
  - [Escalada de Privilegios Local](#Escalada-de-Privilegios-Local)
  - [Escalada de Privilegios del dominio](/Apuntes-AD/Domain-privesc/#Escalada-de-Privilegios-del-dominio)
    - [AS-REP Roasting](/Apuntes-AD/Domain-privesc/AS-REP-Roasting)
