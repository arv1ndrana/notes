# i3-wm: window manager

```shell
sudo pacman -S i3-wm i3blocks i3lock i3status
sudo pacman -S dex xss-lock
```

# ly: display manager/ login manager

```shell
sudo pacman -S ly
sudo pacman -S xorg-auth pam libx11 libxcb libxft libxinerama

sudo systemctl enable ly.service
sudo systemctl disable getty@tty2.service
sudo systemctl start ly.service
```

# yay: yet another yogurt

```shell
sudo pacman -S git base-devel --needed

git clone https://aur.archlinux.org/paru-bin.git
mv yay-bin .yay
cd .yay
makepkg -si
```
# dmenu: minimalist menu
```shell
mkdir ~/.local/src
cd ~/.local/src

git clone https://git.suckless.org/dmenu
cd dmenu
sudo make clean install
```
- **NOTE**: If dmenu is installed there is no need for [[#rofi menu]].
# touchpad
**NOTE:** This option is for **Laptop** only.

```shell
sudo pacman -S xorg-xinput

xinput list #note the name of your touchpad
xinput set-prop "name of your touchpad" "libinput Tapping Enabled" 1
```

# pipewire: audio

```shell
sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack
reboot
```

# pcmanfm: file manager

```shell
sudo pacman -S pcmanfm-gtk3 gvfs xarchiver

sudo pacman -S xdg-user-dirs
xdg-user-dirs-update
```

- Trash files are stored in ~/.local/share/Trash/files

# ufw: fire wall

```shell
sudo pacman -S ufw

sudo ufw limit 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw default deny incoming
sudo ufw default allow outgoing

sudo ufw enable
sudo ufw status
```

# udiskie: pendrive mounting

```shell
sudo pacman -S udiskie

udiskie
```

# ibus: nepali keyboard
```shell
sudo pacman -S ibus
yay -S ibus-m17n --noconfirm

ibus start
```

- Right Click on keyboard icon on the right side down.
- Click on Preferences.
- Click on Input Method.
- Click on Add.
- Click on three dot option below Spanish. Type "Nepali".
- Click on first option i.e Nepali (macrolanguage)
- Click on ne-trad(m17n) and Add.
- Now, Close the Window.

# keepassxc: passwd manager

```shell
sudo pacman -S keepassxc xclip
```

# auto-jump: cd with jumping ability

```shell
yay -S autojump
vim ~/.shellrc
```

- Add "source /etc/profile.d/autojump.sh" without quotation marks.

# papirus: icon pack

```shell
yay -S papirus-icon-theme
```

# dunst: notification daemon
```shell
yay -S dunst

mkdir ~/.config/dunst -p
cp /etc/dunst/dunstrc ~/.config/dunst
cd ~/.config/dunst

nvim dunstrc
```
- Search for "icon_theme"
- Replace 'Adwaita' to 'Papirus'
- Same as above for "icon_path"
- Search for "[urgency_low]" and "[urgency_normal]"
- Set the timeout to 3
```shell
killall dunst && dunst
```
# batify & batsignal: notify when unplugged or low battery

**NOTE:** This option is for **Laptop** only.

```shell
yay -S batify batsignal
```

**WORK IN PROGRESS**
# rofi: menu

```shell
yay -S rofi

rofi -show drun -icon-theme "Papirus" -show-icons
```
# zsh: shell

```shell
yay -S zsh
chsh -s /bin/zsh

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
# darkmode - not working

```shell
cd ~/.config/gtk-3.0/
nvim settings.ini
```

- Add the following line "gtk-application-prefer-dark-theme = true" without quotation marks.
```shell
gsettings set org.gnome.desktop.interface color-scheme prefer-dark
```
**WORK IN PROGRESS**
# lxappearance: change theme

```shell
yay -S lxappearance-gtk3
```
# wine: wine is not an emulator
```shell
su
nvim /etc/pacman.conf
```
- uncomment:
	\#multilib
	\#include = /etc/pacman.d/mirrorlist
```shell
yay -Syu
yay -S wine winetricks wine-mono wine-gecko
```
To install `Microsoft Office 2007`.
- Download:
[Microsoft Office 2007 ISO](https://drive.massgrave.dev/en_office_enterprise_2007_united_states_x86_cd_481472.iso)
```shell
mkdir -p /media/office-2007
mount -o loop <path-to-iso> /media/office-2007
```
- Go to file manager
- Click on `OFFICE 12`
- Right Click on `setup.exe`
- Click on `Wine Windows Program Loader`
- Fill `BQDQB-KRRY9-43DBR-4P9J4-DH7D8` in the Product Key Input.
- Wait!
- Done!
```shell
umount -a
```
# qemu: virtual desktop
```shell
yay -S qemu-full virtmanager dnsmasq

yay -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat --needed

sudo systemctl enable libvirtd
sudo systemctl start libvirtd

sudo virsh net-list --all
sudo virsh net-start default

sudo virsh net-autostart default

sudo virt-manager
```
# feh: wallpaper setter
```shell
sudo pacman -S feh

mkdir ~/.wallpapers
feh --bg-fill ~/.wallpapers/
```