# jbinto/fix-osx

This repo contains a few tips and tricks for "fixing" an OS X installation to my preferences.

## Disable dashboard

```
defaults write com.apple.dashboard mcx-disabled -boolean true
killall Dock
```

**Why?** The OS X dashboard gets in the way of switching desktops with CTRL-LEFT. 

Source: https://apple.stackexchange.com/questions/91722/can-i-disable-dashboard-in-mountain-lion/91723#91723

## Disable .DS_Store on remote shares

```
defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

**Why?** OS X (specifically, Finder) will create a .DS_Store in every single directory you open in Finder.

This remembers the state of the Finder window (e.g. what folders are expanded, etc).

Two problems with this:

* It pollutes your network share.
* If the folder state is complex, over a slow link, the initial "connect to server" can appear to freeze for several minutes.

Source: http://support.apple.com/kb/ht1629

## Fix incredibly slow SMB shares

No matter whether accessed via `smb://` or `cifs://`, or whether using Finder or the terminal, all SMB/CIFS access to a Windows 8 share was unusably slow.

`sudo dmesg` showed some of the following (truncated for Google):

     smb_fid_get_kernel_fid: No smb2 fid found for fid ...
     smb_iod_reconnect: Reconnected share ...

Finally fixed by adding the following to `~/Library/Preferences/nsmb.conf`:

    [default]
    smb_neg=smb1_only
