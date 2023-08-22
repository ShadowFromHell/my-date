## Галерея
<img src="https://notabug.org/owl410/owl_dotfiles/raw/master/dotfiles/hyprland/hypr_arch/.img/photo_2023-08-17_20-55-56.jpg" width="350" align="center">
<img src="https://notabug.org/owl410/owl_dotfiles/raw/master/dotfiles/hyprland/hypr_arch/.img/photo_2023-08-17_20-55-59.jpg" width="350" align="center">
<img src="https://notabug.org/owl410/owl_dotfiles/raw/master/dotfiles/hyprland/hypr_arch/.img/photo_2023-08-17_20-56-01.jpg" width="350" align="center">
<img src="https://notabug.org/owl410/owl_dotfiles/raw/master/dotfiles/hyprland/hypr_arch/.img/photo_2023-08-17_20-56-03.jpg" width="350" align="center">
<img src="https://notabug.org/owl410/owl_dotfiles/raw/master/dotfiles/hyprland/hypr_arch/.img/photo_2023-08-17_20-56-04.jpg" width="350" align="center">
<img src="https://notabug.org/owl410/owl_dotfiles/raw/master/dotfiles/hyprland/hypr_arch/.img/photo_2023-08-17_20-58-04.jpg" width="350" align="center">

## Информация
|DIstro|[ARCH](https://archlinux.org/)|
|:---:|:---:|
|WM|[Hyprland](https://hyprland.org/)|
|Bar|[Waybar](https://github.com/Alexays/Waybar)|
|Terminal|[Alacritty](https://github.com/alacritty/alacritty)|
|Shell|[Fish](https://fishshell.com/)|
|Icon|[breeze-icons-dark](--)|
|GTK3|[Fantome](--)|
|Cursors|[Capitaine cursors](https://github.com/keeferrourke/capitaine-cursors)|
|Fonts|[JetBrainsMono](https://www.jetbrains.com/lp/mono/)|
|Launcher|[wofi](https://sr.ht/~scoopta/wofi/)|

  
## ВАЖНО!!!
Я делал данный райс на ArchLinux, все настройки идут от `~/.config/hypr/themes/hypr_arch/hypr/config` В первую очередь необходимо открыть этот файл и закоментировать/раскоментировать то что тебе нужно.
  
Конфиги и обои берутся из `~/.config/hypr/themes/hypr_arch` 
## Настройка системы

[```Установка ArchLinux```](https://notabug.org/owl410/owl_dotfiles/src/master/guid/ArchLinux%20uefi%20install.md)  
[```Установка Apparmor```](https://notabug.org/owl410/owl_dotfiles/src/master/guid/Apparmor.md)  
[```Установка Lutris```](https://notabug.org/owl410/owl_dotfiles/src/master/guid/Lutris.md)  
[```Автостарт и Автологин```](https://notabug.org/owl410/owl_dotfiles/src/master/guid/Autostart_wm.md)  
  
  
## Установка Hyprland
```
sudo pacman -S base-devel gdb ninja gcc cmake libxcb xcb-proto xcb-util  
xcb-util-keysyms libxfixes libx11 libxcomposite xorg-xinput libxrender  
pixman wayland-protocols cairo pango seatd libxkbcommon xcb-util-wm  
xorg-xwayland cmake wlroots mesa git meson polkit 
  
git clone --recursive https://github.com/hyprwm/Hyprland  
cd Hyprland  
git submodule init  
git submodule update  
sudo make install  
  
cp Hyprland/example/hyprland.conf ~/.config/hypr/
  
Hyprland - для того что бы запустить

Так же можно из реп поставить sudo pacman -S hyprland или из аура
```
  
## Установка Hyprpaper
```
git clone https://github.com/hyprwm/hyprpaper  
cd hyprpaper  
make all  
  
sudo cp ~/hyprpaper/build/hyprpaper /usr/bin 

Ну или из реп поставить sudo pacman -S hyprpaper или из аура
```
  
## Установка Waybar
```
git clone https://github.com/Alexays/Waybar/  
cd Waybar  
sudo pacman -S fmt spdlog gtkmm3 libdbusmenu-gtk3 upower libmpdclient sndio gtk-layer-shell scdoc  
clang awesome-terminal-fonts jq  

yay catch2-git

sed -i 's/zext_workspace_handle_v1_activate(workspace_handle_);/const std::string command = "hyprctl dispatch   workspace " + name_;\n\tsystem(command.c_str());/g' src/modules/wlr/workspace_manager.cpp  

meson --prefix=/usr --buildtype=plain --auto-features=enabled --wrap-mode=nodownload build  
meson configure -Dexperimental=true build  
sudo ninja -C build install  

Можно так же из реп поставить или из аура. Я ставил из реп, вроде все пофиксили и все норм.
```
  
## Установка софта
```
sudo pacman -S pulseaudio pavucontrol firefox telegram-desktop mousepad gimp inkscape  
blender ghostscript obs-studio xdg-desktop-portal-wlr transmission-gtk python  
imv mpv nemo waybar grim slurp swaybg swaylock mako jq wofi htop cmus neofetch ranger unzip
ttf-nerd-fonts-symbols

yay cava
``` 
  
## Установка темы hypr_arch
```
Склонировать репозиторий командой(предварительно нужно поставить пакет git): 

git clone https://notabug.org/owl410/owl_dotfiles
```  
  
```
Из ~/owl_dotfiles/dotfiles/hyprland/hypr_arch/.config скопировать все в ~/.config
можно мышкой в файловом менеджере.
 
cp -r ~/owl_dotfiles/dotfiles/hyprland/hypr_arch/.config/ ~/.config
```  
  
```
Сделать исполняемыми все скрипты в ~/.config/hypr/themes/hypr_arch/scripts
sudo chmod -R u+x ~/.config/hypr/themes/hypr_arch/scripts
```  
  
```
Установка тем, иконок и курсоров:
gsettings set org.gnome.desktop.interface icon-theme breeze-icons-dark  
gsettings set org.gnome.desktop.interface gtk-theme Fantome
gsettings set org.gnome.desktop.interface cursor-theme capitaine-cursors
```  
  
```
В ~/.config/hypr/hyprland.conf заинклюженна ссылка на конфиг,
потому что я не знаю как сделать по другому) Точнее знаю но мне проверять лень)
```