# headlesspi

This is a simple bash script that installs Arch Linux ARM onto an SD card
and sets it up to automatically connect to a user-specified Wi-Fi profile once the Raspberry Pi is powered on.
This allows easy headlesss setup of the Pi Model A, which lacks an ethernet port.

The basic Arch Linux ARM installation steps are outlined here: https://archlinuxarm.org/platforms/armv6/raspberry-pi

Warning! The script will overwrite your SD card.
Root priviliges are required.

## How to use

1. Insert your SD card into your computer. Use `dmesg` to verify that it was detected
as `/dev/mmcblk0`. This is the device that the script will target.

2. Run the script with `sudo ./rpisetup --install`.

3. Open a terminal and check all the IPs on your LAN with `nmap -sn 192.168.0.1/24`.
Your router address might not be `192.168.0.1`.
You can find out what it is with `ip route show | grep -i 'default via' | awk '{print $3 }'`.

3. Power on the Pi with the prepared SD card. Give it a little time to boot.

4. Run `nmap` again and it there should be a new IP listed.
This is the IP address of the Raspberry Pi.

5. Connect to the Pi with `ssh alarm@<IP>` and log in using the default password `alarm`.
