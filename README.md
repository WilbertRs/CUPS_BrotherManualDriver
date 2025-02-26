<img align="right" src="https://visitor-badge.laobi.icu/badge?page_id=WilbertRs.CUPS_BrotherManualDriver" />

# CUPS - How to manually install brother driver for your CUPS Print Server (For newbie like me)
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

Download Driver Installation Tool from Brother Website. Pick the linux deb version (It works on my Ubuntu). From this step, you already know where this is going. For Desktop Version Ubuntu users, you can skip straight to number 4. But for Server Version Ubuntu, I think it's easier to download the driver installation tool from another computer and use a USB drive to move it to the Ubuntu server.

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
sudo cp /media/usb/linux-brprinter-installer-*.*.*-*.gz /cd
```

Don't forget to unmount it!
```sh
sudo umount /media/usb
```

That's it for step 3

<hr/>
<br/>

**4.** Install the printer driver

1. Decompress the file
```sh
gunzip linux-brprinter-installer-*.*.*-*.gz
```
example: linux-brprinter-installer-2.1.1-1.gz


2. Get Superuser
```sh
sudo su
```


4. Install the driver
```sh
bash linux-brprinter-installer-*.*.*-* Brother machine name
```
example: bash linux-brprinter-installer-2.1.1-1 DCP-T310


5. The install process may take some time
<div align="center">
When you see the message "Will you specify the DeviceURI?"
</div>
<div align="center">
For USB Users: Choose N(No)
</div>
<div align="center">
For Network Users: Choose Y(Yes) and DeviceURI number.
</div> 

<hr/>
<br/>

**5.** Add your printer and desired settings. Make sure you share your printer and choose the correct printer driver. Check pictures:
<p align="center">
  <img src="https://github.com/user-attachments/assets/1e0287a7-402d-4267-aef8-5e1861d5c395">
  <img src="https://github.com/user-attachments/assets/4f2065cd-aadf-42a5-841e-e06ae863155f">
  <img src="https://github.com/user-attachments/assets/e656c3f7-257a-4037-9127-1bd7b194abab">
</p>


<hr/>
<br/>

I hope this helps you on manually installing brother driver for your CUPS Print Server. If you have a question just ask on the issues tab.
