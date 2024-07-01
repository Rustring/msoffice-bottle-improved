### MS Office 2010
Use Microsoft Office 2010 in Linux using WINE and Bottles.

*Prerequisite:*   
[Flatpak](https://flatpak.org/setup/)  
[Bottles installed by Flatpak](https://flathub.org/apps/com.usebottles.bottles)  


1. Download WINE Runner:
```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-8.2 && wget https://www.playonlinux.com/wine/binaries/phoenicis/upstream-linux-x86/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz -O /tmp/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz && tar -xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-8.2 --strip-components=1 -f /tmp/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz && rm /tmp/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz
```

2. Create a new bottle using Bottles named `office2010`  
3. Environment `Custom`.  
4. From Custom `Runner: pol-8.2`. Architecture: `32-bit`.  
5. Configaration: Select `office2010.yml`.  
6. Click `Create`.
   
![Screenshot_20240701_113937](https://github.com/tazihad/msoffice-bottle/assets/19417232/916c186a-08c8-4b81-8504-21ae0bab7dd3)  

> Unfortunately for some bug, DLL override doesn't get imported from yml. So, we do this manually.
7. From bottle `office2010` -> `Setting` -> `DLL Overrides` -> add `gdiplus` & `riched20`.

![Screenshot_20240701_114718](https://github.com/tazihad/msoffice-bottle/assets/19417232/ef064bed-62aa-4349-9424-7188cb4f6cb0)  

8. That's it. Now install 32-bit version of *MS Office 2010*. Find the executable and run with Bottles.
