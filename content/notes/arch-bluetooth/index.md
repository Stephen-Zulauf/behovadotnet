---
title: "Arch- Connect BlueTooth"
date: 2024-07-14
# weight: 1
# aliases: ["/first"]
tags: ["arch", "linux", "blue-tooth", "connect"]
categories: ["notes"]
author: "behoovah"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: true
comments: false
# description: "Desc Text."
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: false
ShowWordCount: true
ShowRssButtonInSectionTermList: false
UseHugoToc: true
# cover:
  #  image: "<image path/url>" # image path/url
  #  alt: "<alt text>" # alt text
  #  caption: "<text>" # display caption under cover
  #  relative: false # when using page bundles set this to true
  #  hidden: true # only hide on current single page
# editPost:
  #  URL: "https://github.com/<path_to_repo>/content"
  #  Text: "Suggest Changes" # edit text
  #  appendFilePath: true # to append file path to Edit link
---
### Make sure Packages are Installed
[Bluez](https://archlinux.org/packages/?name=bluez) and [bluez-utils](https://archlinux.org/packages/?name=bluez-utils)
are required for bluetooth ctl.

### Start/Enable Bluetooth Service
```
# systemctl start bluetooth.service
```
### Start bluetoothctl 
```
# bluetoothctl
```
This will start an interactive prompt. 
```
# exit
```
to exit
### Enter Scan
```
# scan on
```
to begin looking for devices to pair.
### Pair
You can highlight the mac address of the device you want to pair
then:
```
ctrl+shift+c
```
to copy it to the clipboard.
then type

```
# pair ctrl+shift+v
```
to copy in the mac address. once this is successful move onto the next step.
### Connect
```
# connect ctrl+shift+v
```

to copy the mac address back in and connect to the device.
