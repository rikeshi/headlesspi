# headlesspi

This is a simple bash script that installs Arch Linux ARM onto an SD card
and sets it up to automatically connect to a user-specified Wi-Fi profile once the Raspberry Pi is powered on.
This allows the Pi Model A, which lacks an Ethernet port,
to be set up and configured with just a USB Wi-Fi dongle (no screen, keyboard or mouse needed).

The basic Arch Linux ARM installation steps are outlined here: https://archlinuxarm.org/platforms/armv6/raspberry-pi

Warning! The script will overwrite your SD card.
Root priviliges are required.

## Usage

1. Insert your SD card into your computer. Use `dmesg` to verify that it was detected
as `/dev/mmcblk0`. This is the device that the script will target.

2. Run the script with `sudo ./rpisetup --install`.
The downloading and unpacking of the archive can take a while.

3. Open a terminal and check all the IPs on your LAN with `nmap -sn <RouterIP>/24`, e.g. `192.168.0.1/24`.
Your router might have a different IP.
You can find out what it is with `ip route show default | awk '{ print $3 }'`.

3. Power on the Pi with the prepared SD card. Give it a little time to boot.

4. Run `nmap` again and it there should be a new IP listed.
This is the IP address of the Raspberry Pi.

5. Connect to the Pi with `ssh alarm@<IP>` and log in using the default password `alarm`.

## Dependencies

- mkfs.vfat
- wpa_passphrase

Install these with your package manager if they are missing.
