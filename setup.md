
# How to setup your environment to work on Firefox OS

Thanks for being with us on this event! This document describes all the steps required to setup your local environment to work with Firefox OS.

The initial prerequisites for all platforms are:

1. Mozilla Firefox 
    (Nightly version for
     [windows](firefox-24.0a1.en-US.win32.installer.exe),
     [osx](firefox-24.0a1.en-US.mac.dmg),
     [linux32](firefox-24.0a1.en-US.linux-i686.tar.bz2),
     [linux64](firefox-24.0a1.en-US.linux-x86_64.tar.bz2))
2. Firefox OS Simulator (drag the .xpi file into Firefox,
     [windows](firefox_os_simulator-3.0-fx-windows.xpi),
     [osx](firefox_os_simulator-3.0-fx-mac.xpi),
     [linux](firefox_os_simulator-3.0-fx-linux.xpi))
3. Node.js
    ([windows](node-v0.10.5-x86.msi),
     [osx](node-v0.10.5.pkg),
     [linux](node-v0.10.5.tar.gz))
4. An IDE or text editor

## Application templates

This guide comes with two application templates.

* [simple-app](simple-app.zip), which is the most simple Firefox OS application imaginable. It comes with an index HTML file, a manifest and the [building blocks](http://buildingfirefoxos.com/building-blocks/) for rapid prototyping.
* [complex-app](complex-app.zip), a more complex Firefox OS application built on top of [AngularJS](http://angularjs.org/). It comes with page transitions, offline support via appcache and 3rd party resource caching. ([Project page on github](https://github.com/comoyo/ffos-list-detail))

## Testing dependencies

To verify that your setup is completed, open Firefox and go into:

* Windows: Firefox button > Web Developer > Firefox OS Simulator
* OSX/Linux: Tools > Web Developer > Firefox OS Simulator

Now click the 'Add Directory' button and locate the manifest.webapp file in your app template (for complex-app, go into the www/ folder).

The simulator should start your application and all should be good.

## Development workflow

Developing through the simulator will be quite cumbersome so it is recommended to do all development in the browser. Both projects contain a simple static web server that help you with this. Open a terminal or command line and navigate to the project folder. Then run:

    node server.js

The application is now available under [http://localhost:8081](http://localhost:8081) (complex-app) or [http://localhost:8082](http://localhost:8082) (simple-app).

As long as you don't use sensors or anything that requires a real phone this is an excellent way of developing. First develop in the browser, then verify in simulator and then test on device.

# Pushing to GeeksPhone

To push your application to your [GeeksPhone](http://www.geeksphone.com/) you will need some additional configuration.

After running through these steps you will have a 'Push' button in the simulator that you can use to push your application.

## Preparing the device

1. Go into Settings > Device Information > More Information > Developer
2. Toggle 'Remote debugging'

## Windows XP / Vista / 7

1. Download the [driver for Windows](windows-driver.zip)
2. Plug in the device and wait a while
3. A message will appear that installation failed
4. Go into '[Device Management](http://pcsupport.about.com/od/windowsxp/f/opendmxp.htm)'
5. Locate the 'Android' entry
6. Right click and choose 'Update driver software'
7. Manually locate the windows-driver folder and let the device install
8. If being prompt about an unsafe driver, install anyway
9. Unplug the device and re-plug it in

## Windows 8
1. [Follow these instructions](http://www.craftedge.com/tutorials/driver_install_windows8/driver_install_win8.html)
2. Now follow the Windows 7 instructions

## Linux

1. Create a file `/etc/udev/rules.d/51-android.rules`
2. Add the following line  
      
    `SUBSYSTEM=="usb", ATTR{idVendor}=="05c6", MODE="0666", GROUP="plugdev"`
3. Execute `chmod a+r /etc/udev/rules.d/51-android.rules`
4. Run `sudo service udev restart`
5. Plug in the device
6. Go into `~/.mozilla` and execute `find . -name adb`
7. You will find a path in the form of 'r2d2b2g@mozilla.org/resources/r2d2b2g/data/XXXX/adb/adb'
8. Cd into that directory
9. Run `./adb devices`

If everything is OK you will see the name of the device (e.g. full_keon). If you see '?????????' and a permissions error:

1. Run `./adb kill-server`
2. Run `sudo ./adb start-server`
3. Run `./adb devices` and verify

## OS/X

No actions required

# Troubleshooting

## I pushed but my app doesn't show up?

This is a known problem. The 'Application installed' message appears but there is no icon for the application in the home screen. To get around this:

* Swipe all the way left to everything.me and type in the app name
* Or restart the device

## I re-pushed my app but it isn't updated

1. Hold the home button
2. Close your running application
3. Re-launch


