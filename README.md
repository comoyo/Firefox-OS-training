# Firefox OS Training materials

This repo contains the training materials for workshops, app days, etc.

## Containing

1. setup.md contains information for participants on how to set up their environment, GeekPhones etc. on all platforms
2. Firefox Nightly
3. Firefox Simulator
4. Two boilerplate applications to bootstrap development

## How to use it

1. Clone the repo locally
2. Run `./setup.sh`
3. Copy the content of the folder onto a USB stick or make the folder available through a network share

## Sharing folder on network

1. In OS/X go to System Preferences > Sharing
2. Enable File sharing
3. Under 'Options' enable Samba sharing
4. Add the training folder and give Read only rights to everyone

Put a slide up with the following instructions:

* On OSX: In Finder, Go > Connect to Server > `afp://yourip`
* On Windows: In explorer > `\\yourip`
* On Linux: `mount -t nfs [mac's ip or name]:Users/Shared /mnt/[mountfolder]`
