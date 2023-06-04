# Update / upgrade client:
* As described [here][1]
```
sudo make uninstall
source ~/dlang/dmd-2.101.2/activate
git pull
./configure --enable-notifications
make clean; make;
sudo make install
```
* Then check if onedrive is running using `pgrep -l one`
* Reauthenticate using `onedrive --reauth`
* Run it temporarily using `onedrive --monitor`
* Check if it is running in other terminal `pgrep -l one`
* `Ctrl+C` in monitoring and run from startup program `Startup Applications` in linux GUI. 

[1]: https://github.com/abraunegg/onedrive/blob/master/docs/INSTALL.md
