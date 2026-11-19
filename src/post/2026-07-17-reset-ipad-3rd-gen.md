---
title: Resetting an iPad 3rd Gen Without The Apple ID Password
---

A few years ago, I was given an old 3rd gen iPad ([model A1416](https://en.wikipedia.org/wiki/IPad_%283rd_generation%29)) to recycle. It surprisingly still turned on, so I set it aside to use for a future project. I just tried turning it on again yesterday and discovered that it was still signed in to the previous owner's Apple ID. Erasing the iPad's data requires signing out of the Apple ID account, which I do not have the password for!

I finally discovered a way to get around this and figured I should share the method to hopefully save a few hours of someone's time in the future. :)

This method requires plugging the iPad into a Mac (not sure if this works on Windows with iTunes). For reference, I used a Mac running macOS Tahoe 26.5.2.

Note: this method should only be used to reset an iPad that you rightfully own, and is **not** intended to be used for resetting stolen devices.

## 1. Reboot the iPad into recovery mode

Plug the iPad in to your computer and open Finder. Next, press and hold both the iPad's power button and home button at the same time, and keep holding both buttons. Once the screen goes completely black, release the power button *while keeping the home button pressed*.

After about 10 seconds, the iPad should appear under the device list in Finder. Once it appears, you can let go of the Home button.

If the iPad didn't appear or if the iPad booted to the lock screen, try starting over and doing the same steps again. Getting it to boot into recovery mode can be tricky and it sometimes takes a few attempts.

## 2. Restore the iPad's software

Select the iPad in Finder. If the iPad booted into recovery mode, Finder should show a very simple page with only one or two buttons, one of which giving the option to "Restore". (Unfortunately I didn't get a screenshot here, but if your Finder is showing a full page of information about the device, the iPad likely didn't boot into recovery mode and you should start over.)

Click the "Restore" button and allow the iPad to be reset. This step took about 20 minutes for me, so be patient. When it's finished, the iPad should turn on to a white screen.

## 3. Activate the iPad without an Apple ID

After selecting your language and region on the iPad, it will ask you to connect to a WiFi network. **If you connect to the internet at this step, it'll force you to sign in with an Apple ID, so don't connect to WiFi.** I believe the last supported version of this iPad's iOS is too old to connect to modern Apple accounts. I tried using multiple accounts, one being an old account that had only ever been used with an iPhone 5, but they all failed to activate. The only way I could get past this step is by not signing in to an Apple ID.

On the top right corner of the iPad's WiFi network selection screen, there should be a "Next" button. If the button is gray, press and hold the iPad's power button and press "Reset" on the popup. I had to reset my iPad this way three times before the button started appearing blue without selecting a WiFi network. Once it turns blue, you should be good to go!

## Final thoughts

I haven't tried connecting to an Apple ID again after setting up the iPad. This device will only be used to show a local web page in Safari, so I have no need to log in to an account, but if you have any success doing this, please let me know and I'll update this post!
