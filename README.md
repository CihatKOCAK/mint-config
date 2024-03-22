# siduction Linux config

last update: 2023-12-27



# Debian Unstable

https://wiki.debian.org/DebianUnstable

siduction is a distro based on Debian Sid (Unstable).

So, let's follow the advises from Debian (from the link above)

```bash
# make sure this package is NOT installed:
apt list --installed unattended-upgrades

# let's be aware of grave bugs or important changes when you install new packages or during an upgrade:
apt install apt-listbugs apt-listchanges
```



# System Upgrade

https://manual.siduction.org/kernel-and-packages_en.html

https://manual.siduction.org/sys-admin-apt_en.html#updating-the-system

```bash
# An upgrade can only be performed when X graphics server is stopped.
# To stop the graphics server, the following command can be entered into a console as root:
su
init 3https://flathub.org/apps/com.discordapp.Discord

# apt full-upgrade is the recommended procedure to upgrade a siduction installation to the latest version.
# A simple apt upgrade of Debian Sid is usually not recommended.
# A system update should be performed regularly, every one to two weeks has proven to be a good guideline.
apt full-upgrade

# Afterwards, start the graphical user interface with the following command:
init 5

# or
reboot
```



# flatpak

```bash
# already installed:
# apt install flatpak
# apt install plasma-discover-backend-flatpak

flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
# restart at this point.
```



# flatpak - PeaZip

Lets's install PeaZip to restore backups easily.

```bash
# install
flatpak install flathub io.github.peazip.PeaZip

# run
flatpak run io.github.peazip.PeaZip
```

output:

```
$ flatpak install flathub io.github.peazip.PeaZip
Looking for matches…
Required runtime for io.github.peazip.PeaZip/x86_64/stable (runtime/org.kde.Platform/x86_64/5.15-23.08) found in remote flathub
Do you want to install it? [Y/n]: y

io.github.peazip.PeaZip permissions:
    ipc     x11     dri     multiarch     file access [1]     dbus access [2]

    [1] host, xdg-config/kdeglobals:ro
    [2] com.canonical.AppMenu.Registrar, org.freedesktop.Notifications, org.kde.KGlobalSettings, org.kde.StatusNotifierWatcher,
        org.kde.kconfig.notify


        ID                                               Branch                 Op            Remote             Download
 1. [✓] io.github.peazip.PeaZip.Addon.i386               stable                 i             flathub              8,3 MB / 8,8 MB
 2. [✓] org.freedesktop.Platform.GL.default              23.08                  i             flathub            162,0 MB / 162,2 MB
 3. [✓] org.freedesktop.Platform.GL.default              23.08-extra            i             flathub             17,8 MB / 162,2 MB
 4. [✓] org.freedesktop.Platform.VAAPI.Intel             23.08                  i             flathub             13,3 MB / 13,4 MB
 5. [✓] org.freedesktop.Platform.openh264                2.2.0                  i             flathub            886,7 kB / 944,3 kB
 6. [✓] org.gtk.Gtk3theme.Breeze                         3.22                   i             flathub            114,3 kB / 191,9 kB
 7. [✓] org.kde.Platform.Locale                          5.15-23.08             i             flathub              4,7 MB / 381,6 MB
 8. [✓] org.kde.Platform                                 5.15-23.08             i             flathub            267,8 MB / 334,4 MB
 9. [|] io.github.peazip.PeaZip                          stable                 i             flathub             10,7 MB / 12,0 MB

Installing 9/9… ████████████████████ 100%  5,4 MB/s
```



# flatpak - Discord

```bash
flatpak install flathub com.discordapp.Discord

flatpak run com.discordapp.Discord
```

https://flathub.org/apps/com.discordapp.Discord



# flatpak - DOSBox-X

```bash
flatpak install flathub com.dosbox_x.DOSBox-X

flatpak run com.dosbox_x.DOSBox-X
```

```bash
~ $ flatpak install flathub com.dosbox_x.DOSBox-X
Looking for matches…

com.dosbox_x.DOSBox-X permissions:
    ipc    network    pulseaudio    x11    devices    file access [1]

    [1] home


        ID                             Branch          Op          Remote          Download
 1. [✓] com.dosbox_x.DOSBox-X          stable          i           flathub         19,3 MB / 19,7 MB

Installation complete.
```

Make sure the directory exists:

