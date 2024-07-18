---
title: "WSU Wireless on Arch Linux"
date: 2024-07-17
# weight: 1
# aliases: ["/first"]
tags: ["Linux", "Arch", "WSU", "Wireless"]
categories: ["blog"]
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
## Intro
I've found a way to connect my Arch-Linux laptop to the WSU WIFI reliably. 
Since I had a bit of difficulty figuring this out on my own I thought I would document it here.

I'm assuming you already have wifi capability set-up, and have connected to other networks.
I am using [Network Manager](https://wiki.archlinux.org/title/NetworkManager), with the `nmcli` command to
connect to networks normally. But I found it's easier to use `nmtui`, when dealing with networks that
require a username and a password.

## Download Network Manager
Be sure that you have the [Network Manager](https://wiki.archlinux.org/title/NetworkManager)
package installed. If you do not you can just run:
```
# sudo pacman -S networkmanager
```
To download and install the package.

## Open the TUI
Go to the command line and run:
```
# nmtui
```
This will open a text based gui where you can edit network connections.

## Create the connection
You can use the arrow keys to navigate the menu and enter to make selections. 
do the following:
+ select `edit a connection`
+ select `add`
+ select `WIFI`
+ Optionally name the connection (e.g. 'WSU Wireless')
+ Enter the SSID field exactly as the network name appears (e.g. 'WSU Wireless').
(you can run `# nmcli device wifi list` to scan for the wifi network names)
+ select `security` then choose `WPA & WPA2 Enterprise`
+ select `Authentication` and choose `<PEAP>`
+ Enter in the `Domain` field: `wsu.edu`
+ Under `Inner authentication`, `<MSCHAPv2>` should be selected.
+ Beneath Inner authentication there is a username and password feild. 
The username should be your email without the '@wsu.edu' (e.g. 'jane.doe')
and the password is the normal one you would use for canvas or email.

Everything else should be left blank, when finished scroll all the way down
and select ok. This should create the new connection and bring you back to the
previous menu.

Before you exit you should select `back` and then select `Activate a connection` to be sure 
the new connection is up.

All thats left is to quit out and `# ping www.google.com` to see if it worked.
