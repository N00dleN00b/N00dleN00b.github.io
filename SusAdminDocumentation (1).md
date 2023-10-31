# Fall 2023 CYB-3353 Project
## Bristie Rahman

### 1. Installing linux and setting up the DE
First I installed VMWare Workstation Pro using the liscened key issued to me 

Then I went to the archlinux wiki and downloaded an ISO

Then I opened up my VMWare and clicked create new machine 

Next when prompted, I clicked Typical instead of Custom installation

I clicked the installer button and browsed for the iso file 

Then made sure to put Linux as well as Other Linix Kernel 64-bit

After naming my project, I selected 15 GB of disc storage, making sure it split with multiple files

I customized the hardware to make sure it was set to 2 GB memory

After creating my VM, I was prompted with the generic Arch Linux terminal 

following the install instructions, I typed in the root@archiso terminal:

>setfont -d

To partition the disc space I did

>lsblk
>cfdisk /dev/sda

Then I was prompted with a Free space screen where I clicked "New" and make the first partition with a size of 1M type BIOS boot as /dev/sda1 

The next partition had a size of 4GB type Linux swap titled partition /dev/sda2 

The final partition I gave the remained disk space to, titled /dev/sda3 type Linux filesystem 

Then, after exiting the partition menu, I created a filesystem using the command

>mkfs.ext4 /dev/sda3

Following that I made the swapspace allocating the VM

>mkswap /dev/sda2

Checking swapon, I changed directory into mnt

>swapon -a
>cd /mnt

I checked inside with ls and found no lost+found item
>ls

I fixed this by typing the below

>mount /dev/sda3 /mnt
>ls

lost+found is now seen, I proceed utilize pacstrap and get the linux firmware integrated

>pacstrap /mnt base linux linux-firmware nano grub dhcpcd

After all of those linux files downloaded, I wrapped up with the following getting the linux interface going

>genfstab /mnt
>genfstab /mnt >> /mnt/etc/fstab

First I had to move to my root and create a password

>arch-chroot
>passwd

Now inside the arch root, with a password, I install grub
>grub-install /dev/sda
>grub-mkconfig -o /boot/grub/grub.cfg

I exit and reboot welcoming me with the arch linux grub option screen
>exit
>reboot

I then added a user and created a password
>useraddd -m Bristie
>passwd Bristie

### Next the UI

I installed KDE using my terminal which led to my graphical implementation of arch linux

I started with updating

>pacman -Syu

>pacman -S xorg

Then I downloaded the plasma DE so that my virtual env would have applications
>pacman -S plasma-meta kde-applications

Clicking enter and just doing the default applications for all options 

>systemctl enable sddm

>systemctl enable NetworkManager

Then as my arch linux boots I am prompted with a log on screen where I customize my interface a bit

### 2. Create a user account for yourself and codi with sudo permissions. The user name for Codi shall be "codi" and the password shall be "GraceHopper1906" and be set to be changed after login.

I had already created my personal account in the step 1 arch install, so my goal of this part was to make a Codi user with a password change prompt 

>useradd codi 
>passwd codi
>GraceHopper1906

The below command allows codi to be kicked out when he tries to log in
>passwd -e Codi

### 3. Install a different shell other than bash, such as zsh or fish.

>sudo pacman -S zsh
>zsh

### 4. Install ssh and use it to ssh into the class gateway (129.244.245.111).

>sudo pacman -S Openssh
>systemctl status sshd

### 5. Add color coding to the terminal (like you see in the archiso during installation).

I added color using the following commands 
>ls /etc/bash.bashrc
>ls .bashrc
>cp .bashrc .bashrc.backup
>sudo cp /etc/bash.bashrc /etc/bash.bashrc.backup

Going into the browser in my VM I downloaded the color files from ArchLinux Bash/Prompt customization wiki

>cd Documents/Colors/DIR_Colors
>sudo mv bash.bashrc /etc/bash.bashrc
>sudo mv DIR_COLORS /etc/
>mv .bashrc ~/.bashrc
>exit

I proceeded to open up Konsole and was greeted by a colored terminal


### 6. Set the system to boot into the GUI desktop environment.

Apart of step 1. Arch Install above 

### 7. Add a few aliases to .bashrc or .zshrc. Need some ideas for good Linux aliases? Check here.

Alias listed below

>alias brc = ".barshrc"
>alias zsh = ".zshrc"
>alias b = ".bashrc"






>











