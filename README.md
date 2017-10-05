# Creating a bootable USB stick on Ubuntu

The process of creating a bootable USB stick on Ubuntu is based on two simple steps:
1. Formatting the USB stick
2. Copying the desired ISO image into it

These two steps are explained below.

# 1. Formatting
In order to format the USB stick just follow these steps:
1- List all the volumes:
```
sudo df
```

2- Through the previous command, find which volume refers to your USB stick. It should be somenthing like /dev/sbXY where X is a letter and Y a number (example: /dev/sdb1).

3- Unmount the USB volume (look for the name on the previous command; it should be somenthing like `/dev/sdb1`)
```
sudo umount /dev/sdXY
# Example: sudo umount /dev/sdb1
```

4- Format it
```
sudo mkfs.vfat -n 'name_for_your_pendrive' -I /dev/sdXY
# Exemple: sudo mkfs.vfat -n 'MyBootableOS' -I /dev/sdb1
```

# 2. Copying the ISO
To copy the ISO into your USB stick just go through the following steps:

1- Unmount the USB volume
```
sudo umount /dev/sdXY
# Example: sudo umount /dev/sdb1
```

2- Copy the ISO content into the volume:
Atention: You want to run the next command to /dev/sdX and not /dev/sdX1
```
sudo dd if=/path/to/ubuntu.iso of=/dev/sdX bs=4M && sync
# Example: sudo dd if=/path/to/ubuntu.iso of=/dev/sdb bs=4M && sync
```
