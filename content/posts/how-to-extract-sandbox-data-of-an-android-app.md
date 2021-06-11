---
author: "Ali Rezaiyan"
date: 2014-09-28
linktitle: Creating a New Theme
title: How to Extract Sandbox data of an Android App?
categories: [ "Development", "Android" ]
tags: ["adb", "android", "debugging"]
weight: 10
---
A few days ago I faced an issue that was reported to me by one of the beta testers. It was a crash, in the production version, After a lot of struggling with code, I couldn’t reproduce the crash. I understood the problem might be with cached data, I needed to extract the cached data of the installed application (sandbox).

### There are some ways to do that:
* #### Root the device and access the sandbox easily with file explorer applications or anything else.
  If you root your device, it breaks the guarantee! so it's not a preferred way. also makes some security issues!\
  You can do it with an emulator, but its process is more complicated and I'd rather suggest another solution.

* #### With ADB (Android Debug Bridge)
  Android Debug Bridge (ADB) is a versatile command-line tool that lets you communicate with a device. The ADB command facilitates a variety of device actions, such as installing   and debugging apps, and it provides access to a Unix shell that you can use to run a variety of commands on a device.
  
In this article, I'm going to talk about the ADB way, Stay tuned!

### There are two steps:
  #### 1. Get a backup from the desired application.
  #### 2. Extract the backup file.
  
### 1. Get a backup from the desired application
First of all to make sure the device is connected correctly:

    adb devices

To get a backup from the application:

    adb backup -noapk <packageName>
    
_The backup file will be generated in the current directory of your terminal._

### 2. Extract the backup file
  To Extract this backup file with the prefix of .ab you need a tool like android-backup-extractor.
  
It is compressed by DEFLATE algorithm and encrypted by AES.

#### Notice: There are many other tools to extract .ab files.

Then change the directory to here:
  _~/android-backup-extractor/android-backup-extractor-bin/_
  
  And type the following command:\
  
    java.exe -jar abe.jar unpack <DIRDIRECTORY\backup.ab> <DIRECTORY\backup.tar> ""
    



Finally, backup.tar is generated and you can extract that easily with common extractor software and see the content of your application.


Thanks for sticking around till the end, hope you learned something!👋\
Have you any feedback? feel free to reach me on [Twitter](https://twitter.com/arezaiyan), [Linkedin](https://www.linkedin.com/in/rezaiyan)
