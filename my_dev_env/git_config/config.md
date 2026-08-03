# GIT BASIC CONFIG

## Configuraciones iniciales:
```cmd
# Agrega nombre de usuario.
git config --global user.name "name"

# Agrega email del usuario.
git config --global user.email email

# Abre VSCode como editor por defecto (puede ser otro editor).
git config --global core.editor "code --wait"

# Configura la rama main por default.
git config --global init.defaultBranch main

# Abre el archivo de configuración en el editor por defecto.
git config --global -e
```



## Alias:
```cmd
# Muestra de una forma más estética el git log.
git config --global alias.tree "log --graph --decorate --all --oneline"
```



## Manejo de saltos de línea:
**En Windows (CRLF), ejecuta el siguiente comando:**
```cmd
git config --global core.autocrlf true
```
\r = Carriage return.
\n = Line feed.

**En sistemas Unix (LF), ejecuta el siguiente comando:**

```cmd
git config --global core.autocrlf input
```
\n = Line feed.
