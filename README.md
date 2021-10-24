# Técnicas de explotación de AD
Recopilación de técnicas de explotación de AD

## Información
- Servicio creado por `Microsoft` para gestionar en Windows `redes de dominio`.
- Se almacena información relacionada con objetos como ordenadores, usuarios, etc..
- `Autenticación` mediante tickets de `Kerberos`. 
- Otros dispositivos que no son Windows también se pueden autenticar al AD con `RADIUS` o `LDAP`.

![JustWalking](https://github.com/WizzzStark/AD-Notes/blob/main/JustWalking.jpg)

- [Técnicas de explotación de AD](#Técnicas-de-Explotación-de-AD)
  - [Información](#Información)
  - [Herramientas](/Apuntes-AD/Herramientas)
  - [Enumeración del dominio](/Apuntes-AD/Enumeracion-dominio)
    - [Usando BloodHound](/Apuntes-AD/Enumeracion-dominio/BloodHound)
    - [Usando PowerView](/Apuntes-AD/Enumeracion-dominio/PowerView)
    - [Formas útiles de enumeración](/Apuntes-AD/Enumeración)
  - [Escalada de Privilegios Local](/Apuntes-AD/Local-privesc)
  - [Escalada de Privilegios del dominio](/Apuntes-AD/Domain-privesc/#Escalada-de-Privilegios-del-dominio)
    - [AS-REP Roasting](/Apuntes-AD/Domain-privesc/AS-REP-Roasting)
    - [Kerberoasting](/Apuntes-AD/Domain-privesc/Kerberoasting)
    - [LLMNR-Poisoning](/Apuntes-AD/Domain-privesc/LLMNR-Poisoning)
    - [SMB Relay](/Apuntes-AD/Domain-privesc/SMB-Relay)
       - [SMB Relay por IPv4](/Apuntes-AD/Domain-privesc/SMB-Relay/#Efectuar-un-SMB-Relay-por-IPv4)
       - [SMB Relay por IPv6 (mitm6)](/Apuntes-AD/Domain-privesc/SMB-Relay/#Ejecutar-comandos-mediante-un-SMB-Relay-por-IPv6)
    - [.scf malicioso](/Apuntes-AD/Domain-privesc/scf-malicioso)
    - [Password Spraying](/Apuntes-AD/Domain-privesc/Password-spraying)
    - [Formas de autenticarse](/Apuntes-AD/Autenticaciones)
  - [Peresistencia en el dominio](/Apuntes-AD/Domain-persistence)
    - [Golden Ticket Atack](/Apuntes-AD/Domain-persistence/Golden-ticket-atack)
    - [Dumpear Credenciales con mimikatz](/Apuntes-AD/Domain-persistence/Dumpear-mimikatz)
  - [Recomendaciones Post Exploitation](/Apuntes-AD/Domain-persistence/Post-Exploitation)
