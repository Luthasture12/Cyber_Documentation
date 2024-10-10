# BIOS In Depth

Here’s a further look into the BIOS. **NOTE: Most computers nowadays have UEFI as their firmware. UEFI is a more modern version of BIOS. UEFI provides support for larger hard drives, faster boot times, better security features, and a more user-friendly interface. It supports both 32-bit and 64-bit modes.**  
 **However, most people I have interacted with still refer to this firmware and process as the BIOS. I will be calling it BIOS, but know that this covers UEFI, too.**  
The BIOS is stored on a ROM chip on the motherboard. It works closely with the CMOS battery, which keeps track of system settings and the real-world time.  
The BIOS is a type of firmware that does several things: it checks the hardware to make sure all parts are functioning correctly, it uses the boot loader to load the OS from the hard drive and puts it into RAM, it provides a way for the OS to control hardware settings, and it provides an interface for the user to configure hardware settings. This is a lot, so I will break it down.

Steps of BIOS

1. **Power-On Self Test (POST):**  
   1. When you turn on your computer, the BIOS performs a POST to check if the hardware components are functioning correctly. It checks the RAM, CPU, storage devices, and other peripheral devices.  
   2. If any issues are found, the BIOS typically generates a series of beeps or displays error messages, indicating what might be wrong.  
   3. Certain hardware functions are enabled, such as the keyboard.  
2. **Bootstrap Loader:**  
   1. After POST, the BIOS locates and initializes the boot loader. This is a small program that resides on the boot sector of the storage device (e.g., hard drive or SSD) containing the operating system.  
   2. The boot loader then loads the operating system into memory.

During the steps of BIOS, these other functions take place.

**BIOS Setup Utility:**  
During POST, the BIOS includes a setup utility that allows users to configure hardware settings such as system time and date, boot sequence, and hardware configurations. Users can access the BIOS setup utility by pressing a specific key (commonly F2, Del, Esc, or F10) during the POST process.

**BIOS Drivers:**  
During the booting, or loading, of the OS, the BIOS provides low-level drivers that help the computer communicate with hardware components like the keyboard, mouse, and hard drives before the operating system's drivers are loaded. These are helpful for situations in which the operating system’s drivers haven’t loaded or having issues. Then these drivers are available to allow the user to do something.

**BIOS Update:**  
Updating the BIOS can provide new features, support for new hardware, and fix bugs. However, it must be done carefully to avoid corrupting the firmware.   
A file containing the updated version of the BIOS can be put on a flash drive. Then during POST, enter the BIOS setup utility by pressing the corresponding button for your motherboard. Then navigate to the BIOS update function, and it will guide you from there. 