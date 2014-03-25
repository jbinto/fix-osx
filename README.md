# jbinto/fix-osx

This repo contains a few tips and tricks for "fixing" an OS X installation to my preferences.

## Disable dashboard

The OS X dashboard gets in the way of switching desktops with CTRL-LEFT. 

```
defaults write com.apple.dashboard mcx-disabled -boolean true
killall Dock
```

Source: https://apple.stackexchange.com/questions/91722/can-i-disable-dashboard-in-mountain-lion/91723#91723


