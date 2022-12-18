https://github.com/GrazerComputerClub/Raspjamming-OS_Banana-Pi-M2-Zero/releases
beware of german keyboard

sudo dpkg-reconfigure locales
deselect german with space
select en-AU UTF-8

sudo nano /etc/default/keyboard
change to us

sudo raspi-config
3 Boot Options
console and autologin

restart

sudo fdisk /dev/mmcblk0
p // see info
d // delete partition 2
n // recreate partition 2, primary, +6G, erase key
w // write to commit changes
sudo resize2fs /dev/mmcblk0p2
df -h // check that /dev/root is now 6G

passwd

wpa_passphrase <wifi_name> <wifi_password> | sudo tee /etc/wpa_supplicant.conf
sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlan0
sudo dhclient wlan0
add above two lines to /etc/rc.local

https://github.com/EconoHobby/kiln-controller
perform up to activating the venv
cp -r /usr/local/lib/python3.7/dist-packages/RPi ~/kiln-controller/venv/lib/python3.7/site-packages/
cp /usr/local/lib/python3.7/dist-packages/RPi.GPIO-0.7.200708.egg-info ~/kiln-controller/venv/lib/python3.7/site-packages/

import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
Physical pin 12 = BCM pin 18
see https://raw.githubusercontent.com/GrazerComputerClub/Raspjamming-OS_Banana-Pi-M2-Zero/master/BananaPiM2ZeroWiringPi.png
scripts to turn on/off BCM pins 20 and 21

sudo mkdir /mnt/usb


// Bootup sequence
1. read usb
2. if valid wifi base64 file found, replace wpa_supplicant
3. wpa_supplicant and dhclient
4. output ip address (valid or invalid) to usb
5. check if ip address exists, if so turn on wifi LED
6. start server
7. if server running, turn on other server led

/home/pi/kiln-controller/start-on-boot

// TODO cron to lock it
// TODO remove .git, remove git tokens