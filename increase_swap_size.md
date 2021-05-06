**Swap** is a special area on a computer, which the OS can use as additional RAM.

*Note: before running the following commands, please make sure you have a backup of your data!*

In the example below, we will resize the swap space available in the /swapfile from 2 GB to 20 GB.

1. Turn off all swap processes  
```sudo swapoff -a```

2. Resize the swap  
```sudo dd if=/dev/zero of=/swapfile bs=10G count=10```

    if = input file  
    of = output file  
    bs = block size  
    count = multiplier of blocks  

3. Change permission  
```sudo chmod 600 /swapfile```

4. Make the file usable as swap  
```sudo mkswap /swapfile```

5. Activate the swap file  
```sudo swapon /swapfile```

6. Edit /etc/fstab and add the new swapfile if it isn’t already there  
```/swapfile none swap sw 0 0```


7. Check the amount of swap available  
```grep SwapTotal /proc/meminfo```
