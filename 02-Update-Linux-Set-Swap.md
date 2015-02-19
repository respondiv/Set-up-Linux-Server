#### All of these commands has to be performed into SSH terminal

Login to the terminal using root access or with the user account with SUDO permission

**First we need to Update Linux, run this command**

`sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade`

**We will install zip for future use**

`sudo apt-get install zip`

Create a SWAP. The SWAP size is generally preferred to be double the size of your RAM

**Allocate a swap space, this 2 GB is for 1 GB of System RAM**

`sudo fallocate -l 2G /ee-swapfile`

**Secure the swap Space**

`sudo chmod 600 /ee-swapfile`

**Check the SWAP Space whether it has required permission (-rw-------)**

`sudo ls -lh /ee-swapfile`

**Create a SWAP Space**

`sudo mkswap /ee-swapfile`

**Enable SWAP Space**

`sudo swapon /ee-swapfile`

**Check Your SWAP**

```
sudo swapon -s
sudo free -m
```

**To make SWAP Permanent, open the `/etc/fstab` file with nano editor**

`sudo nano /etc/fstab`

Add following line at the bottom of the file

`/ee-swapfile none swap sw 0 0`

Press `ctrl+x` and type `y` to save and exit

**To tweak SWAP setting for better performance, open `/etc/sysctl.conf` file with nano editor**

`sudo nano /etc/sysctl.conf`

Add following line at the bottom of the file

```
# tweak SWAP Setting 
vm.swappiness = 10
vm.vfs_cache_pressure = 50
```

Press `ctrl+x` and type `y` to save and exit

**Reboot the System for changes to be effective**

`sudo reboot now`

Re-Login to the server via SSH

**Check you SWAP**

```
sudo swapon -s
sudo free -m
```






