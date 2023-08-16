# Update / upgrade client:
* Check if onedrive is running using `pgrep -l one`
* If it is, kill it using `kill <pid>`
* Rebase on correct location: `git rebase --interactive --onto v2.4.25 upstream/master`
* Reinstall as described [here][1]
```
sudo make uninstall
source ~/dlang/dmd-2.101.2/activate
git pull
./configure --enable-notifications
make clean; make;
sudo make install
```
* Reauthenticate using `onedrive --reauth`
* Run it temporarily using `onedrive --monitor`
* Check if it is running in other terminal `pgrep -l one`
* `Ctrl+C` in monitoring to end the program
* Run from startup program `Startup Applications` in linux GUI. 

[1]: https://github.com/abraunegg/onedrive/blob/master/docs/INSTALL.md
