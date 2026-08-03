# Ubuntu 26.04 Resolute Raccon

Atajos del teclado/Personalizar: Agregar **ctrl + alt + t** para abrir la **terminal** (Escritorio GNOME).

```bash
ptyxis
```



Instalación de utilidades:

```bash
# Mejora la integración de máquinavirtual y SO. 
sudo apt install open-vm-tools-desktop

# Actualiza todo lo que esté disponible. 
sudo apt update && sudo apt full-upgrade -y

# Fastfetch.
sudo apt install fastfetch -y

# Visualizador de tareas/recursos.
sudo apt install htop btop -y

# Complementos para que reconozca todo tipo de particiones de disco duro.
sudo apt install exfat-fuse hfsplus hfsutils ntfs-3g

# Gestores de paquetes.
sudo apt install gdebi gdebi-core synaptic -y

# Editores de texto.
sudo apt install nano vim neovim -y

# Compresores.
sudo apt install p7zip-full rar unrar -y

# Restricted extras.
sudo apt install ubuntu-restricted-extras -y

# Herramientas de comandos para transferencia de datos desde y hacia servidores.
sudo apt install curl wget -y

# Git
sudo apt install git -y
```



Opcionales:

```bash
# Acceso y descifrado de DVDs.
sudo apt install libdvdcss2

# Reconfigura paquetes ya instalados y lo hace con libdvd-pkg.
sudo dpkg-reconfigure libdvd-pkg
```



Instalación de Flatpak:

```bash
# Instalación de Flatpak.
sudo apt install flatpak -y

# Instalaciones extras para GNOME y su plugin de Flatpak (Sólo GNOME).
sudo apt install gnome-software gnome-software-plugin-flatpak -y

# Añade repositorio de Flathub.
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```



Eliminar residuos:

```bash
# Limpieza de residuos.
sudo apt clean && sudo apt autoclean && sudo apt autoremove -y
```



Eliminar mensajes de Ubuntu Pro en terminal:

```bash
# Deshabilita el ESM Hook.
sudo dpkg-divert --rename --divert /etc/apt/apt.conf.d/20apt-esm-hook.conf.disabled --add /etc/apt/apt.conf.d/20apt-esm-hook.conf

# Restaura el ESM Hook.
sudo dpkg-divert --rename --remove /etc/apt/apt.conf.d/20apt-esm-hook.conf
```
