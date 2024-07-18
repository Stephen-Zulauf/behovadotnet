---
title: "Arch- wifi"
date: 2024-07-17
# weight: 1
# aliases: ["/first"]
tags: ["wifi", "wireless", "linux", "arch", "connect"]
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

---
## Make Sure Packages Are Installed
[Network Manager](https://wiki.archlinux.org/title/NetworkManager) is the most simple network utility
that I have found.

## Start/Enable Network Manager Service
If you haven't yet you can enter:
```
# systemctl start NetworkManager.service
```
to start the network manager daemon.

## Start Network Manager
You can use the curses tui:
```
# nmtui
```
and use the menus to create/activate a new connection.
or you can use the cli:
+ `# nmcli device wifi list` to scan for networks
+ `# nmcli device wifi connect <SSID_or_BSSID> password <password>` to connect to a network.
+ `ping www.google.com` to test the connection.

see the [arch wiki](https://wiki.archlinux.org/title/NetworkManager#Usage) for a detailed list
of nmcli commands.

---
