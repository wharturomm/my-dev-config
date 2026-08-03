# Manjaro

Atajos del teclado/Personalizar: Agregar **ctrl + alt + t** para abrir la **terminal** (Escritorio GNOME).

```bash
kgx
```



Agregar **asteriscos** en las contraseñas:

```bash
sudo nano /etc/sudoers

# Debajo de la línea: Defaults	specification, añadir:
Defaults	env_reset
Defaults	pwfeedback

# Presionar ctrl+o, después enter para guardar los cambios.
# Reiniciamos la terminal.
```



Configuración de **pacman**:

```bash
sudo nano /etc/pacman.conf

# Buscar la línea: ParallelDownloads y modificarla de 4 a 10:
ParallelDownloads = 10
```



**Mirrors** (Pueden variar según el país):

```bash
sudo nano /etc/pacman.d/mirrorlist

# Cambiar al mirrorlist más cercano:
sudo pacman-mirrors --geoip
```



Instalación de utilidades:

```bash
# Mejora la integración de máquinavirtual y SO. 
# sudo dnf install open-vm-tools-desktop

# Actualiza todo lo que esté disponible. 
sudo pamac update --force-refresh --no-confirm

# Elimina residuos.
sudo pamac clean --no-confirm

# Paquete de aplicaciones para desarrollo.
sudo pacman -Sy base-devel --no-confirm

# Neofetch/Fastfetch.
sudo pamac install neofetch fastfetch --no-confirm

# Visualizador de tareas/recursos.
sudo pamac install htop btop --no-confirm

# Complementos para que reconozca todo tipo de particiones de disco duro.
sudo pamac install ntfs-3g --no-confirm

# Editores de texto.
sudo pamac install nano vim neovim --no-confirm

# Compresores.
sudo pacman -S xz bzip2 p7zip lbzip2 lrzip arj lzop cpio unrar --no-confirm

# Codecs de audio y vídeo.
sudo pacman -S jasper lame libdca libdv gst-libav libtheora libvorbis libxv wavpack x264 xvidcore dvd+rw-tools dvdauthor dvgrab libmad libmpeg2 libdvdcss exfat-utils fuse-exfat a52dec faac faad2 flac --no-confirm

# Herramientas de comandos para transferencia de datos desde y hacia servidores.
sudo pamac install curl wget --no-confirm

# Acceso y descifrado de DVDs.
sudo pamac install libdvdread libdvdnav lsdvd --no-confirm

# Tipografías de Ubuntu.
# sudo dnf copr enable atim/ubuntu-fonts && sudo dnf install ubuntu-family-fonts -y
```



**Repositorios** (Pueden variar según la versión de Manjaro):

```bash
# Ya que Manjaro es base Arch, añadimos los repositorios de AUR mediante yay:
git clone https://aur.archlinux.org/yay.git

# Compilamos:
cd yay
makepkg -si

# Comprobamos que ya tenemos AUR:
yay -Syu
```



Instalación de Flatpak:

```bash
# Instalación de Flatpak.
sudo pacman -S flatpak

# Para que el centro de aplicaciones reconozca Flatpak.
pamac install flatpak libpamac-flatpak-plugin

# Añade repositorio de Flathub.
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```



Instalación de Snap:

```bash
# Instalación de Snap.
sudo pacman -S snapd

# Activamos el servicios de Snap.
sudo systemctl enable --now snapd.socket
sudo systemctl enable --now snapd.apparmor

# Creamos acceso directo.
sudo ln -s /var/lib/snapd/snap /snap

# Plugin para que aparezcan los Snaps en Pamac.
pamac install libpamac-snap-plugin
```

