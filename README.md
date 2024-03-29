# Kitty Configuration
Goes into ~/.config

## Setup Fonts

```
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts && curl -fLo "JetBrains Mono Regular Nerd Font Complete Mono Windows Compatible.ttf" \
    https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/JetBrainsMono/Ligatures/Regular/JetBrainsMonoNerdFontMono-Regular.ttf
cd ~/.local/share/fonts && curl -fLo "JetBrains Mono Bold Nerd Font Complete Mono Windows Compatible.ttf" \
    https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/JetBrainsMono/Ligatures/Bold/JetBrainsMonoNerdFontMono-Bold.ttf
cd ~/.local/share/fonts && curl -fLo "JetBrains Mono Italic Nerd Font Complete Mono Windows Compatible.ttf" \
    https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/JetBrainsMono/Ligatures/Italic/JetBrainsMonoNerdFontMono-Italic.ttf
cd ~/.local/share/fonts && curl -fLo "JetBrains Mono Bold Italic Nerd Font Complete Mono Windows Compatible.ttf" \
    https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/JetBrainsMono/Ligatures/BoldItalic/JetBrainsMonoNerdFontMono-BoldItalic.ttf

mkdir -p ~/.config/fontconfig
cd ~/.config/fontconfig && vim fonts.conf

# Copy the text below
<!-- Override monospace detection for custom fonts -->
<match target="scan">
    <test name="family">
        <string>JetBrainsMono NFM</string>
    </test>
    <edit name="spacing">
        <int>100</int>
    </edit>
</match>

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
