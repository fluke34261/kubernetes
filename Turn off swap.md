# Turn off swap ( for all machine )

1. Turn off swap    
    ```bash
    sudo swapoff -a
    ```
    
2. In case of you reboot machine. Add comment `#` to this line and save
    
    ```bash
    sudo vi /etc/fstab
    #/swap.img  none    swap    sw  0    0
    ```
