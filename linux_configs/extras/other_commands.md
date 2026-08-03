# Otros comandos

```bash
# Muestra el nombre de la distribución GNU/Linux, número de versión y descripción detallada:
cat nano /etc/os-release

# Cambiar el nombre del hostname (cerrar sesión o reiniciar equipo para ver los cambios):
sudo hostnamectl set-hostname new-hostname

# Remover LibreOffice base Debian:
sudo apt purge "libreoffice*"
sudo apt autoremove --purge
```



## Configuración de terminal
```bash
# Ghostty
# Abrimos el archivo de configuración y añadimos las siguientes líneas.
theme = Catppuccin Mocha # Tema para la terminal.
command = /bin/zsh -l -i # Establece ZSH por defecto, solo para esta terminal.
background-opacity = 0.85 # Transparencia de la terminal.
```



## Configuración de Zed editor en VM
```bash
# Bash
echo 'export ZED_ALLOW_EMULATED_GPU=1' >> ~/.bashrc
source ~/.bashrc

# Zsh
echo 'export ZED_ALLOW_EMULATED_GPU=1' >> ~/.zshrc
source ~/.zshrc
```
