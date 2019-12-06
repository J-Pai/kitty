# Kitty Configuration
Goes into ~/.config

# Setting Up as Default Terminal
```
sudo ln -s ~/.local/kitty.app/bin/kitty /usr/local/bin/
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/local/bin/kitty 50
sudo update-alternatives --config x-terminal-emulator
```
