# <img src="https://cdn.discordapp.com/attachments/853780763538751498/954086768284672072/38002.png" alt="Android Logo" width="20" height="24"> Fortnite Android Guide

Hey, I've been asked a bit about this "how to get lawin working" so I decided to make a quick yet clear and effective guide for you, so you can understand how to get LawinServer working on Android.

Cr: Shady For Making This Guide

![Example of Fortnite Season 6 Working On Lawin Server With XMPP ](https://cdn.discordapp.com/attachments/853780763538751498/954148891987681310/Screenshot_20220307-141558_Fortnite.jpg)

## Part 0 - Before you start

# Prerequisites
On your PC:
Apktool - https://ibotpeaches.github.io/Apktool/install/

HxD - https://mh-nexus.de/downloads/HxDSetup.zip

Fiddler - https://tinyurl.com/fiddlerclassic

# On your Phone:
MiX File Explorer - https://tinyurl.com/mixfileexplorer

(Note: You do not need to root your phone to follow this tutorial. All you need is a compatible Android device)

Download all the programs listed.

## Part 1 - Choose your build
Well you know, to begin you have to choose one of the builds listed on my archive [here.](https://github.com/Nintendosss/FNAndroid-Archive)

You can see what season you are getting right **here.**

![Season Example](https://cdn.discordapp.com/attachments/853780763538751498/954152830367858759/unknown.png)

## Part 2 - Open Command Prompt

now navigate to the folder that the fortnite apk is in.

After that, run apktool d (apkname).apk

(Video: https://streamable.com/zofnm5)

## Part 3 - HxD Part

Open The Folder That Was Created, lib, and arm64-v8a. You should see a file named libUE4.so.

Open HxD, and then drag and drop libUE4.so onto it.

(Video: https://streamable.com/yn19bk)

## Part 4 - On HxD

Search for these exact hex bytes:

08 01 40 F9 E0 03 1F 2A 1F 01 00 F1 E8 07 9F 1A 68 02 11 39

Now, manually override them with the following hex bytes (DON'T COPY AND PASTE):

1F 20 03 D5 1F 20 03 D5 1F 20 03 D5 08 00 80 52

After you are done, click File -> Save and exit out of HxD.

Note: If at any point it tells you that the file size will change, you did it wrong.

(Video: https://streamable.com/bn0bu6)

## Part 5 - Open Fiddler

in the top left, press on Tools -> Options. Now, click on Connections. Turn on Allow remote computers to connect, Reuse client connections, and Reuse server connections. Press OK and restart Fiddler.

Once Fiddler is restarted, hover your cursor over the [Online] icon in the top right. Write down the smallest IP that is on there as you will need it for later.

Now, go back to the Fortnite folder and open Assets. After that, open UE4CommandLine.txt.

Make a new line under ../../../FortniteGame/FortniteGame.uproject and type in -skippatchcheck -httpproxy=.

Next to -httpproxy=, type in the IP you wrote down, followed by :8888.

Once you are done, the UE4CommandLine.txt file should look something like [This.](https://cdn.discordapp.com/attachments/912818657237815366/912820384980680764/unknown.png) If it does, save it and close it.
