# Debian 12 Bookworm

Entra en modo **root**:

```bash
su -
```



Atajos del teclado/Personalizar: Agregar **ctrl + alt + t** para abrir la **terminal** (Escritorio GNOME).

```bash
gnome-terminal
```



Agregar **asteriscos** en las contraseñas:

```bash
nano /etc/sudoers

# Debajo de la línea: Defaults	env_reset, añadir:
Defaults	pwfeedback

# Presionar ctrl+o, después enter para guardar los cambios.
# Reiniciamos la terminal.
```



Añadir **permisos root** un usuario determinado:

```bash
nano /etc/sudoers.d/user_name

# Para poder invocar sudo con nuestro usuario, agregamos la siguiente línea:
user_name	ALL=(ALL:ALL) ALL

# Presionar ctrl+o, después enter para guardar los cambios.
# Reiniciamos la terminal.

# Otra opción más moderna es agregar los permisos root por medio de la terminal con el siguiente comando:
sudo usermod -aG sudo username

# Verificamos que se haya añadido al grupo sudo:
groups username
```



Modificar inicio de **GRUB**:

```bash
nano /etc/default/grub

# Para que no aparezca el GRUB. Es innecesario si solo se tiene un SO de linux.
GRUB_TIMEOUT=5 # Igualarlo a 0.
GRUB_CMDLINE_LINUX_DEFAULT="quiet" # Después de quiet, colocar un espacio y escribir la palabra splash: "quiet splash". Esto para añadir el playmod.
GRUB_GFXMODE=640X480 # Quitar comentario y añadir la resolución personalizada. Comúnmente solo afecta en máquinas virtuales.
GRUB_BACKGROUND="" # Quita la pantalla del GRUB.

# Precionar ctrl+o, después enter para guardar los cambios.

# Ejecutamos los siguientes comandos para actualizar los cambios realizados en el GRUB:
sudo update-grub # También puede ser: sudo update-grub2.

# Reiniciar SO.
```



Para **desinstalar** aplicaciones predeterminadas innecesarias en GNOME; abrimos el **Gestor de paquetes Synaptic**, escribimos gnome-games y eliminamos.



Instalar la aplicación **Software & Updates** desde Discover y abrir la aplicación.



**Repositorios** (Pueden variar según la versión de Debian):

Marcar las casillas:

- Software compatible con las "DFSG" con dependencias no libres (contrib).
- Software no compatible con las "DFSG" (non-free).

En la pestaña **Other Software** agregar el siguiente repositorio:

```bash
deb http://deb.debian.org/debian bookworm-backports main
```

Le damos en añadir origen sin marcar la casilla y recargamos los repositorios.

```bash
# Aunque la mejor opción es, borrar todo el contenido del archivo, copiar y pergar los siguientes repositorios.
deb https://ftp.debian.org/debian/ bookworm contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ bookworm contrib main non-free non-free-firmware

deb https://ftp.debian.org/debian/ bookworm-updates contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ bookworm-updates contrib main non-free non-free-firmware

deb https://ftp.debian.org/debian/ bookworm-proposed-updates contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ bookworm-proposed-updates contrib main non-free non-free-firmware

deb https://ftp.debian.org/debian/ bookworm-backports contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ bookworm-backports contrib main non-free non-free-firmware

deb https://security.debian.org/debian-security/ bookworm-security contrib main non-free non-free-firmware
# deb-src https://security.debian.org/debian-security/ bookworm-security contrib main non-free non-free-firmware
```



Instalación de utilidades:

```bash
# Actualiza todo lo que esté disponible. 
sudo apt update && sudo apt dist-upgrade -y

# Neofetch/Fastfetch.
sudo apt install neofetch fastfetch -y

# Visualizador de tareas/recursos.
sudo apt install htop btop -y

# Complementos para que reconozca todo tipo de particiones de disco duro.
sudo apt install exfat-fuse hfsplus hfsutils ntfs-3g

# Gestores de paquetes.
sudo apt install gdebi gdebi-core synaptic -y

# Editores de texto.
sudo apt install nano vim neovim -y

# Compresores.
sudo apt install p7zip-full p7zip-rar rar unrar -y

# Herramientas de comandos para transferencia de datos desde y hacia servidores.
sudo apt install curl wget -y

# Git
sudo apt install git -y

# Codecs de audio y vídeo.
sudo apt install ffmpeg libavcodec-extra gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad gstreamer1.0-pulseaudio vorbis-tools -y

# Tipografías.
sudo apt-get install fonts-freefont-ttf fonts-freefont-otf

# Tipografías de Microsoft.
sudo apt-get install ttf-mscorefonts-installer -y

# Tipografías de Ubuntu.
sudo apt install fonts-ubuntu
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



Instalación de kernel actualizado por Backports:

```bash
sudo apt install -t bookworm-backports linux-image-amd64
```
