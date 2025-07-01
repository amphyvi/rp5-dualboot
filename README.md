# Android/Linux Dualboot on RP5
This guide was, for some reason, "removed by Reddit's filters" after being up for ~8 months. My guess is that Reddit doesn't like it when you edit a post too many times. I was just trying to keep it up to date, but go off, Reddit 🤷‍♀️
[Original thread here](https://www.reddit.com/r/retroid/comments/1h4lxsv/comment/mznsrlh)

There's a few formatting changes on this version since Github is nicer for that sort of thing. All the info is the same though!

-----

Hey everybody, this is Amphy from nowhere in particular. I believe I've done it - I've figured out how to get the best of both Linux and Android on the Retroid Pocket 5 **using one single microSD card**. I'll be filming a video guide for this over the weekend, which I'll share around the community when it's done & link here as well - please look forward to that!

I've written this guide to require as little technical know-how as possible. Everything should be pretty cut and dry. That being said, I'm a technical person myself. So, if I wrote things a little *too* technically, please let me know so I can refine things and/or write in some guard-rails to help the newbies out.

## Before we get started, please be aware that following these steps will wipe your SD card.

There's no way around this that I'm aware of - we're going to need to write Rocknix to the SD card, and that means yeeting your data. I highly recommend either **doing this before you set everything up on your RP5** or **making a complete backup of your SD card to a safe place**. Updating Rocknix afterward should be entirely safe, barring any surprises - it's just the initial setup that requires a wipe.

You will need:

* **A microSD card**. I will save time in this guide by referring to it as "the SD card", but just know it needs to be a microSD card of course - the RP5 will only take microSD cards.
* **Your Retroid Pocket 5** or some other device that can boot to Rocknix from the SD card. Unfortunately, I don't know of any way to do this without having a device in-hand.
* **A computer** to image Rocknix to the SD card of your choice. We'll be using Windows in this guide. macOS *can* work, you will need to find your own substitutes where necessary though!
* A way to connect your SD card to your computer.
* A WiFi network which both your computer & your RP5 can use at the same time.
* Some patience! This is a lot of steps - take them at your own pace and it should be smooth sailing.

### The steps:

1. Connect your SD card to your computer.
2. Download the **latest Rocknix image** (ending in `.img.gz`) from here: [https://github.com/ROCKNIX/distribution/releases](https://github.com/ROCKNIX/distribution/releases) There's a chart saying which image to get. In our case, we'll want the Download Package for **Retroid Pocket 5, Pocket Mini**, etc.
3. If you don't have it already, download the **Rufus setup** from here: [https://rufus.ie/en](https://rufus.ie/en) In our case, we'll be getting the topmost option in the list, "rufus-4.9.exe". The version number may be different when you go to download it, and that's fine - just grab the topmost option in the list.
4. **Run the installer** you downloaded in the previous step. Rufus will then launch. You may be prompted to approve the Windows security message, just press Yes when prompted.
5. We're now at the default Rufus screen. In the **Device** drop-down menu, find your SD card. Rufus is pretty good at determining which of your devices you may want to use, so the chances of it finding a sensitive drive on your computer and putting it in this list is minimal - but still, **be totally sure** you're choosing your SD card here.
6. Once you're entirely sure you chose the SD card in your previous step, press **SELECT** \- it's below the menu mentioned in the previous step, on the right side of the window. **Choose the Rocknix image** you downloaded in step 2 (again, ending in `.img.gz`).
7. The check mark next to the SELECT button will go green (this can be a little hard to tell). Now, just press the **START** at the bottom of the window, and Rufus will flash Rocknix to your SD card. You'll receive a message saying "WARNING: ALL DATA ON DEVICE WILL BE DESTROYED." **Now's a great time to do one final check and make sure you chose that SD card, because this is your last chance.** Once you're ready, press the button that means "yeah man, I wanna do it."
8. If you get a second pop-up that says "IMPORTANT: THIS DRIVE CONTAINS MULTIPLE PARTITIONS" (unlikely that you'll ever see this, unless you're reflashing Rocknix or something!), just press OK to proceed.
9. Rocknix will now flash to the SD card. When it's done, Rufus will ding and can now safely be closed. The SD card is ready to be removed from your computer! **Do that now.**
10. **Put the SD card into your Retroid Pocket 5** (or other device that can boot from it - we'll be assuming you're using your RP5 in this guide). 
    * If you can see the RP5's screen, then the SD card label should face down. (Thanks for suggesting to add this, [tcardlab](https://github.com/amphyvi/rp5-dualboot/pull/1)!)
11. On your RP5, **swipe down** from the top so you find your Android options (Internet, Floating Icon, etc). **Swipe down a second time** to see even more options. At the bottom-right corner, you'll find the Power ⏻ symbol. Press that.
12. Use the option to **Restart**. **Immediately start holding Volume Up** on the top of your RP5. You should get a scary - but entirely safe! - sideways screen with text made for ants. You can let go of Volume Up now.
    * **If you see a lot of options:** Press Volume Up to choose the 2nd option, "Boot". Press Power to confirm it. In my experience, I only ever saw this once.
    * **If you see just a few options in a box:** If you have an RP5, just press Power to select the topmost option, "Retroid Pocket 5". (If you have an RP Mini, press Volume Down to switch options, then press Power.)
13. Your RP5 will now reboot into Rocknix. You'll get some text saying it's doing a lot of things, including "extending" a "file partition". You don't need to remember the terminology, but this is important - it's finishing setting up our SD card for us!
14. Your RP5 will then boot into Rocknix proper. If there's anything you have in mind for Rocknix, the team has a [really helpful Wiki](https://rocknix.org/) you can check out if you want. When you're ready to move on, **press Start** to open the main menu.
15. Navigate down to **System Settings**. **Press A** to choose it. (For those of you who have customized your physical buttons: by default, that will be the face button on the right!)
16. Navigate down to **Security**. Make a note of the **Root Password** as well since you'll need it later - it should be just `rocknix` by default.
17. **Press B** (bottom face button) twice to go back. Navigate up to **Network Settings** and open it with A (right face button). Make sure the following are turned on: **Show Network Indicator**, **Enable WiFi**, and **Enable SSH**.
18. Navigate to **WiFi SSID** and open it with A. Choose your WiFi network.
19. Use **WiFi Key** to enter your WiFi password (if applicable).
20. **Press B** (bottom face button) when you're done to "lock in" your settings. You should get a pop-up that says "WiFi Enabled", press A to acknowledge it.
21. Open **Network Settings** again. **Make a note of the IP address - this is super important**. If you don't see an IP address there (4 groups of numbers with dots between them), press B to go back to the previous menu, then press A again - this will reload the Network Settings menu. (Note: On the latest version of Rocknix, I encountered a bug where the WiFi SSID list was empty while "Enable SSH" was turned on. You may need to turn it off temporarily to get WiFi to connect the first time.)
22. Back to your computer! Now's a good time to make sure it's on the same WiFi network that your RP5 is using.
23. Open **Terminal**. On Windows, just open the 🪟Start menu and type in 'terminal'. The first app result should be Terminal (with a "`>_`" on the icon). Open that.
24. Type in the following text. Please note that all commands from now on need to be typed **exactly** as you see them here, they're case-sensitive. `ssh root@`
25. Without typing in any spaces or typing Enter or anything: **type in the IP address** from step 20. So, for example, if your IP is "192.168.12.34", it would look like this all together: `ssh` `root​@​192.168.12.34`
26. **Press Enter** to start the SSH process. If you're asked if you want to continue connecting, and that the "authenticity" can't be established, just type `yes` and press Enter.
27. You'll be prompted for a password. **Type in the password from step 18** and press Enter. (You won't see anything while you type - that's normal!)
28. You should get "ROCKNIX" in big letters - which means it's ready! Finally, we can use the command which was the whole reason we needed to do all this to begin with. Just type the following and press Enter. `chmod -R 777 /storage`

Give it a few seconds, and... that's it! When it's done, it should just prompt you to type something else if you want, kind of its way of saying it's "ready and waiting" (the ▂ symbol will show up again, like it did before you typed anything on the final step there).

On your device, you'll now have one spot sectioned off (a "partition") for Rocknix with a very fitting `ROCKNIX` label that'll be \~2.1 GB (FAT32) in size. You'll also have a fancy new `STORAGE` partition for the rest of your SD card (ext4) - that's where you'll add your games for both Android and Rocknix to use! Treat this space as you would any normal SD card solution on just about any other handheld... just be sure to not delete the folders Rocknix created (they're all lowercase, i.e. "roms"), otherwise you might run run into headaches in Rocknix.

### Tips, tricks, Q&A, etc:

* **Adding games:** You can use [any of the methods on the Rocknix Wiki](https://rocknix.org/play/add-games/). You can also use [Linux File Systems for Windows by Paragon Software](https://www.paragon-software.com/us/home/linuxfs-windows/#) if you want, which will let you use the SD card directly with your Windows computer at the expense of speed (it's really, really slow!). Perhaps **the best solution to copy files to your RP5** now though is to just **keep the SD card in your RP5**, **boot it into Android**, and **connect your RP5 to your computer using a USB cable**. Transfers are fast, and you can copy to (or from!) the internal RP5 storage and/or the SD card as needed. (You can do this while running Rocknix too, you'll just need to go to Network Settings, then set "USB Gadget function" to "MTP" every time.)
   * **Be sure to point your Android emulators to** `/games-internal/roms/` **to find your ROMs**, The regular `/roms/` may show up as empty on Android. As far as I can tell, it seems to be a Linux filesystem link that Rocknix provides for convenience, and Android doesn't like using links like that.
* **Why is my STORAGE partition empty in Android?** Be sure to update to the latest Android OTA firmware version. As of 2025-06-24, the version number will end in `152` if you're on an RP5.
* **If for some reason Android decides to stop being able to save data to the STORAGE partition:** Just boot into Rocknix & repeat steps 17 onward. I've never experienced this issue and it seems incredibly unlikely to ever happen, but I wanted to include this part just to be safe. A Rocknix over-the-air (OTA) update also shouldn't cause this issue, but you never know.
* **Ready to go back to Android?** Just reboot your RP5 anytime... assuming you didn't change Rocknix to be the default OS of course :)
   * **Want to go back to Rocknix?** Use steps 11-14 again! This process will likely start to feel pretty intuitive/easy after doing it a few times.

I'm no expert when it comes to stuff like this, so please don't expect much if you DM me with any questions you may have. All I did was figure out some basic stuff (with the help of friendly Redditors!) and lay the steps out in a piecemeal format like this. If you know what you're doing, it all boils down to: install Rocknix from the website... boot into it... turn on SSH... and perform the final step haha. I recommend working with the community (i.e. [their Discord](https://www.goretroid.com/pages/about-us)) to troubleshoot things. Thanks!
