# MCHOSEProfileSelector

These scripts let you automatically apply a performance profile (including motion sync, polling rate, DPI, etc.) when launching a Steam game on Linux, and switch to a power-saving profile when closing it.

## Instructions

### Create the chromium user directory:
```bash
mkdir -p $HOME/.config/chromium_profile
```
### Start Chromium using the created user directory:
```bash
chromium --user-data-dir=$HOME/.config/chromium_profile
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
