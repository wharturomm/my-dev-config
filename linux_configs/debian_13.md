# Debian 13 Trixie

Entra en modo **root**:

```bash
su -
```



Atajos del teclado/Personalizar: Agregar **ctrl + alt + t** para abrir la **terminal** (Escritorio GNOME).

```bash
# Hasta esta versión, aún viene por default la terminal de GNOME, pero se recomienda instalar ptyxis o warp, varía según gustos.
gnome-terminal
ptyxis
warp-terminal

# Para eliminar el mensaje de copyright en la terminal de Warp, creamos un archivo .hushlogin en la carpeta de usuario:
touch ~/.hushlogin
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



**Repositorios** (Pueden variar según la versión de Debian):

```bash
nano /etc/apt/sources.list

# En los repositorios, que por lo regular son 6. Después de la palabra 'main', vamos a escribir 'contrib non-free'en todos los repositorios.

# Aunque la mejor opción es, borrar todo el contenido del archivo, copiar y pergar los siguientes repositorios.
deb https://deb.debian.org/debian/ trixie contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ trixie contrib main non-free non-free-firmware

deb https://deb.debian.org/debian/ trixie-updates contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ trixie-updates contrib main non-free non-free-firmware

deb https://deb.debian.org/debian/ trixie-proposed-updates contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ trixie-proposed-updates contrib main non-free non-free-firmware

deb https://deb.debian.org/debian/ trixie-backports contrib main non-free non-free-firmware
# deb-src https://deb.debian.org/debian/ trixie-backports contrib main non-free non-free-firmware

deb https://security.debian.org/debian-security/ trixie-security contrib main non-free non-free-firmware
# deb-src https://security.debian.org/debian-security/ trixie-security contrib main non-free non-free-firmware
```



Instalación de utilidades:

```bash
# Actualiza todo lo que esté disponible. 
sudo apt update && sudo apt dist-upgrade -y

# Fastfetch.
sudo apt install fastfetch -y

# Visualizador de tareas/recursos.
sudo apt install htop btop -y

# Complementos para que reconozca todo tipo de particiones de disco duro.
sudo apt install exfat-fuse hfsplus ntfs-3g

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
sudo apt install fonts-freefont-ttf fonts-freefont-otf

# Tipografías de Microsoft.
sudo apt install ttf-mscorefonts-installer -y

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



Opcionales:   
Reemplazar GNOME terminal por Ptyxis.

```bash
# Para que Nautilus pueda abrir Ptyxis desde el menú contextual, es necesario instalar varios paquetes clave.
sudo apt install git make python3-nautilus gir1.2-gtk-4.0 gettext build-essential -y

# GNOME Terminal es el emulador predeterminado en Nautilus. Para cambiarlo, usaremos la extensión nautilus-open-any-terminal de Stunkymonkey, que permite seleccionar cualquier terminal compatible.
cd /tmp
git clone https://github.com/Stunkymonkey/nautilus-open-any-terminal.git
cd nautilus-open-any-terminal
make
sudo make install schema
sudo glib-compile-schemas /usr/share/glib-2.0/schemas

# Configurar Ptyxis como terminal predeterminada.
gsettings set com.github.stunkymonkey.nautilus-open-any-terminal terminal ptyxis

# Reiniciar Nautilus para aplicar los cambios.
nautilus -q

# Eliminar GNOME Terminal si ya no lo usas.
sudo apt remove --purge gnome-terminal -y
sudo apt autoremove -y
```



Reemplazar el kernel actual por el de liquorix:
```bash
# Instalación de kernel liquorix.
curl -s 'https://liquorix.net/install-liquorix.sh' | sudo bash
```
