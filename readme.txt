Mentioned is a simple kernel module for a block device driver.
Device is named as "mydisk"
Here, "mydisk" is simulated as a separate block device and we have allocated 512 KiB of space in the memory to it. 
Block driver can also read and write to this virtual disk. 
This disk is partitioned in 3 primary and 3 logical partitions.

Steps  - 
1. Load the driver main.ko using insmod (( >> sudo insmod ./mydisk.ko )) .
(This will create a block device files representing the disk on 512 KiB of RAM, with three primary and three logical partitions)
2. Use ((  >> ls -l /dev/mydisk*  )) for checking the automatically created device files.
    mydisk is entire disk which is 512 KiB in size and it is partitioned into 3 primary (mydisk1, mydisk2, mydisk3) and 3 logical (mydisk5, mydisk6, mydisk7)   partitions.
3. Give sudo permissions using (( >> sudo -s ))
4. Use ((  >> cat > /dev/mydisk1 )) 
Text entered after running above command will be written into disk's first partition (you may choose any partition for the same)
5. Run (( >>  xxd /dev/mydisk1 | less )) to read the text written on partition.
6. Unload the driver using (( >> sudo rmmod ./mydisk.ko )).


