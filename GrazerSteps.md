https://github.com/GrazerComputerClub/Raspjamming-OS_Banana-Pi-M2-Zero/releases
beware of german keybioard

dpkg-reconfigure locales
deselect german with space
select en-AU UTF-8

sudo nano /etc/default/keyboard
change to us

restart

passwd

sudo raspi-config
2 Boot Options
console and auto boot

wpa_passphrase <wifi_name> <wifi_password> | sudo tee /etc/wpa_supplicant.conf
sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlan0
sudo dhclient wlan0
add above two lines to /etc/rc.local

import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
Physical pin 12 = BCM pin 18
see https://raw.githubusercontent.com/GrazerComputerClub/Raspjamming-OS_Banana-Pi-M2-Zero/master/BananaPiM2ZeroWiringPi.png
scripts to turn on/off BCM pins 20 and 21

// TODO cron to lock it

// Bootup sequence
1. read usb
2. if valid wifi base64 file found, replace wpa_supplicant
3. wpa_supplicant and dhclient
4. output ip address (valid or invalid) to usb
5. check if ip address exists, if so turn on wifi LED
6. start server
7. if server running, turn on other server led