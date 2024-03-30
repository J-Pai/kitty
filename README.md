# Kitty Configuration
Goes into ~/.config

## Setup Fonts

```
mkdir -p ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/JetBrainsMono.zip
unzip JetBrainsMono.zip
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/Noto.zip
unzip Noto.zip
mkdir -p ~/.config/fontconfig
cd ~/.config/fontconfig && vim fonts.conf

# Then run fc-cache to update the font cache
fc-cache -f -v

# Kitty should have JetBrainsMono
kitty list-fonts
```

## Setting Up as Default Terminal
```
sudo ln -s ~/.local/kitty.app/bin/kitty /usr/local/bin/
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/local/bin/kitty 50
sudo update-alternatives --config x-terminal-emulator
```

## Fixing SSH TERM Issues
Add the following alias:
```
alias ssh='TERM=xterm ssh'
```
