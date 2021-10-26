# How to install DietPi

## Downloading the image

First, download the correct version for your Raspberry Pi from the [DietPi website](https://www.dietpi.com/). Scroll down until you reach the downloads section. You want to select your single-board computer (SBC) from the list (this is probably a RaspberryPi), and then download the correct version for the model of your SBC. 

If you have a Raspberry Pi, you'll have many options to choose from. Here is a [screenshot](https://i.imgur.com/km4nXjO.png) of the options you have to choose from. Simply run down the list, and select the version that is compatible with your raspberry pi. If you're unsure, just select the first option. You probably don't want the Amiberry or Allo GUI versions. 

After you have downloaded the correct version, you'll need to extract the .7z file. You can do this using a program called [7-Zip](https://www.7-zip.org/). If you don't have 7-Zip, you can download it from [7-Zip.org](https://www.7-zip.org/).

After you have 7-Zip installed, you can simply right click on the .7z file you downloaded, and click on extract to `\DietPi_xxxxx.7z` (where xxxxx whatever version you downloaded).

In the newly created folder, you'll find a file called `DietPi_xxxxx.img`. This is the image file that you need to flash to your SD card.

To flash your SD card, you'll need a piece of software called "BalenaEtcher". This is a program that you can download from [balena.io](https://balena.io/etcher).

Simply click on "Download for Windows", and then run the program. 

## Flashing your SD card

Now is the time to insert your SD card into your computer. Once you do, in BalenaEtcher, select the image file you downloaded by clicking "Flash from file", and then navigating to where you downloaded that image file from earlier. Then select your SD card you've inserted by clicking on "Select target".

Make sure you have selected the correct target. If a target has a green check mark by it, **BalenaEtcher will flash to it, and erase the entire target** only flash to entries with the correct size as your SD card.

Once you're 100% sure you've put everything correctly in to BalenaEtcher, click "Flash!"

After BalenaEtcher is done, you'll see a message saying "Flashing completed successfully". This means that you've successfully flashed your SD card, and you're ready for the next step.

Insert the SD card in to your Raspberry Pi. If you have a monitor connected, wait a while for the Raspberry Pi to boot.

## First time boot

If you do not have a monitor connected, you'll have to find your Raspberry Pi's IP address. To do this, you can use AngryIPScanner (a program that you can download from [angryip.org](https://angryip.org/)). Simply click on "Free Download", and then run the program. Click on "Start" to beginning scanning. You'll see a entry with a hostname of "DietPi", this is your Raspberry Pi.

Next, you'll need to connect to your Raspberry Pi through PuTTY, you can download it from [putty.org](https://www.putty.org/).

Enter in the Host Name field the IP address of your Raspberry Pi. Then click on "Open" at the bottom. You'll see a black command line window open asking for your username and password.

Your username is: `root`

Your password is: `dietpi`

Once logged in, you'll see a screen like [this](https://i.imgur.com/fZE4j49.jpeg). Simply press the "Enter" key to continue.

It will ask you to join the DietPi-Survey. If you choose to accept, you'll send some usage statistics to the DietPi team. You can view the data they have collected by going to the [DietPi website](https://www.dietpi.com/survey/). If you choose to decline, you won't be asked again, and no data will be sent.

After, you'll be asked to set a new password for your Raspberry Pi. You can choose any password you want, but it's best to choose something that you can remember. You may be asked to set 2 passwords, one to login to the Pi, and one that is used for all software that is installed. 

Now you're done (for the most part)! If you would like, you can now choose software to install. Simply select the category you would like, and then press enter to select the software. After you have selected all of the software you would like, go back, and then select "Go" to install everything you have selected.