```bash
mkdir ~/.var/app/com.dosbox_x.DOSBox-X/config/dosbox-x

touch ~/.var/app/com.dosbox_x.DOSBox-X/config/dosbox-x/dosbox-x-2023.10.06.conf

# optional: add the following line to ~/.bash_aliases
alias dosbox='flatpak run com.dosbox_x.DOSBox-X'
```



# apt packages

```bash
# already installed:
# mc curl htop tree synaptic imagemagick neofetch sweeper build-essential bash-commpletion libreoffice kolourpaint gimp

# not in repos:
# libclamunrar libunrar5

# decided not to install (maybe later)
# bleachbit zeal exuberant-ctags vstfpd lua5.4 love bb
# virtualbox virtualbox-qt virtualbox-ext-pack
# clamav clamav-freshclam
# lazarus-ide

apt install xclip rdfind dos2unix keepassxc kbackup doublecmd-qt kamoso filelight

apt install timeshift  # GTK, but we need this anyway

apt install webhttrack

apt install git make cmake kdiff3 python3-pip python3-full python3-pip python3-virtualenvwrapper

apt install lazarus-ide

apt install nethack-qt
# https://nethackwiki.com/wiki/The_DevTeam_Thinks_of_Everything

apt install udftools  # for KDE partition manager

apt install virtualbox virtualbox-ext-pack virtualbox-guest-additions-iso virtualbox-guest-utils
```



# Kopia

https://kopia.io/docs/installation/#linux-installation-using-apt-debian-ubuntu

```bash
curl -s https://kopia.io/signing-key | sudo gpg --dearmor -o /etc/apt/keyrings/kopia-keyring.gpg

echo "deb [signed-by=/etc/apt/keyrings/kopia-keyring.gpg] http://packages.kopia.io/apt/ stable main" | sudo tee /etc/apt/sources.list.d/kopia.list

apt update

apt install kopia kopia-ui
```

output:

```
The following NEW packages will be installed:
  kopia kopia-ui libayatana-appindicator3-1 libayatana-ido3-0.4-0 libayatana-indicator3-7
```



# Obsidian from FlatHub

https://obsidian.md/download

https://flathub.org/apps/md.obsidian.Obsidian

```
flatpak install flathub md.obsidian.Obsidian

Looking for matches…
Required runtime for md.obsidian.Obsidian/x86_64/stable (runtime/org.freedesktop.Platform/x86_64/23.08) found in remote flathub
Do you want to install it? [Y/n]: y

md.obsidian.Obsidian permissions:
    ipc      network      pulseaudio      ssh-auth      x11      dri      file access [1]     dbus access [2]     tags [3]

    [1] /media, /mnt, /run/media, home, xdg-run/app/com.discordapp.Discord:create, xdg-run/gnupg:ro, ~/.local/share/fonts:ro
    [2] org.freedesktop.portal.Fcitx
    [3] proprietary


        ID                                        Branch           Op           Remote            Download
 1. [✓] md.obsidian.Obsidian.Locale               stable           i            flathub           225,6 kB / 3,6 MB
 2. [✓] org.freedesktop.Platform.Locale           23.08            i            flathub            21,4 kB / 359,7 MB
 3. [✓] org.freedesktop.Platform                  23.08            i            flathub            72,0 MB / 224,7 MB
 4. [✓] md.obsidian.Obsidian                      stable           i            flathub           168,9 MB / 176,0 MB

Installation complete.
```

run:
```
flatpak run md.obsidian.Obsidian
```



# Python packages

Note that `--user` install is not valud anymore:

```
$ pip install --user pynvim


error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.

    If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.

    If you wish to install a non-Debian packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.

    See /usr/share/doc/python3.11/README.venv for more information.
flatpak install flathub com.valvesoftware.Steam
flatpak run com.valvesoftware.Steam
note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.
```

So, make a virtualenv and use it instead:


```bash
apt install python3-pip

mkvirtualenv p3

# assert that p3 is activated.

pip install \
    autopep8 \
    black \
    isort \
    pep8 \
    pylint \
    # end


pip install \
    PyAutoGUI \
    PySimpleGUI \
    click \
    cookiecutter \
    httpie \
    inquirer \
    jedi \
    pipenv \
    prompt_toolkit \
    pynvim \
    pyperclip \
    rich \
    virtualenvwrapper \
    whiptail-dialogs \
    # end
```



