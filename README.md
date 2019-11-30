# Manjaro-Xfce4-Dell-7559
You can download it [here](https://manjaro.org/download/official/xfce/) and prepare bootable disk with [rufus](https://rufus.akeo.ie/) (with DD mode) or if you are on linux, you can use etcher, DD, imagewriter etc..

After that, reboot your computer and when you see the dell logo, you should press F2 and disable boot secure in boot section, then close the bios with F10(Yes). Again at the dell logo, you should press F12 and select your bootable disk. Then you see that Manjaro boot menu, select Boot:Manjaro Linux. 

Now, you can start the installiation. Follow the steps in the Manjaro User Guide. You can download [Manjaro User Guide](https://manjaro.org/support/userguide/) or find your on live manjaro system.
**After the installation, reboot your system. Press e when you see Manjaro Grub Screen(It appears if your system is dual-boot otherwise you should keep pressing shift button to show grub screen)**
then add the line after `quiet` word.
```acpi_osi=! acpi_osi="Windows 2009" ``` 

```
sudo nano /etc/default/grub 
```
> GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=! acpi_osi=\"Windows 2009\"

```
sudo update-grub
```

### Fastest pacman
```
sudo pacman-mirrors --fasttrack 5
```
### Update Your System
```
sudo pacman -Syu
```



### Packages I use
```
sudo pacman -S yay aria2 speedtest-cli telegram-desktop kdenlive inkscape create_ap virtualbox fish flameshot deepin-terminal neofetch gtop kolourpaint gedit
```
### Change the bash shell to fish
```
chsh -s /usr/bin/fish
curl -L https://get.oh-my.fish | fish
omf install bobthefish
```
## Customize shell and terminal
Change `.config/fish/conf.d/omf.fish` with [this](https://github.com/oguzkaganeren/manjaro-cinnamon-dell-7559/blob/master/.config/fish/omf.fish)
Set default deepin terminal then open it. Right click on the terminal and switch theme `argonaut`.
### Aur Packages I use
```
yay -S materia-theme opera chromium ttf-font-awesome ttf-font-awesome-4 ttf-roboto android-studio woeusb-git jdownloader2 ttf-ms-fonts vscodium-bin breeze-blurred-git otf-san-francisco xdman gwe svr zettlr-bin fslint waterfox-bin odio-appimage skypeforlinux-stable-bin posy-cursors all-repository-fonts ttf-wps-fonts
```
### Change light-locker with betterlockscreen(optinal)
```
sudo pacman -Rns light-locker
yay -S betterlockscreen
cp /usr/share/doc/betterlockscreen/examples/betterlockscreenrc ~/.config
betterlockscreen -u /usr/share/backgrounds/wallpapers-2018/palm-wave.jpg
```
Set shortkey;
```
betterlockscreen -l dim
```
`Right click -> properties` on whisker menu(manjaro icon at bottom-left of the screen). Change lock screen command with `betterlockscreen -l dim` at Commands tab.
**Reset all keyboard shortcut Settings  →  Keyboard  (optionally)**
Add super key whiskermenu
```
xfce4-popup-whiskermenu
```
**Change show desktop shortcut Settings  →  Window Manager  →  Keyboard  → Show Desktop**
### Dual-boot Wrong time problem
```
timedatectl set-local-rtc 1 --adjust-system-clock
```
### Adblock Spotify
```
yay -S --mflags --skipinteg --needed spotify spotify-adblock
```

### SSD
>  :exclamation: If you have a SSD, you should enable fstrim.

```
sudo systemctl enable fstrim.timer
```
### If skype not run
```
sudo sysctl kernel.unprivileged_userns_clone=1
```
### If headphones not detected when restart (after startup not working, I am working on it )
```
sudo nano /etc/pulse/default.pa
```
at the bottom under `### Make some devices default` put
```
set-default-sink 3
set-default-source 3
```
## Nvidia Options
**There are many options for installing nvidia driver. Follow the [link](https://forum.manjaro.org/t/options-for-nvidia-optimus-graphics/75185)**

### Open Wifi Hotspot
```
sudo create_ap wlp5s0 wlp5s0 MyAccessPoint password
```

#### Libre Office icon;
```
yay -S papirus-libreoffice-theme
```
After that;
LibreOffice->tools->options->View->Icon Style->Papirus
### For Other Partitations
If you have another partition(E, D etc.). You can mount it on the startup. Thus some applications which are using other partitions don't get an error.

```
lsblk -f
```
The command shows your disks uuid.
```
sudo gedit /etc/fstab 
```
Open your fstab config with the command. You should add codes similar to the following example. You should change UUID and /run/media/yourUserName/Partition.
```
UUID=b336b98e-d0b5-4254-b6aa-9e66f85b0dfc /run/media/oguz/Files ext4 defaults  0 0
```

>  :exclamation: If you use manjaro with dual boot, you should close fast-startup,hibarnate on your Windows, otherwise, you have not a write permission for other partitions.
#### For Android Studio(KVM);
```
sudo pacman -S virt-manager qemu vde2 ebtables dnsmasq bridge-utils openbsd-netcat
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
```

yay -S candy-icons-git

git clone https://github.com/EliverLara/firefox-sweet-theme/ && cd firefox-sweet-theme
./scripts/install.sh -g

