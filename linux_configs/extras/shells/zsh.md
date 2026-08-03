# Instalación de ZSH (SHELL)

```bash
# Actualizar repositorios:
sudo apt update -y

# Instalar curl y zsh:
sudo apt install curl zsh -y

Establecer zsh por defecto:
# which zsh -> Muestra la ruta de zsh.
chsh -s $(which zsh)
chsh -s /usr/bin/zsh

# Instalar oh-my-zsh (instalador de complementos de zsh):
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Instalación del tema Powerlevel10k:
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"

# Abrimos la configuración de ZSH:
nano .zshrc

# En la línea 'ZSH_THEME=' añadimos el tema:
ZSH_THEME='powerlevel10k/powerlevel10k'

# Instalación de plugins:
- zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

- zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

- fast-syntax-highlighting
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git \
${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting\

- zsh-autocomplete
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete

# Nuevamente abrimos la configuración de ZSH y nn la línea 'plugins=' añadimos lo siguiente:
plugins=(git zsh-autosuggestions zsh-syntax-highlighting fast-syntax-highlighting zsh-autocomplete)

# Comando para abrir la configuración de Powerlevel10k:
p10k configure
```
