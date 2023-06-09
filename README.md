# Union Context Menu
 Custom post-production quick actions for MacOS.
<br><br>

![Union Quick Actions Screenshot](images/union_qa.jpg)
<br><br>

# Description

These installer scripts will install several custom quick actions in MacOS. The installation is streamlined, and user variables are mostly installed automatically via Automator actions.

The scripts install *FFMPEG, IINA, ExifTool, Rysnc, Progress, and Watch.*
Other dependancies are *Adobe After Effects, Adobe Premiere.*

Most of these Quick Actions use a command-line application to monitor progress. They will open a Terminal window and provide updates every 2 seconds for every long action.
<br><br>

# Installation

First, click **Code** at the top of this page and then select **Download Zip.** Unzip the package and copy the `Union_Actions` folder to your *home* folder. You can get to your *home* folder in Finder by clicking `Go > Home` in the top menu. The Union_Actions should now live somewhere like `users/username/Union_Actions`. This location is important. All the scripts look here for user-variables needed to run the Quick Actions. Inside `Union_Actions` is a `InstallScripts.zip` which contains four installation scripts. Unzip them. Then click on each to install them in sequential order. Follow the instructions to manually configure IINA.
> Note: Apple's security policies are going to flip out and you will have to allow usage of each of these scripts in `System Settings > Privacy & Security" 
<br><br>

![Privacy screenshot 1](images/privacy.jpg)
<br><br>


## The Installation Scripts

### 1_InstallHomebrew.app
* This first script installs Homebrew. Homebrew is a package manager that we are using to install other dependencies. Click on the script and follow the instructions. It will ask you to enter your password and press *return*. The password will not be visible when you enter it, so you will have to use your imagination. When finished, it will ask you to run two more commands. **These are important.** Copy and paste them back into Terminal and press Return--one-by-one.
<br><br>

![Homebrew screenshot 1](images/term1.jpg)

![Homebrew screenshot 2](images/term2.jpg)
<br><br>

### 2_InstallSoftware.app
* This second script will install all the applications. It will also upgrade *rsync* to newer version than what is currently packaged with MacOS. Click return and enter a password when it asks for it. Let it run until the end--it will take a while. It's finished when Terminal returns your username, like the screenshot below.
<br><br>

![Homebrew screenshot 3](images/term3.jpg)
<br><br>

### 3_InstallSettings.app
* This third script will connect all the Quick Actions to the software on your computer. It's mostly automated except `aerender` and will ask you to manually navigate to, and select, *aerender*. Choose any random file if you don't have After Effects and don't plan on using the rendering Quick Action. HINT: *aerender* is most likely found at `/Applications/Adobe After Effects 2023/aerender`.
<br><br>

### 4_InstallScripts.app
* The fourth and final step is to copy all the workflow files from `user/username/Union_Actions/Union_Services` to `user/username/Library/Services`. The Library is a hidden folder, so this script will open both folders in Finder--allowing you to copy from one to the other easily.
<br><br>

### Set up the Quick Actions.
* To set up the actions, right-click on any file and click `customize`. Toggle the Quick Actions you want.
<br><br>

![Quick Actions screenshot 1](images/qa1.jpg)

![Quick Actions screenshot 1](images/qa2.jpg)
<br><br>

# Manually Configuring IINA
* In IINA, were are going to set up three custom video filters for the following: ACEScg-to-sRGB color space conversion, HD Safety guides, and UHD safety guides. This configuration will allow us to toggle them on and off whenever needed. To make a new filter, open `/Applicaitons/IINA` and then navigate the menu to `Video > Video Filters`. Click the plus sign to add new filters and save them after setup.
<br><br>

![IINA screenshot 4](images/iina4.jpg)
<br><br>

### HD Safety Guide
* The first filter we will make is for an HD title/action safety guide. Click the plus sign and add a custom FFMPEG filter, add `drawbox` to the *Filter name*, and add this code to *Filter value*: `x=96:y=54:w=1728:h=972:color=green@0.8`. Once this is added and applied, you can name the filter `HD Saftey`, assign a keyboard shortcut, and save the filter for future use.
<br><br>

![IINA screenshot](images/iina.jpg)

![IINA screenshot 2](images/iina2.jpg)

![IINA screenshot 3](images/iina3.jpg)
<br><br>

### UHD Safety Gudie
* Next, we will do the same for a UHD safety guide. Use this code for UHD: `x=192:y=108:w=3456:h=1944:color=green@0.8`.
<br><br>

### ACEScg to sRGB color space conversion
* Click the plus sign and create a 3D LUT filter. Select `Trilinear` and enter the *File Path* to the provided ACEScg LUT--found at `/Users/username/Union_Actions/luts/ACESsRGB_UnionMPV.cube`. Make sure you change *"username"* to *"your"* username (don't just copy and paste this path). You can also drag the `ACESsRGB_UnionMPV.cube` from Finder into the field. Save, name, and assign a shortcut to the filter. NOTE: This will work for any XXXX-to-sRGB/rec709 LUT (in the cube format), so it will also work for camera RAW playback. Add any other 3D LUTS in your workflow by following the same steps.
<br><br>

![IINA screenshot 5](images/iina5.jpg)
<br><br>

# Quick Actions Included

## Find After Effects & Find Premiere
* These two Quick Actions look through a video file's metadata and track back to the software that rendered it. You can use these to find the project that created any video, as long as you render with metadata enabled.
* Usage: right-click on a video. If it finds the source project, it will copy the path to that project to your clipboard. If it knows you can access that project, it will present the option to open the project directly. 
<br><br>

## Transcode to MP4
* This Quick Action allows you to right-click on any video file and transcode it to an MP4 appropriate for an online posting. It also copies any After Effects or Premiere metadata to the MP4, so you can always track back to the original project.
<br><br>

## Copy Path 
* This Quick Action copies the path or any file or folder to the clipboard so you can easily paste it anywhere and share a link to the file or folder.
<br><br>

## Copy LL Path (win)
* Like the Copy Path Quick Action, this iteration converts a Lucid Link MacOS path to a Lucid Link Windows path so you can share links with Windows peers.
<br><br>

## Render After Effects
* This Quick Action will launch *aerender*, the After Effects command-line renderer--allowing you to render After Effects projects in the background. HINT: Renders are faster this way.
* Usage: set up your renders in After Effects and save. Right-Click on the .aep file, and it will render in the Terminal.
<br><br>

## Rsync
* Rsync is a safe way to copy large amounts of data. This Quick Action automates the process and lets you track large data copies. 
* Usage: right-click on a folder and apply. It will ask you to select a destination. While copying, the action will write a timestamped log to your Desktop. 
* It will run a verification pass after copying the files over and print a second log to you desktop. If no files are listed in the second *"verified"* log, the file copy was 100% successful.
<br><br>

# Compatibility

This has only been tested in MacOS Ventura. It should work with older MacOS versions as long as Quick Actions are supported.
<br><br>

# License

You may modify or distribute anything from these scripts as long as it's not for financial gain and you respect the license of any linked dependencies.
