# Box64Droid
Box64Droid is a project with scripts that automate installation of a preconfigured rootfs with [Box64](https://github.com/ptitSeb/box64), [Box86](https://github.com/ptitSeb/box86), [Proton 8.0-2](https://github.com/ValveSoftware/Proton), [DXVK](https://github.com/doitsujin/dxvk), [D8VK](https://github.com/AlpyneDreams/d8vk) installed. Originally a fork of [Box4Droid](https://github.com/Herick75/Box4Droid) with Box64. Still in beta stage, can't launch all games in the world in 4K 60 FPS, note it when you trying launch AAA games

Project chat [available](https://t.me/box64droidchat) in Telegram, also there is a [site](https://Ilya114.github.io/Box64Droid/)

## Do I need root?

Box64Droid using proot to run rootfs, so no, root is not required, chroot also can use.

## Installation instructons

Install [Termux](https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_arm64-v8a.apk) and [Termux-x11](https://github.com/Ilya114/Box64Droid/releases/download/beta/app-debug.apk), then in Termux run Box64Droid install command: `curl -o install https://raw.githubusercontent.com/Ilya114/Box64Droid/main/scripts/install && chmod +x install && ./install`

After the installation is completed, type `box64droid --start`, starting script will start Termux-X11 and show start menu.

You can use Input Bridge, install 0.1.9 apk then just run app in Android and in Wine from start menu

## System requirements 

- Adreno 616+ recommend (Another GPU's supporting but less games work). If you have Adreno 610, you can use this [Turnip](https://github.com/Ilya114/Box64Droid/releases/download/beta/TurnipA610.tar.xz) (to install unpack archive and run `sh install.sh` in terminal mode in unpacked folder then restart Box64Droid and enjoy). If you have have Adreno 730 or 740, you can use this [Turnip](https://github.com/Ilya114/Box64Droid/releases/download/beta/TurnipA7xx.tar.xz) (to install unpack archive and run `sh install.sh` in terminal mode in unpacked folder then restart Box64Droid and enjoy)
- Android 12+ (proot version), Android 10+ (chroot version)
- 64-bit Android 
- You also need at ~4,4 GB (or ~3,3 for VirGL version) free for the installation to go without problems.

## Configuring

You can choose to use environment variables, there are 3 files, `DXVK_D8VK.conf`, `Box64Droid.conf` and `DXVK_D8VK.conf`. These files are created and found in the /sdcard/Box64Droid/ folder after the first Box64Droid run.

The `Box64Droid.conf` file is for you to use the Box86 and Box64 environment variables, see all of them [here](https://github.com/ptitSeb/box86/blob/master/docs/USAGE.md#) and [here](https://github.com/ptitSeb/box64/blob/main/docs/USAGE.md). You can add as many variables as you like.

The `DXVK_D8VK_HUD.conf` file is for you to use the environment variables referring to [DXVK_HUD](https://github.com/doitsujin/dxvk#hud).

The `DXVK_D8VK.conf` file is for you to use the environment variables referring to [dxvk](https://github.com/doitsujin/dxvk/blob/master/dxvk.conf).

## Known issues

- Error when updating Termux packages. Clear Termux data will help.
- Android 12+ can kill Termux, you may get `[Process completed (signal 9) - press Enter]`, to fix run this command in adb shell: `adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"`
- "Control" menu in Wine (in Wine Proton 8.0-2 working fine) shows nothing. You can just open `control` using "Run"
- Box64Droid can exit after start. This is a TFM issue, no have idea why and how to fix. 
- Winetricks runs a long of time when Proton installed (non-root version)

If you has other issues like black screen or crashing game/app run Box64 in debug mode then open issue and attach /sdcard/Box64Droid.log

## Instructionsl how to mount SD-card external HDD/SSD (chroot version)

If you want mount sdcard or external HDD (SSD), you need to add mountpoint maually. For SD-card go to /storage and see (`sudo ls`) folder example `8D3E-2B7K`. For external drives go to /mnt/media_rw and see folder like `C3G3H6B8A56212H7`. Type `nano $PREFIX/bin/box64droid` and add mount command before `sudo chroot login ...` line: `sudo mount --bind /mnt/media_rw/drivename (or /storage/sdcardname) $ROOTFSPATH/needfolder`. You need to create `needfolder` yourself in ~/ubuntu folder by using `sudo mkdir foldername` 

## Things to note

Some issues/instabilities can happen when using Box86 and Box64 in proot environment, so it's not recommended to use Box86 and Box64 in proot as debug/testing environment, there are better options for that.

## Applications which using in Box64Droid
- [Termux-app](https://github.com/termux/termux-app) GPLv3 license
- [Box64 by ptitseb](https://github.com/ptitSeb/box64) MIT license
- [Box86 by ptitseb](https://github.com/ptitSeb/box86) MIT license
- [Proot-distro](https://github.com/termux/proot-distro) GPL-3.0 license
- [Wine Stable, Staging and Staging-tkg GPL-2.1 license](https://wiki.winehq.org/Licensing) (builded by [Kron4ek](https://github.com/Kron4ek) by MIT License), [Wine Proton by Valve](https://github.com/ValveSoftware/Proton) (own license), [Wine GE](https://github.com/GloriousEggroll/wine-ge-custom) (using in Lutris)
- [Termux-x11](https://github.com/termux/termux-x11) GPL-3.0 license
- [DXVK](https://github.com/doitsujin/dxvk) Zlib license
- [Forked Mesa to work Turnip on Adreno 610](https://gitlab.freedesktop.org/Danil/mesa/-/tree/freedreno/feature/a610) 
- [Forked Mesa to work Turnip on Adreno 730 and 740](https://gitlab.freedesktop.org/Danil/mesa/-/tree/turnip/feature/a7xx-basic-support)
- [D8VK](https://github.com/AlpyneDreams/d8vk) Zlib license
- [DXVK-Async](https://github.com/Sporif/dxvk-async) 
- [DXVK-GPLAsync](https://gitlab.com/Ph42oN/dxvk-gplasync)
- [WineD3D for Windows](https://fdossena.com/?p=wined3d/index.frag) GPL-2.0+ License
- [Winetricks](https://wiki.winehq.org/Winetricks)

## Thanks to:
- [Herick75](https://github.com/Herick75) - for Mesa Turnip patches which make possible compile it
- [Inguna87](https://github.com/inguna87) - for start chroot fix for MIUI and Oxygen
- [Alfhashut](https://github.com/alfhashut) - inspired me to try VirGL again and trying help me with him
