# rpioslite-wn722nv4-driver
how to install a functional driver with monitor mode and package injection on raspberry pi os lite 32 bit legacy



# Setting up rtl8188eus Driver on Raspberry Pi OS Lite 32-bit Legacy

Follow these steps to set up the rtl8188eus driver on Raspberry Pi OS Lite 32-bit legacy.

## Update and Upgrade the System
\`\`\`bash
sudo apt update
sudo apt upgrade
sudo reboot
\`\`\`

## Install Required Packages
\`\`\`bash
sudo apt install bc
sudo apt-get install build-essential
sudo apt-get install libelf-dev
sudo apt install raspberrypi-kernel-headers
\`\`\`

## Download and Compile the Driver
\`\`\`bash
cd ~/Desktop
git clone https://github.com/KanuX-14/rtl8188eus.git
cd rtl8188eus
\`\`\`

## Blacklist Existing Driver
\`\`\`bash
sudo -i
echo "blacklist r8188eu" > /etc/modprobe.d/realtek.conf
echo "blacklist 8188eu" >> /etc/modprobe.d/realtek.conf
exit
\`\`\`

## Compile and Install the Driver
Open the folder with the drivers in a terminal:
\`\`\`bash
sudo make
sudo make install
sudo modprobe 8188eu
\`\`\`

## Modify Boot Configuration
Edit the `config.txt` file to force 32-bit mode and allow connection through USB-C.
\`\`\`bash
sudo nano /boot/config.txt
\`\`\`
Add the following lines at the end of the file:
\`\`\`
arm_64bit=0
dtoverlay=dwc2,dr_mode=host
\`\`\`

Save and exit the editor.

## Reboot the System
\`\`\`bash
sudo reboot
\`\`\`

Follow these steps carefully to set up the rtl8188eus driver on your Raspberry Pi OS Lite 32-bit legacy.
