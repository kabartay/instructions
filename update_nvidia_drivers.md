Update of Nvidia drivers might is essential if:  
- External monitor attached via HDMI is not detected and cannot be used.

To see monitors run `xrandr` in terminal.

Before update of Nvidia drivers:  

    user@user:~$ xrandr 
    eDP-1-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 382mm x 215mm
       1920x1080     60.02*+  40.03    59.93  
       1680x1050     59.95    59.88  
       1400x900      59.96    59.88  
       1280x960      60.00  
       1368x768      59.88    59.85  
       1280x800      59.97    59.81    59.91  
       1152x864      60.00  

After update of Nvidia drivers:  

    user@user:~$ xrandr
    Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
    HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
       1920x1080     60.00*+  75.00    74.97    59.94    50.00  
       1680x1050     59.95  
       1280x1024     75.02    60.02  
       1280x800      59.81    59.91
       1152x864      75.00  
       1024x768      75.03    70.07    60.00  
       800x600       75.00    60.32    56.25  
    eDP-1-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 382mm x 215mm
       1920x1080     60.02*+  40.03    59.93  
       1680x1050     59.95    59.88  
       1400x900      59.96    59.88  
       1280x960      60.00  
       1368x768      59.88    59.85  
       1280x800      59.97    59.81    59.91  
       1152x864      60.00  
       ...


Update procedure is as follows:

Purge and reinstall the Nvidia drivers:

    sudo apt-get purge 'nvidia*'
    sudo add-apt-repository ppa:graphics-drivers
    sudo apt-get update

Then check available drivers by `ubuntu-drivers devices`:

    user@user:~$ ubuntu-drivers devices
    == /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
    modalias : pci:v000010DEd00001F91sv00001043sd0000105Fbc03sc00i00
    vendor   : NVIDIA Corporation
    model    : TU117M [GeForce GTX 1650 Mobile / Max-Q]
    driver   : nvidia-driver-450 - third-party free
    driver   : nvidia-driver-450-server - distro non-free
    driver   : nvidia-driver-460-server - distro non-free
    driver   : nvidia-driver-460 - third-party free recommended
    driver   : xserver-xorg-video-nouveau - distro free builtin
    
Then install selected driver and reboot:  

    sudo apt install nvidia-driver-460
    sudo reboot
    
Done!
