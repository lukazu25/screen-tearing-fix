## Screen Tearing Fix

To configure your graphics card, add a configuration file to `/usr/share/X11/xorg.conf.d` on Linux systems or `/etc/X11/xorg.conf.d` on BSD systems.

For Intel drivers edit or create a file called “10-intel.conf” and add the following then reboot your pc:

```
Section "Device"
  Identifier  "Intel Graphics"
  Driver      "intel"
  Option "TearFree" "true"
EndSection
```
For Radeon drivers edit or create a file called “10-radeon.conf” and add the following then reboot your pc:

```
Section "Device"
  Identifier "Radeon"
  Driver "radeon"
  Option "TearFree" "on"
EndSection
Copy
```
For AMD drivers edit or create a file called “10-amdgpu.conf” and add the following then reboot your pc:

```
Section "Device"
  Identifier "AMDgpu"
  Driver "amdgpu"
  Option "TearFree" "on"
EndSection
```
For Nvidia drivers you’ll need to enable “modsetting”. Run the following two commands to create a file called “nvidia-nomodset.conf” and update the kernel’s initramfs then reboot:

```
sudo echo "options nvidia-drm modset=1" > /etc/modprobe.d/nvidia-nomodset.conf
sudo update-initramfs -u
```
### Fix mate keyboard backlight on startup 

1. Open dconf-editor.
2. Navigate to `/org/mate/power-manager/kbd-brightness-on-ac`.
3. Uncheck "Use default value".
4. Set "Custom value" to 0.

### Install latest nvidia driver on debian
1. Install extrepo package
```
sudo apt install extrepo
```
2. Enable nvidia-cuda repo
```
sudo extrepo enable nvidia-cuda
```
3. Go to `/etc/extrepo/config.yaml` and uncomment contrib and non-free
4. Install nvidia driver 
```
sudo apt install nvidia-open
```
For older cards
```
sudo apt install nvidia-driver
```
