# Table of contents
* [SSH Keys](#ssh-keys)
* [Windows Envrionment](#windows-environment)
* [Ubuntu Initial Installs](#ubuntu-initial-installs)
* [VSCode](#vscode)
* [Ubuntu Server on Laptop](#ubuntu-server-on-laptop)

# SSH Keys
Create a ssh key on your machine.
```bash
ssh-keygen -t ed25519
cat ~/.ssh/id_ed25519.pub
```
SSH Key Settings:
- [GitHub](https://github.com/settings/keys)

# Windows Environment
### Add bin to PATH
1. Go to `Edit environment variables for your account` (just search)
2. Under `User variables for X` select `Path` and click `Edit`
3. Click on `New` and add the absolute path to the folder

### C++ Compiler
1. Install [msys2](https://www.msys2.org/)
2. Install mingw toolchain
```bash
pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain
```
3. Add `C:\msys64\ucrt64\bin` to [PATH](#add-bin-to-path)
4. Open new `cmd` and use `gcc`

### Git
1. Install [Git for Windows](https://git-scm.com/download/win)
2. Add `C:\Program Files\Git\cmd` to [Path](#add-bin-to-path)
3. Open new `cmd` and use `git`

# Ubuntu Initial Installs
```bash
# update the system
sudo apt update -y && sudo apt upgrade -y

# install curl
sudo apt install curl -y

# install firacode font
sudo apt install fonts-firacode -y

# install vscode
sudo apt-get install wget gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg

sudo apt install apt-transport-https
sudo apt update
sudo apt install code # or code-insiders

# download custom settings.json into vscode
curl https://raw.githubusercontent.com/eat4/environment/main/vscode/settings.json > ~/.config/Code/User/settings.json
curl https://raw.githubusercontent.com/eat4/environment/main/vscode/keybindings.json > ~/.config/Code/User/keybindings.json
```

# VSCode
### Font: Fira Code
https://github.com/tonsky/FiraCode/wiki/Installing

- User [settings.json](./vscode/settings.json)
- [keybindings.json](./vscode/keybindings.json)

### extensions
```text
EditorConfig.EditorConfig
dotenv.dotenv-vscode
ms-vscode.cpptools
ms-vscode-remote.remote-wsl
```

# Ubuntu Server on Laptop
### Disable Closing Lid Sleep Mode
```bash
sudo vim /etc/systemd/logind.conf
# change these
#HandleLidSwitch=suspend
HandleLidSwitch=ignore

#LidSwitchIgnoreInhibited=yes
LidSwitchIgnoreInhibited=no

# restart service
sudo service systemd-logind restart
```

### Turn the screen of the Laptop off/on (does not work via remote ssh, only directly on the machine)
```bash
# off
setterm --blank force

# on
setterm --blank poke

# put them into bash aliases as screenoff/on
```