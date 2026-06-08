# Dotfiles-install-guide

## Install via archinstall



 
## After install
# check if nvidia is working correctly
- lsmod | grep nvidia - should return smth
- nvidia-smi should return info about gpu and driver
- echo $XDG_SESSION_TYPE should return wayland
- cat /sys/module/nvidia_drm/parameters/modeset should return Y
- hyprctl systeminfo should return some nvidia gpu info

# install git 
sudo pacman -S git 

# install yay
git clone https://aur.archlinux.org/yay.git ~
cd yay
makepkg -si

# install browser (brave)
yay brave-bin

# configure basic hyprland settins

nano ~/.config/hypr/hyprland.conf
monitor=DP-1,2560x1440@240,0x0,1

input{
kb_layout=hr

}

$mainMod = SUPER
$terminal = kitty
$fileManager = dolphin
$menu = wofi --show drun

bind = $mainMod, Q, exec, $terminal
bind = $mainMod, C, killactive,
bind = $mainMod, M, exec, command -v hyprshutdown >/dev/null 2>&1 && hyprshutdown || hyprctl dispatch exit
bind = $mainMod, E, exec, $fileManager
bind = $mainMod, V, togglefloating,
bind = $mainMod, R, exec, $menu

# install nevim/lazyvim text editor
install neovim/lazyvim (texteditor)
https://github.com/lazyvim/lazyvim
git clone https://github.com/LazyVim/starter ~/.config/nvim
rm -rf ~/.config/nvim/.git
nvim
# configure kitty and install zsh/oh my zsh/powerlevel10k
-copy the conf files kitty uses jetbrains mono
# install fonts and nwg-look
- sudo pacman -S nwg-look
- sudo pacman -S ttf-jetbrains-mono-nerd
- sudo pacman -S ttf-cascadia-code-nerd
- sudo pacman -S noto-fonts noto-fonts-cjk noto-fonts-emoji
-in nwg-look set dark theme and NotoSans mono medium font size 13
# font rendering
- nvim ~/.config/fontconfig/fonts.conf
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <alias>
    <family>monospace</family>
    <prefer>
      <family>JetBrains Mono Nerd Font Mono</family>
    </prefer>
  </alias>

<match target="font">
    <edit name="antialias" mode="assign">
      <bool>true</bool>
    </edit>

    <edit name="hinting" mode="assign">
      <bool>true</bool>
    </edit>

    <edit name="hintstyle" mode="assign">
      <const>hintslight</const>
    </edit>

    <edit name="rgba" mode="assign">
      <const>rgb</const>
    </edit>

    <edit name="lcdfilter" mode="assign">
      <const>lcddefault</const>
    </edit>
  </match>


</fontconfig>
```
- then  fc-cache -fv
# install nautilis
- edit hyprland cont and set it as default
# install rofi
- sudo pacman -S rofi
- git clone https://github.com/adi1090x/rofi.git --depth=1
- sudo pacman -S xdg-user-dirs
- xdg-user-dirs-update
- cd rodi
- cp -r colorss config.rasi launchers ~/.config/rofi (make the folder if it doesnt exist)
- sudo pacman -S exa
- nvim .zshrc
- add alias ls="exa -l"
