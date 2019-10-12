# Manjaro-Xfce4-Dell-7559
sudo pacman -Sy
sudo pacman -S yay
yay -S lightdm-webkit2-theme-sapphire

Setup Theme

To set the lightdm-theme-sapphire as default theme for login by modifying lightdm-webkit2-greeter.conf, located at

/etc/lightdm/lightdm-webkit2-greeter.conf

Modify [greeter] section and set

webkit_theme = lightdm-theme-sapphire


sudo pacman -Rns light-locker
yay -S betterlockscreen
cp /usr/share/doc/betterlockscreen/examples/betterlockscreenrc ~/.config
betterlockscreen -u /usr/share/backgrounds/gnome/adwaita-day.jpg

Set shortkey;
betterlockscreen -l dim
Edit power Settings.

Remove drop-down from Ctrl+Alt+T shortkey xfce4-terminal.

sudo pacman -S compton polybar rofi

Then click ‘Window Manager Tweaks’, then the ‘Compositor’ tab, and un-tick the ‘Enable Display Compositing’ box:

Go Settings Manager > Session and Start > Auto Start then add compton command `compton --shadow-exclude '!focused' --xrender-sync-fence --vsync`

Add shortkey super key `rofi -show drun`


sudo nano /etc/lightdm/lightdm.conf edit greeter-session=lightdm-webkit2-greeter
