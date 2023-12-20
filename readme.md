# Descption
My notes for building my linux machine

# Boot manager
https://www.rodsbooks.com/refind/
https://www.rodsbooks.com/refind/installing.html#packagefile
Installing rEFInd Using an RPM or Debian Package File
I provide RPM and Debian package files for rEFInd; and I maintain an Ubuntu PPA for rEFInd. If you have a working RPM-based or Debian-based Linux installation that boots in EFI mode, using one of these files is likely to be the easiest way to install rEFInd: You need only download the file and issue an appropriate installation command. In some cases, double-clicking the package in your file manager will install it. If that doesn't work, a command like the following will install the RPM on an RPM-based system:

# rpm -Uvh refind-0.14.0-1.x86_64.rpm
On a Debian-based system, the equivalent command is:

# dpkg -i refind_0.14.0-1_amd64.deb
Tip: If you're installing on a system with your own custom Secure Boot keys, as described here, and if you're not using Shim, then you should delete all copies of Shim from your ESP before installing a rEFInd package. The package scripts try to find Shim on the ESP and tell refind-install about it; but if that Shim is unnecessary, then its use to boot rEFInd may result in a Secure Boot failure. Depending on the UEFI implementation, this failure might be unnoticeable, a minor warning message, or a complete system hang or shutdown. Removing unnecessary Shim binaries from the ESP will eliminate this failure condition.
Either command produces output similar to that described for using the refind-install script, so you can check it for error messages and other signs of trouble. The package file installs rEFInd and registers it with the EFI to be the default boot loader. The script that runs as part of the installation process tries to determine if you're using Secure Boot, and if so it will try to configure rEFInd to launch using shim; however, this won't work correctly on all systems. Since version 0.11.0, refind-install supports storing Secure Boot private keys in an encrypted form. If you set up rEFInd in this way, the RPM or Debian package will fail to install, since it assumes an unencrypted Secure Boot key.

If you're using Ubuntu, you should be able to install using the PPA as follows:

$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind
Warning: I know of one bug with the version of rEFInd built with GNU-EFI: On both my 32-bit Mac Mini and an ASUS T100TA tablet, the filesystem drivers hang when launched. This can render the system unbootable until you bypass rEFInd. This bug does not manifest when running the same binaries under a 32-bit VirtualBox, and I've never run into it on any 64-bit system (including a 64-bit MacBook Air). Debugging suggests that a function is being entered mid-function, which implies a bug in the EFI or in the development tools. In any event, the bottom line is to not use the PPA on a 32-bit Mac or the ASUS T100TA.
The PPA version asks if you want to install rEFInd to your ESP. (Chances are you want to respond affirmatively.) The PPA version will update automatically with your other software, which you might or might not want to have happen. It's also built with GNU-EFI rather than with TianoCore. This last detail should have no practical effects.

The installation script makes an attempt to install rEFInd in a bootable way even if you run the script from a BIOS-mode boot, and therefore the RPM and Debian packages do the same. I cannot guarantee that this will work, though, and even if it does, some of the tricks that refind-install uses might not persist for long. You might therefore want to use mvrefind to move your rEFInd installation to another name after you boot Linux for the first time from rEFInd.

My package files install the rEFInd binaries to /usr/share/refind-version, the documentation to /usr/share/doc/refind-version, and a few miscellaneous files elsewhere. (The PPA package omits the version number from the file paths.) Upon installation, the package runs the refind-install script to copy the files to the ESP. This enables you to re-install rEFInd after the fact by running refind-install, should some other tool or OS wipe the ESP or should the installation go awry. In such cases you can use refind-install or install manually.



# Gaming

## SteamVR
https://www.nvidia.com/en-us/drivers/unix/
sudo apt install kde-plasma-desktop plasma-workspace-wayland
