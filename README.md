# jbinto/fix-osx

This repo contains a few tips and tricks for "fixing" an OS X installation to my preferences.

## Disable dashboard

```
defaults write com.apple.dashboard mcx-disabled -boolean true
killall Dock
```
