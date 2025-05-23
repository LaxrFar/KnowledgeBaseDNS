---
title: PlayStation PS4/PS5
sidebar_position: 4
---

Game consoles do not support encrypted DNS, but they are well suited for setting up Public AdGuard DNS or Private AdGuard DNS via a linked IP address.

It is likely that your router supports the use of encrypted DNS servers, so you can always configure Private AdGuard DNS on it and connect your game console to it.

[How to configure your router](/private-dns/connect-devices/routers/routers.md)

## Connect AdGuard DNS

Configure your game console to use a public AdGuard DNS server or configure it via linked IP.

### For PlayStation 4

1. Turn on your PS4 console and sign in to your account.
1. From the home screen, select the gear icon located in the top row.
1. Go to *Settings* → *Network* → *Settings*.
1. Select *Set Up Internet Connection*.
1. Select *Use a LAN Cable* → *Easy*.
1. Select *Manual* and then select *Automatic* for *IP Address Settings*.
1. For *DHCP Host Name*, select *Do Not Specify*.
1. For *DNS Settings*, select *Manual*.
1. In the *DNS Server* field, enter one of the following DNS server addresses:
    - `94.140.14.49`
    - `94.140.14.59`
1. Select *Next* to continue.
1. On the *MTU Settings* screen, select *Automatic*.
1. On the *Proxy Server* screen, select *Do Not Use*.
1. Select *Test Internet Connection* to test your new DNS settings.
1. Once the test is complete and you see “Internet Connection: Successful”, save your settings.

### For PlayStation 5

1. Turn on your PS5 console and sign in to your account.
1. From the home screen, select the gear icon located in the top row.
1. Go to *Settings* → *Network* → *Settings*.
1. Select *Set Up Internet Connection*.
1. Select *Set Up Wired LAN* → *Connect*.
1. Select *Manual* and then select *Automatic* for *IP Address Settings*.
1. For *DHCP Host Name*, select *Do Not Specify*.
1. For *DNS Settings*, select *Manual*.
1. In the *DNS Server* field, enter one of the following DNS server addresses:
    - `94.140.14.49`
    - `94.140.14.59`
1. Select *Next* to continue.
1. On the *MTU Settings* screen, select *Automatic*.
1. On the *Proxy Server* screen, select *Do Not Use*.
1. Select *Test Internet Connection* to test your new DNS settings.
1. Once the test is complete and you see “Internet Connection: Successful”, save your settings.

It would be preferable to use linked IP (or dedicated IP if you have a Team subscription):

- [Dedicated IPs](/private-dns/connect-devices/other-options/dedicated-ip.md)
- [Linked IPs](/private-dns/connect-devices/other-options/linked-ip.md)
