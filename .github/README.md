# Wireguard (Installer / Manager)
[![GitHub release](https://img.shields.io/github/v/release/complexorganizations/wireguard-installer-manager)](https://github.com/complexorganizations/wireguard-install/releases)
[![ShellCheck](https://github.com/complexorganizations/wireguard-installer-manager/workflows/ShellCheck/badge.svg)](https://github.com/complexorganizations/wireguard-install/actions)
[![GitHub issues](https://img.shields.io/github/issues/complexorganizations/wireguard-installer-manager)](https://github.com/complexorganizations/wireguard-install/issues)
[![GitHub contributors](https://img.shields.io/github/contributors/complexorganizations/wireguard-installer-manager)](https://github.com/complexorganizations/wireguard-install/graphs/contributors)
[![GitHub forks](https://img.shields.io/github/forks/complexorganizations/wireguard-installer-manager?style=social)](https://github.com/complexorganizations/wireguard-install/fork)

---
**What is WireGuard?**

[WireGuard](https://www.wireguard.com/) is an open-source VPN solution written in C by [Jason Donenfeld](https://www.jasondonenfeld.com), aiming to fix many of the problems that have plagued other modern server-to-server VPN offerings like IPSec/IKEv2, OpenVPN, or L2TP. It shares some similarities with other modern VPN offerings like [Tinc](https://www.tinc-vpn.org/) and [MeshBird](https://github.com/meshbird/meshbird), namely good cipher suites and minimal config. As of 2020-01 [it's been merged into the 5.6 version of the Linux kernel](https://arstechnica.com/gadgets/2020/01/linus-torvalds-pulled-wireguard-vpn-into-the-5-6-kernel-source-tree/), meaning it will ship with most Linux systems out-of-the-box.

**WireGuard Goals**
 - strong, modern security by default
 - minimal config and key management
 - fast, both low-latency and high-bandwidth
 - simple internals and small protocol surface area
 - simple CLI and seamless integration with system networking
 
### Prerequisite 
- CentOS, Debian, Ubuntu, Arch, Fedora, Redhat, Raspbian
- Linux Kernel 4.1 or newer
- You will need root access or a user account with `sudo` privilege.

---
### Installation
***Server Installation***
```
wget https://raw.githubusercontent.com/complexorganizations/wireguard-installer-manager/master/wireguard-server.sh -P /etc/wireguard/
bash /etc/wireguard/wireguard-server.sh
```

In your `/etc/wireguard/clients` directory, you will have `.conf` files. These are the client configuration files. Download them from your WireGuard Interface and connect using your favorite WireGuard Peer.

---
### After Installation

- Show WireGuard Interface
- Start WireGuard Interface
- Stop WireGuard Interface
- Add WireGuard Peer
- Remove WireGuard Peer
- Uninstall WireGuard Interface
- Update this script

---
### Features
- Installs and configures a ready-to-use WireGuard Interface
- IPv6 Supported, IPv6 Leak Protection
- Iptables rules and forwarding managed in a seamless way
- If needed, the script can cleanly remove WireGuard, including configuration and iptables rules
- Variety of DNS resolvers to be pushed to the clients
- The choice to use a self-hosted resolver with Unbound.
- Block DNS leaks
- Many other little things!

---
### Options
* `PRIVATE_SUBNET_V4` - private subnet configuration, `10.8.0.0/24` by default
* `PRIVATE_SUBNET_V6` - private subnet configuration, `fd42:42:42::0/64` by default
* `SERVER_HOST_V4` - public IPv4 address, detected by default using `wget`
* `SERVER_HOST_V6` - public IPv6 address, detected by default using `wget`
* `SERVER_PUB_NIC` - public nig address, detected by default
* `SERVER_PORT` - public port for wireguard server, default is `51820`
* `DISABLE_HOST` - Disable or enable ipv4 and ipv6 
* `CLIENT_ALLOWED_IP` - 
* `NAT_CHOICE` - keep alive settings for wireguard client
* `INSTALL_UNBOUND` - Install unbound settings
* `CLIENT_NAME` - name of the client
* `MTU_CHOICE` - the MTU the client will use to connect to DNS

---
### Compatibility with Linux Distro
| OS              | Supported          | i386               | amd64              | armhf              | arm64              |
| --------------  | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| Ubuntu 14.04 ≤  |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |
| Ubuntu 16.04    |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Ubuntu 18.04    |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Ubuntu 19.10 ≥  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Debian 7.x ≤    |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |
| Debian 8.x      |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Debian 9.x      |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Debian 10.x ≥   |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| CentOS 6.x ≤    |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |
| CentOS 7.x      |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| CentOS 8.x ≥    |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Fedora 29 ≤     |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |
| Fedora 30       |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Fedora 31       |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Fedora 32 ≥     |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| RedHat 6.x ≤    |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |
| RedHat 7.x      |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| RedHat 8.x ≥    |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Arch            |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| Raspbian        |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |:white_check_mark:  |
| LXC             |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |
| OpenVZ          |:x:                 |:x:                 |:x:                 |:x:                 |:x:                 |

### Compatibility with Cloud Providers
| Cloud           | Supported          |
| --------------  | ------------------ |
| AWS             |:white_check_mark:  |
| Google Cloud    |:white_check_mark:  |
| Linode          |:white_check_mark:  |
| Digital Ocean   |:white_check_mark:  |
| Vultr           |:white_check_mark:  |
| Microsoft Azure |:white_check_mark:  |
| OpenStack       |:white_check_mark:  |
| Rackspace       |:white_check_mark:  |
| Scaleway        |:white_check_mark:  |
| EuroVPS         |:white_check_mark:  |
| Hetzner Cloud   |:white_check_mark:  |
| Strato          |:x:                 |

---
### Q&A
Which hosting provider do you recommend?
- [Google Cloud](https://gcpsignup.page.link/H9XL): Worldwide locations, starting at $10/month
- [Vultr](https://www.vultr.com/?ref=8211592): Worldwide locations, IPv6 support, starting at $3.50/month
- [Digital Ocean](https://m.do.co/c/fb46acb2b3b1): Worldwide locations, IPv6 support, starting at $5/month
- [Linode](https://www.linode.com/?r=63227744138ea4f9d2dff402cfe5b8ad19e45dae): Worldwide locations, IPv6 support, starting at $5/month

Which WireGuard client do you recommend?
- Windows: [WireGuard](https://www.wireguard.com/install/).
- macOS: [WireGuard](https://apps.apple.com/us/app/wireguard/id1451685025).
- Android: [WireGuard](https://play.google.com/store/apps/details?id=com.wireguard.android).
- iOS: [WireGuard](https://itunes.apple.com/us/app/wireguard/id1441195209).

Is there WireGuard documentation?
- Yes, please head to the [WireGuard Manual](https://www.wireguard.com), which references all the options.

How do i install wireguard without the questions? (Headless Install) ***Server Only***
- ```HEADLESS_INSTALL=y /etc/wireguard/wireguard-server.sh```

**Official Links**
- Homepage: https://www.wireguard.com
- Install: https://www.wireguard.com/install/
- QuickStart: https://www.wireguard.com/quickstart/
- Main Git repo: https://git.zx2c4.com/WireGuard/
- Github Mirror: https://github.com/WireGuard/WireGuard
- Mailing List: https://lists.zx2c4.com/mailman/listinfo/wireguard

---
### Developing
Use a browser based development environment:

[![Open in Gitpod](https://img.shields.io/badge/Gitpod-ready--to--code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/complexorganizations/wireguard-install)

***Debugging***
```
git clone https://github.com/complexorganizations/wireguard-installer-manager /etc/wireguard/
bash -x /etc/wireguard/wireguard-(server|client).sh >> /etc/wireguard/wireguard-(server|client).log
```
___
### Credits
[Angristan](https://raw.githubusercontent.com/angristan/wireguard-install/master/LICENSE)
[l-n-s](https://raw.githubusercontent.com/l-n-s/wireguard-install/master/LICENSE) 

### License 
This project is under the [General Public License](https://raw.githubusercontent.com/complexorganizations/wireguard-install/master/.github/LICENSE)
