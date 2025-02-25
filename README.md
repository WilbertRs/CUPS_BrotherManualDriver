# CUPS - How to manually install driver for your CUPS Print Server (For newbie like me) (Brother Printer)
I recently created a project to make my old printer into a Wi-Fi printer with a used HG680P STB using Armbian Ubuntu Focal Server. The printer I use is the Brother DCP-T310, but this printer does not have a PPD file available online for CUPS which means I have to install the driver manually. Here's the step-by-step:

<hr/>
<br/>

**1.** Install CUPS Print Server First
<p align="center">
  <img width="483" height="246" src="https://github.com/user-attachments/assets/ddcc8e1f-30d9-46e4-aa03-0daac386a3dc">
</p>
<p align="center">
    https://ubuntu.com/server/docs/install-and-configure-a-cups-print-server
</p>

<hr/>
<br/>

**2.** Download the Driver
<p align="center">
  <img  src="https://github.com/user-attachments/assets/b74cae9e-15ca-4ab2-942f-e653f1da393c">
</p>

Download Driver Installation Tool from Brother Website. From this step, you already know where this is going. For Desktop Version Ubuntu users, you can skip straight to number 4. But for Server Version Ubuntu, I think it's easier to download the driver installation tool from another computer and use a USB drive to move it to the Ubuntu server.

<hr/>
<br/>

**3.** Mount the USB Drive

Move the "linux-brprinter-installer-*.*.*-*.gz" file to a USB drive then mount your USB to the server:

Source: https://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal

1. Find what the drive is called
```sh
lsblk
sudo blkid
sudo fdisk -l
```

You're looking for a partition that should look something like: /dev/sdb1. The more disks you have the higher the letter this is likely to be. Anyway, find it and remember what it's called.

2. Create a mount point (optional)
```sh
sudo  mkdir /media/usb
```

3. Mount
```sh
sudo mount /dev/sdb1 /media/usb
```

4. Move the file to your Ubuntu Server (Recommended)
```sh
cp /media/usb/linux-brprinter-installer-*.*.*-*.gz /
```
  
