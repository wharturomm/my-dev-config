# Fedora 42

Atajos del teclado/Personalizar: Agregar **ctrl + alt + t** para abrir la **terminal**.

```bash
ptyxis

# Si lo desea, también se sugiere instalar una terminal al gusto, en cuestiones de gusto personal, acostumbro a instalar la terminal de GNOME o Tilix.

sudo dnf install gnome-terminal -y
sudo dnf install tilix -y
```



Agregar **asteriscos** en las contraseñas:

```bash
sudo nano /etc/sudoers

# Debajo de la línea: Defaults	env_reset, añadir:
Defaults	pwfeedback

# Presionar ctrl+o, después enter para guardar los cambios.
# Reiniciamos la terminal.
```



Configuración de **dnf**:

```bash
sudo nano /etc/dnf/dnf.conf

# Debajo de la línea: [main], añadir:
max_parallel_downloads=10
fastestmirror=1
deltarpm=true
```



**Repositorios** (Pueden variar según la versión de Fedora):

```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```



Instalación de utilidades:

```bash
# Mejora la integración de máquinavirtual y SO. 
sudo dnf install open-vm-tools-desktop

# Actualiza todo lo que esté disponible. 
sudo dnf update -y
sudo dnf --nogpgcheck --best --allowerasing update -y

# Elimina residuos.
sudo dnf autoremove -y && sudo dnf clean all && sudo journalctl --vacuum-size=100M

# Neofetch/Fastfetch.
sudo dnf install neofetch fastfetch -y

# Visualizador de tareas/recursos.
sudo dnf install htop btop -y

# Complementos para que reconozca todo tipo de particiones de disco duro.
sudo dnf install hfsutils ntfs-3g -y

# Editores de texto.
sudo dnf install nano vim neovim -y

# Compresores.
sudo dnf install p7zip p7zip-plugins unrar -y

# Plugins Core
sudo dnf install dnf-plugins-core -y

# Procesamiento de sonido, vídeo y otros medios.
sudo dnf install gstreamer1-{libav,plugins-{good,ugly,bad{-free,-nonfree}}} --setopt=strict=0 -y

sudo dnf install gstreamer1-devel gstreamer1-plugins-base-tools gstreamer1-doc gstreamer1-plugins-base-devel gstreamer1-plugins-good gstreamer1-plugins-good-extras gstreamer1-plugins-ugly gstreamer1-plugins-bad-free gstreamer1-plugins-bad-free-devel gstreamer1-plugins-bad-free-extra -y

# Herramientas de comandos para transferencia de datos desde y hacia servidores.
sudo dnf install curl wget

# Acceso y descifrado de DVDs.
sudo dnf install libdvdread libdvdnav lsdvd -y

# Tipografías de Microsoft.
sudo dnf install mscore-fonts-all -y

# Tipografías de Ubuntu.
sudo dnf copr enable atim/ubuntu-fonts && sudo dnf install ubuntu-family-fonts -y
```



Instalación de Flatpak:

```bash
# Instalación de Flatpak.
sudo dnf install flatpak -y

# Instalaciones extras para GNOME y su plugin de Flatpak (Sólo GNOME).
sudo dnf install gnome-software

# Añade repositorio de Flathub.
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```



Instalación de Snap:

```bash
# Instalación de Snap.
sudo dnf install snapd -y

sudo ln -s /var/lib/snapd/snap /snap
```



Instalación de kernel Vanilla:

```bash
sudo dnf copr enable @kernel-vanilla/stable -y
sudo dnf upgrade 'kernel*'
mokutil --sb-state
```
