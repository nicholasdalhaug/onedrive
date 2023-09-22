# Update / upgrade client:
* Uninstall as described [here](https://github.com/abraunegg/onedrive/blob/master/docs/INSTALL.md#upgrading-the-client). 
```bash
sudo make uninstall
```
* Install as if [Ubuntu 22.04 Jammy](https://github.com/abraunegg/onedrive/blob/master/docs/ubuntu-package-install.md#distribution-ubuntu-2204)
, since Mint version not available. 
```bash
sudo apt remove onedrive
sudo add-apt-repository --remove ppa:yann1ck/onedrive
sudo rm /etc/systemd/user/default.target.wants/onedrive.service

sudo rm -rf /var/lib/dpkg/lock-frontend
sudo rm -rf /var/lib/dpkg/lock
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y

reboot
lsb_release -a

wget -qO - https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04/Release.key | gpg --dearmor | sudo tee /usr/share/keyrings/obs-onedrive.gpg > /dev/null
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/obs-onedrive.gpg] https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04/ ./" | sudo tee /etc/apt/sources.list.d/onedrive.list
sudo apt-get update
sudo apt install --no-install-recommends --no-install-suggests onedrive
```

## Check if running and re-authenticating
* Check if onedrive is running using `pgrep -l one`
* If it is, kill it using `kill <pid>`
* Reauthenticate using `onedrive --reauth`
* Run it temporarily using `onedrive --monitor`
* Run from startup program `Startup Applications` in linux GUI. 