# Neovim

neovim in official Debian repositories are too old for LunarVim, since there is no maintainer.

Flatpak version is newer, but it does not integrate with the rest of the system.

So, simply download the most recent version from its official web site:

https://neovim.io/

https://github.com/neovim/neovim/blob/master/INSTALL.md
https://github.com/neovim/neovim/releases


and put its `bin` directory to somewhere in PATH.



# LunarVim - Nerd Fonts

Prerequisite for LunarVim to show icons in console.

https://github.com/ryanoasis/nerd-fonts

If you use Hack font in Konsole, you should install the related Hack fonts.

Here is a direct link:
https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/Hack.zip
from this site:

https://www.nerdfonts.com/font-downloads
(search will not work)



# LunarVim

https://www.lunarvim.org/docs/installation

First, install dependencies:

```bash
apt install git make python3-pip npm nodejs cargo fd-find ripgrep tree-sitter-cli
```

Activate the virtualenv (because it needs pynvim) and run the command to install it:

```bash
workon p3

LV_BRANCH='release-1.3/neovim-0.9' bash <(curl -s https://raw.githubusercontent.com/LunarVim/LunarVim/release-1.3/neovim-0.9/utils/installer/install.sh)
```

run it with:
```bash
touch ~/.config/lvim/init.vim

lvim
```

and run:
```
checkhealth
```



# gaming - NVidia drivers

Backup the system with Timeshift before applying this step.

```
cd /etc/apt/sources.list.d
ls
cat debian.list
```

output:
```
# debian loadbalancer
deb      https://deb.debian.org/debian/ unstable main contrib non-free-firmware
#deb-src https://deb.debian.org/debian/ unstable main contrib non-free-firmware

# deb     https://deb.debian.org/debian/ experimental main contrib non-free-firmware
# deb-src https://deb.debian.org/debian/ experimental main contrib non-free-firmware

# deb      https://incoming.debian.org/debian-buildd buildd-unstable main contrib non-free-firmware
# deb-src  https://incoming.debian.org/debian-buildd buildd-unstable main contrib non-free-firmware
```

Note that there is `non-free-firmware`, but no `non-free` in the default settings of siduction.

https://manual.siduction.org/gpu_en.html

> Since the non-free firmware is usually required for correct operation (AMD, Intel from Skylake on, and Nvidia from Fermi on), an entry similar to
> deb http://deb.debian.org/debian/ unstable main contrib non-free
> should be set. To prevent subsequent problems with WiFi, network, Bluetooth, or similar, a
> apt update && apt install firmware-linux-nonfree
> makes sense. This will install more firmwares than you might need, but that should not be a disadvantage.

https://wiki.debian.org/NvidiaGraphicsDrivers

```bash
apt update && apt install firmware-linux-nonfree nvidia-driver nvidia-detect

apt list --installed | grep nvidia
```



# gaming - Steam

https://flathub.org/apps/com.valvesoftware.Steam

```bash
flatpak install flathub com.valvesoftware.Steam
flatpak run com.valvesoftware.Steam
```

output:
```
Looking for matches…

com.valvesoftware.Steam permissions:
    ipc              network           pulseaudio              wayland                 x11                     devices                   bluetooth
    devel            multiarch         per-app-dev-shm         file access [1]         dbus access [2]         bus ownership [3]         system dbus access [4]
    tags [5]

    [1] xdg-music:ro, xdg-pictures:ro, xdg-run/app/com.discordapp.Discord:create
    [2] org.freedesktop.Notifications, org.freedesktop.PowerManagement, org.freedesktop.ScreenSaver, org.gnome.SettingsDaemon.MediaKeys, org.kde.StatusNotifierWatcher
    [3] com.steampowered.*
    [4] org.freedesktop.UDisks2, org.freedesktop.UPower
    [5] proprietary


        ID                                                           Branch                   Op             Remote              Download
 1. [✓] org.freedesktop.Platform.Compat.i386                         23.08                    i              flathub              95,1 MB / 108,6 MB
 2. [✓] org.freedesktop.Platform.GL.nvidia-525-147-05                1.4                      i              flathub             415,0 MB / 415,0 MB
 3. [✓] org.freedesktop.Platform.GL32.default                        23.08                    i              flathub             143,4 MB / 174,1 MB
 4. [✓] org.freedesktop.Platform.GL32.default                        23.08-extra              i              flathub              19,1 MB / 174,1 MB
 5. [✓] org.freedesktop.Platform.GL32.nvidia-525-147-05              1.4                      i              flathub             414,9 MB / 415,0 MB
 6. [✓] org.freedesktop.Platform.VAAPI.Intel.i386                    23.08                    i              flathub               1,9 MB / 1,9 MB
 7. [✓] com.valvesoftware.Steam                                      stable                   i              flathub              12,0 MB / 13,4 MB

Installation complete.
```

