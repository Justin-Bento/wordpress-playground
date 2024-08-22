# Download Fedora Workstation 40

This guide will walk you through the process of installing Fedora Workstation 40 on your computer.

1. **Visit the Official Fedora Website:**
   - Go to the [Fedora Workstation download page](https://getfedora.org/workstation/).

2. **Download the ISO:**
   - Click on the "Download" button to get the Fedora Workstation 40 ISO file.
   - You can choose to download directly or via torrent.
   
## Step 2: Create a Bootable USB Drive

1. **Insert a USB Drive:**
   - Make sure you have a USB drive with at least 4 GB of space.

2. **Use a Tool to Create the Bootable USB:**
   - **Windows Users:**
     - Download and install [Rufus](https://rufus.ie/).
     - Open Rufus, select the Fedora ISO, and choose the USB drive.
     - Click "Start" to create the bootable drive.
   - **macOS Users:**
     - Use [Etcher](https://www.balena.io/etcher/) to create the bootable USB.
    
## Step 3: Boot from the USB Drive

1. **Restart Your Computer:**
   - Insert the USB drive and reboot your computer.

2. **Enter Boot Menu:**
   - Access the boot menu by pressing the key (usually F12, Esc, F2, or Del) indicated on your screen during startup.

3. **Select USB Drive:**
   - Choose the USB drive from the list of boot options.

4. **Boot into Fedora:**
   - Head over to the boot menu inside your motherboard bios.
   - Select "Start Fedora Workstation Live 40" to boot into the live environment.

## Step 4: Install Fedora Workstation

1.**Test Out Fedora Workstation**
   - Open Up the terminal
   - Run commands like
       - lspci - is a utility for displaying information about PCI buses in the system and devices connected to them.
       - lsblk - list block devices
       - lscpu - display information about the CPU architecture
   - These commands give detailed information about what's under the hood and ensure everything showes up.
   - You can also check your wifi and blutooth connection stability before getting fully commiting to installing linux. 
      
2.  **Start the Installation Process:**
   - In the live environment, double-click the "Install to Hard Drive" icon on the desktop.

2. **Choose Your Language:**
   - Select your preferred language and click "Continue."

3. **Select Installation Destination:**
   - Choose the hard drive where you want to install Fedora.
   - You can choose automatic partitioning or manually configure your partitions.
   - If you have windows or another os fedora will ask you to create seprate paritions. As this is a clean install I'm going to continue.

4. **Set Time and Date:**
   - Configure your time zone and clock settings.

5. **Installation Summary:**
   - Review the installation summary and make any necessary changes.

6. **Begin Installation:**
   - Click "Begin Installation" to start the process.

7. **Set Up Root Password and User Account:**
   - During installation, set the root password and create your user account.
   - Just enter your name and password and leave everything by default.

8. **Wait for the Installation to Complete:**
   - Once done, click "Finish Installation."

9. **Reboot Your System**

