# MCHOSEProfileSelector

These scripts, written in Python and automated with Selenium, automatically apply a performance profile (including motion sync, polling rate, DPI, etc.) when launching a Steam game on Linux, and switch to a power-saving profile when closing it.

## Instructions

### Create the chromium user directory:
```bash
mkdir -p $HOME/.config/chromium_profile
```
### Start Chromium using the created user directory:
```bash
chromium --user-data-dir=$HOME/.config/chromium_profile
```
### Get the Vendor ID and Product ID of your mouse:
```bash
lsusb
```
### Create an udev rule
```bash
nano /etc/udev/rules.d/99-mouse-mchose.rules 
```
### Paste the following line into the file, making sure to include your specific mouse Vendor ID and Product ID:
```bash
KERNEL=="hidraw*", ATTRS{idVendor}=="3837", ATTRS{idProduct}=="100b", MODE="0666", TAG+="uaccess"
```
### Reload udev rules
```bash
udevadm control --reload && udevadm trigger
```
### Open the MCHOSE webdriver website, pair your mouse and create two profiles, one called "Performance" and one called "Powersave":
```bash
www.mchose.com.cn
```
### Copy the scripts to any folder you like and make scripts executable:
```bash
chmod +x Performance.py Powersave.py
```
### Add to Steam Game Commands (change the directory based on where your scripts are):
```bash
python3 ~/Scripts/Performance.py %command%; python3 ~/Scripts/Powersave.py
```
