# Generar SSH key en Windows

**Verificar llaves existentes:**

```bash
# Enlista los archivos en la carpeta .ssh.
cd ~/.ssh && ls

# Si no existe la carpeta, debemos crearla con el siguiente comando.
mkdir ~/.ssh
# Después volvemos a ejecutar el primer comando.
```



**Generar una nueva llave:**

```shell
# Si no queremos cambiar el nombre del archivo default ni la passphrase, presionamos enter 3 veces.
ssh-keygen -t ed25519 -C "your_email@example.com"
```



> [!IMPORTANT]  
> A partir de este momento, sustituye los siguientes valores:
> 
> **YOU**: Por tu nombre de **usuario** de Windows.   
> **id_ed25519**: Por el nombre de tu archivo en caso de haberlo cambiado.



**Añadir la llave al ssh-agent:**

```bash
# Inicia el ssh-agent en 2do plano.
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent

# Añade la llave al ssh-agent.
ssh-add C:/Users/YOU/.ssh/id_ed25519
```



**Copia el contenido de la llave para añadirla a una cuenta GitHub:**

```bash
# Copia el contenido del archivo id_ed25519.pub a su portapapeles.
cat ~/.ssh/id_ed25519.pub | clip

# En caso de que no funcione porque el sistema es más antiguo.
clip < ~/.ssh/id_ed25519.pub
```



**Verifica el correcto funcionamiento:**

```bash
# Para verificar que la llave funciona correctamente, ejecutamos el siguiente comando.
ssh -T git@github.com
```
