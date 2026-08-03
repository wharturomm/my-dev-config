# Instalación de Fish (SHELL)

```bash
# Actualizar repositorios:
sudo apt update -y

# Instalar curl y fish:
sudo apt install curl fish -y

# Establecer fish por defecto:
# which fish -> Muestra la ruta de fish.
chsh -s $(which fish)
chsh -s /usr/bin/fish

# Instalar fisher (instalador de complementos de fish):
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher

# Instalar tide (framework de fish):
fisher install IlanCosman/tide@v6
# tide configure

# Eliminar mensaje de bienvenida:
set -U fish_greeting ""
```
