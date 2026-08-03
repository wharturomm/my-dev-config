# Múltiples cuentas Git

> [!IMPORTANT]  
> Para la cuenta principal/personal se recomienda dejar el **Host** como **github.com**, sin embargo, se puede cambiar por el alias al que se desee.

```bash
Host github.com # Otras opciones son: cuenta-principal o personal
  HostName github.com
  User git # Para conectar a GitHub siempre se usa "git".
  IdentityFile ~/.ssh/id_ed25519_personal
  IdentitiesOnly yes

Host cuenta-trabajo.com
  HostName github.com
  User mi_otro_usuario # Para conectar a GitHub siempre se usa "git".
  IdentityFile ~/.ssh/id_ed25519_trabajo
  IdentitiesOnly yes
```
