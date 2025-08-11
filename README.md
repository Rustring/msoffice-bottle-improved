## Desctiption

This guide should help you run Microsft Office all the way from 2007 to 2016 on bottles using WINE, 2019 and onwards are unfortunately not possible, or are very hard to install.

### Note:

1. This is not strictly made by me, I made the original guide a little better, the original one is [here](https://github.com/tazihad/msoffice-bottle).
2. It is more reccomended to use the ISO as it just works, and generally there can be issues with the online installer.

## Microsoft Office 2007, 2010

Screenshot of Office 2007 (Taken by me):

![Screenshot_20240701_123107](https://github.com/user-attachments/assets/d659516e-73e3-4e9c-96dc-ae448c32429e)

*Prerequisite:*   
[Flatpak](https://flatpak.org/setup/)  
[Bottles installed by Flatpak](https://flathub.org/apps/com.usebottles.bottles)  

Permissions:  
Give drive permissions using flatseal or do from commandline
```
flatpak override com.usebottles.bottles --user --filesystem=xdg-data/applications
flatpak override com.usebottles.bottles --user --filesystem=home
```

1. Download WINE Runner:
```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-8.2 && \
wget https://www.playonlinux.com/wine/binaries/phoenicis/upstream-linux-x86/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz \
-O /tmp/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz && \
tar -xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-8.2 --strip-components=1 \
-f /tmp/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz && \
rm /tmp/PlayOnLinux-wine-8.2-upstream-linux-x86.tar.gz
```

If you cant download from here, or is too slow, download from the release [here](https://github.com/Rustring/msoffice-bottle-improved/releases/tag/sample-tag).

2. Create a new bottle using Bottles and name it whatever (it's reccomened there's no spaces for ease in later steps)  
3. Environment `Custom`.  
4. From Custom `Runner: pol-8.2`. Architecture: `32-bit`.  
5. Configaration: Select `office2010.yml`.  
6. Click `Create`.
   
![Screenshot_20240701_113937](https://github.com/tazihad/msoffice-bottle/assets/19417232/916c186a-08c8-4b81-8504-21ae0bab7dd3)  

> Unfortunately for some bug, DLL override doesn't get imported from yml. So, we do this manually.

7. From the bottle you created go to -> `Setting` -> `DLL Overrides` -> add `gdiplus` & `riched20`.

If it doesn't work, add `WINEDLLOVERRIDES="gdiplus=n,b;riched20=n,b" %command%` to the launch options of the setup and applications.

![Screenshot_20240701_114718](https://github.com/tazihad/msoffice-bottle/assets/19417232/ef064bed-62aa-4349-9424-7188cb4f6cb0)  

8. That's it. Now install 32-bit version of *MS Office 2010*. Find the executable and run with Bottles.  

### Fixes To Common Problems

If wine runner `8.2` doesn't work use wine runner `3.0.3`:

```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-3.0.3 && \
curl -L https://www.playonlinux.com/wine/binaries/phoenicis/upstream-linux-x86/PlayOnLinux-wine-3.0.3-upstream-linux-x86.tar.gz \
-o /tmp/PlayOnLinux-wine-3.0.3-upstream-linux-x86.tar.gz && \
tar -xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-9.0 --strip-components=1 \
-f /tmp/PlayOnLinux-wine-3.0.3-upstream-linux-x86.tar.gz && \
rm /tmp/PlayOnLinux-wine-3.0.3-upstream-linux-x86.tar.gz
```

If you find that PowerPoint crashes for no reason, then remove the `riched20` DLL override, by going into -> `Setting` -> `DLL Overrides`  

But do __not__ remove the dependency.

## Microsoft Office 2013, 2016

Screenshot of Office 2013 (Taken by me):

![Screenshot_20240826_170550](https://github.com/user-attachments/assets/96dfb38f-52f3-4531-8846-34a4d06ee509)

Wine runner pol-4.3:
```
mkdir -p ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-4.3 && \
wget https://www.playonlinux.com/wine/binaries/phoenicis/upstream-linux-x86/PlayOnLinux-wine-4.3-upstream-linux-x86.tar.gz \
-O /tmp/PlayOnLinux-wine-4.3-upstream-linux-x86.tar.gz && \
tar -xz -C ~/.var/app/com.usebottles.bottles/data/bottles/runners/pol-4.3 --strip-components=1 \
-f /tmp/PlayOnLinux-wine-4.3-upstream-linux-x86.tar.gz && \
rm /tmp/PlayOnLinux-wine-4.3-upstream-linux-x86.tar.gz
```

The rest of the steps are the same as Office 2010, just use `office2013.yml` or `office2016.yml` as the bottle configurations.

If you cant download from here, or is too slow, download from the release [here](https://github.com/Rustring/msoffice-bottle-improved/releases/tag/sample-tag).

## File Integrations  

Copy all `.desktop` files from [File-Intergrations](https://github.com/Rustring/MsOffice-On-WineBottles-Improved/tree/main/File-Intergrations) and [Applicationn-File](https://github.com/Rustring/MsOffice-On-WineBottles-Improved/tree/main/Applicationn-File) to `~/.local/share/applications` 

Change `Icon` path by changing to your username and bottle path name.  
Change the bottle name (can include spaces) in `Exec`.
