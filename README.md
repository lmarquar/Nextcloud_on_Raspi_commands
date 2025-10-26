# Nextcloud_on_Raspi_commands
these are the commands i need to set up a cloud on the Raspberry pi 5

# Highsideswitch-fan
## circuit:
<img width="440" height="440" alt="image" src="https://github.com/user-attachments/assets/f01977fc-32c6-43df-839f-fcfcaeec8156" />

## append to end of /boot/firmware/config.txt
dtoverlay=gpio-fan  
dtoverlay=gpio-led,gpio=14,label=fan_state  
## cronjobs
@reboot echo 1 > /sys/class/leds/fan_state/brightness  
0 6 * * * echo 1 > /sys/class/leds/fan_state/brightness  
0 22 * * * echo 0 > /sys/class/leds/fan_state/brightness  

# AIO interface/borg password
sudo docker exec nextcloud-aio-mastercontainer grep password /mnt/docker-aio-config/data/configuration.json