Note that this is the installer.
You need to run it once so that the installer will download the files.



# gaming - ProtonUp-Qt

https://davidotek.github.io/protonup-qt/

https://flathub.org/apps/net.davidotek.pupgui2

https://www.makeuseof.com/install-proton-ge-on-steamos-linux/

```bash
flatpak install flathub net.davidotek.pupgui2

# run it and download the latest proton-ge
flatpak run net.davidotek.pupgui2
```

output:
```
Looking for matches…
Required runtime for net.davidotek.pupgui2/x86_64/stable (runtime/org.kde.Platform/x86_64/6.5) found in remote flathub
Do you want to install it? [Y/n]: y

net.davidotek.pupgui2 permissions:
    ipc     network     wayland     x11     devices     file access [1]     dbus access [2]

    [1] xdg-config/kdeglobals:ro, ~/.bashrc, ~/.config, ~/.kshrc, ~/.local/share/Steam, ~/.local/share/lutris/pga.db:ro, ~/.local/share/lutris/runners, ~/.local/share/lutris/runtime/dxvk,
        ~/.local/share/lutris/runtime/vkd3d, ~/.steam, ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/GamesConfig, ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/gog_store,
        ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/sideload_apps, ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/store_cache,
        ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/tools, ~/.var/app/com.heroicgameslauncher.hgl/config/legendary, ~/.var/app/com.usebottles.bottles/data/bottles/runners,
        ~/.var/app/com.valvesoftware.Steam/data/Steam, ~/.var/app/net.lutris.Lutris/config/lutris:ro, ~/.var/app/net.lutris.Lutris/data/lutris/pga.db:ro,
        ~/.var/app/net.lutris.Lutris/data/lutris/runners, ~/.var/app/net.lutris.Lutris/data/lutris/runtime/dxvk, ~/.var/app/net.lutris.Lutris/data/lutris/runtime/vkd3d, ~/.zshrc,
        ~/stl:create
    [2] com.canonical.AppMenu.Registrar, org.freedesktop.Flatpak


        ID                                               Branch                 Op            Remote             Download
 1. [✓] org.freedesktop.Platform.GL.default              22.08                  i             flathub            146,5 MB / 146,8 MB
 2. [✓] org.freedesktop.Platform.GL.default              22.08-extra            i             flathub             17,9 MB / 146,8 MB
 3. [✓] org.freedesktop.Platform.VAAPI.Intel             22.08                  i             flathub             13,3 MB / 13,4 MB
 4. [✓] org.kde.Platform.Locale                          6.5                    i             flathub            887,6 kB / 333,4 MB
 5. [✓] org.kde.Platform                                 6.5                    i             flathub            199,7 MB / 263,1 MB
 6. [✓] net.davidotek.pupgui2                            stable                 i             flathub             19,4 MB / 25,0 MB

Installation complete.
```


# gaming - Heroic Launcher (for GOG games)

https://flathub.org/apps/com.heroicgameslauncher.hgl

```bash
flatpak install flathub com.heroicgameslauncher.hgl

# run
flatpak run com.heroicgameslauncher.hgl
```

output:
```
Looking for matches…

com.heroicgameslauncher.hgl permissions:
    ipc            network       pulseaudio       wayland               x11
    devices        devel         multiarch        file access [1]       dbus access [2]

    [1] /mnt, /run/media, /run/udev:ro, xdg-desktop, xdg-documents,
        xdg-run/app/com.discordapp.Discord:create, ~/.local/share/applications, ~/.local/share/lutris,
        ~/.steam, ~/.steam/steam, ~/.var/app/com.valvesoftware.Steam, ~/Games/Heroic:create
    [2] org.kde.StatusNotifierWatcher


        ID                                 Branch        Op        Remote         Download
 1. [✓] com.heroicgameslauncher.hgl        stable        i         flathub        155,0 MB / 160,6 MB

Installation complete.
```
