https://github.com/GrazerComputerClub/Raspjamming-OS_Banana-Pi-M2-Zero/releases
beware of german keybioard

dpkg-reconfigure locales
deselect german with space
select en-AU UTF-8

sudo nano /etc/default/keyboard
change to us

restart

passwd

wpa_passphrase <wifi_name> <wifi_password> | sudo tee /etc/wpa_supplicant.conf
sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlan0
sudo dhclient wlan0

import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
Physical pin 12 = BCM pin 18
see https://raw.githubusercontent.com/GrazerComputerClub/Raspjamming-OS_Banana-Pi-M2-Zero/master/BananaPiM2ZeroWiringPi.png

