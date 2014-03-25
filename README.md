# jbinto/fix-osx

This repo contains a few tips and tricks for "fixing" an OS X installation to my preferences.

## Disable dashboard

The OS X dashboard gets in the way of switching desktops with CTRL-LEFT. 

```
defaults write com.apple.dashboard mcx-disabled -boolean true
killall Dock
```

Source: https://apple.stackexchange.com/questions/91722/can-i-disable-dashboard-in-mountain-lion/91723#91723

## Disable .DS_Store on remote shares

OS X (specifically, Finder) will create a .DS_Store in every single directory you open in Finder.

This remembers the state of the Finder window (e.g. what folders are expanded, etc).

Two problems with this:

* It pollutes your network share.
* If the folder state is complex, over a slow link, the initial "connect to server" can appear to freeze for several minutes.

```
defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

Source: http://support.apple.com/kb/ht1629
