# Setting Up a Headless Raspberry Pi

## Required Materials

1. Raspberry Pi with Version 1.
2. MicroSD card (minimum 8GB).
3. A computer with an SD card reader.

## Step 1: Download and Install Raspberry Pi Imager

The Raspberry Pi Imager is a tool that lets you download and install an operating system onto your microSD card. Follow these steps to install it:

1. Visit the [Raspberry Pi Imager download page](https://www.raspberrypi.org/software/).
2. Download the appropriate version for your operating system.
3. Install the application on your computer by following the prompts.

## Step 2: Install Operating System with Raspberry Pi Imager

1. Open the Raspberry Pi Imager.
2. Select 'CHOOSE OS'.
3. Select 'Raspberry Pi OS (other)' and choose 'Raspberry Pi OS Lite (32-bit)'.
4. Click on 'CHOOSE SD CARD' and select your SD card.
5. Click 'WRITE' to begin writing the OS to the SD card. This may take a few minutes.

## Step 3: Enable SSH

To enable SSH on your Raspberry Pi, you need to create a file named `ssh` without any extension in the boot partition of your SD card:

1. Once the Raspberry Pi OS image has been written, eject the microSD card and then reinsert it into your computer.
2. The boot partition should automatically mount.
3. In the root directory of the boot partition, create a new file named `ssh` (without any extension).
4. Save and eject the microSD card.

This file acts as a flag, and the Raspberry Pi will enable SSH if it sees this file in the boot partition.

## Step 4: Set Up Wi-Fi

To enable your Raspberry Pi to connect to Wi-Fi, you need to create a file called `wpa_supplicant.conf` in the boot partition. This file contains the WiFi network details.

1. Insert the microSD card back into your computer.
2. Open a text editor and create a new file.
3. In this file, write the following, replacing `your_network_name` and `your_password` with the details of your own WiFi network:

```conf
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="your_network_name"
    psk="your_password"
    key_mgmt=WPA-PSK
}
```