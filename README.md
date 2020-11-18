## Clean out old version
you may need to delete the old rtl88x2bu folder from your home folder first. 

## Run in terminal to install.
```bash
sudo apt update
sudo apt install build-essential git dkms -y
git clone https://github.com/Vertabreak/rtl88x2bu.git
cd rtl88x2bu
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```

## Uninstall
```bash
cd rtl88x2bu
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo dkms remove -m rtl88x2bu -v ${VER}
```
