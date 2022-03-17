# <img src="https://cdn.discordapp.com/attachments/853780763538751498/954086768284672072/38002.png" alt="Android Logo" width="20" height="24"> Fortnite Android Guide

Hey, I've been asked a bit about this "how to get lawin working" so I decided to make a quick yet clear and effective guide for you, so you can understand how to get LawinServer working on Android.

Cr: Shady For Making This Guide Check His [Discord Server.](https://discord.gg/cpRZq2ETC8)

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

## Part 6 - Now, go back to the Apk Folder

With the Fortnite Build APK and the Apk Folder and open Command Prompt.

Navigate to the folder in Command Prompt and run apktool b (foldername). Wait for it to finish, then close Command Prompt.

Now, go inside the Fortnite Folder folder and locate a folder called dist. Inside of it should be an APK. If there's not, check and make sure that nothing went wrong with the build.

(Video: https://streamable.com/hd4jmv)

## Part 7 - Copy the newly made APK over to your phone

Preferably in a folder with no other files.

(Video: https://streamable.com/vz99pf)

## Part 8 - Using MiXplorer to sign the APK.

There are plenty of good tutorials out there on how to do this. I suggest watching [This one.](https://www.youtube.com/watch?v=EEL_tN2OLW0)

## Part 9 - Now, tap on the signed APK in MiXplorer.

If it asks what you would like to install the APK with, press Package Installer.

If a box pops up saying that MiX can't install apps from unknown sources, give the app permission through settings.

Another box may pop up saying that Play Protect has blocked the app. Press Install Anyway.

If another box pops up saying that Play Protect would like to scan the app, ignore it and press No.

Now the APK should be installed!

## Part 10 - Congrats! You have successfully installed the modified app.

In order to have any functionality though, you need to set up a server to connect to.

## Lawin Server - Setup Process 

Prerequisites

NodeJS - https://nodejs.org/dist/v17.1.0/node-v17.1.0-x64.msi

LawinServer - https://tinyurl.com/lawinserver

Fiddler - https://tinyurl.com/fiddlerclassic

(Note: Make sure you install NodeJS with Chocolatey! There should be an option in the installer.)

## Part 1 - Extract the LawinServer ZIP to an empty folder

Now Run install_packages.bat

(Video: https://streamable.com/4q2klc)

## Part 2 - Open Fiddler and click on the FiddlerScript tab.

Then, paste the following code in:

** import Fiddler;

class Handlers
{
    static function OnBeforeRequest(oSession: Session) {
        if (oSession.hostname.Contains(".ol.epicgames.com"))
        {
            if (oSession.HTTPMethodIs("CONNECT"))
            {
                oSession["x-replywithtunnel"] = "FortniteTunnel";
                return;
            }

            oSession.fullUrl = "http://127.0.0.1:3551" + oSession.PathAndQuery;
        }
    }
} **

After that is pasted in, click Save Script.

(Video: https://streamable.com/4q2klc)

## Part 3 - Now, on your Android device.

Navigate to your Wifi settings. Make sure you are connected to the same network that your pc is connected to. Tap on the Settings icon next to the Wifi network, and then tap Advanced

Now tap Proxy and set it to Manual. For the host name, put down the same IP as you put in UE4CommandLine.txt, except without the 8888. Now where it says Proxy Port, put 8888. When you are done, it should look basically the same as this. After you are done, tap Save and exit out of the Settings menu.

Now, open Chrome on your device and go to http://ipv4.fiddler:8888/. You should see some text that says You can download the FiddlerRoot certificate. Click on the blue text. It will download a file, but you will get an error saying Can't install CA certificates. Open Settings on your device and search for Install network certificates. Once you find it, tap on it and navigate to where you have the certificate downloaded. Tap on the certificate and press Done. Now, name the certificate whatever you like and press Done again. It should say that the certificate has been installed.

## Part 4 - open Fortnite on your device.

It should load up like normal.

When you get to the login screen, press Yes, and then press Epic Games. For the email, enter anything followed by @., and put anything for the password.

If everything was done correctly, you should have logged in! It will ask you what firing mode you want, and just pick any. Now press Lobby on the news tab, and boom! You are now connected to LawinServer on your phone.

There you have it! Now you can mess around with LawinServer on your phone. Almost everything that works on PC for LawinServer works on mobile, so try some stuff out!
