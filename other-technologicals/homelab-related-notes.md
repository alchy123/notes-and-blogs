# Homelab Related Notes

<!-- If note file have it's own folder, use './../readme.md' path to go one back. However if note file doesn't have it's own folder, you should use './readme.md' path to go one back. -->
* [Click here to go one back](./readme.md).

* I am a person that curious and love about the fields of sysadmin, cybersecurity, computer hardwares and electronics, operating systems, hacking culture, free and open source software culture and many other. These fields are not directly my main area, but I am also learning about them in my free time. This file is for my notes from these kinda topics. 

## Some of the things I want to do
* I wanna setup nextcloud, i very liked that software.
* I also want to hold my n8n workflow automations inside of my server.
* I want to use as web server also. The softwares I develop and published can use there as both to stay and as their computing cloud.
* Bug bounty and CTFs
* Learn more about FOSS

## About Static and Dynamic IP
* Servers mostly need static ip's because we want to be able to reach them almost every time. Therefore we are setting them a static ip. Also we are giving static ip to many other devices we want to be able to reach easily most of the time too. But the devices like mobile phones and laptops do not need this static ip. So, we are not giving to them. Therefore they have dynamic ip, their ips change after a certain time or event.
* A **Dynamic IP Adress** is an IP address that changes each time a device connects to the internet or network. A device with Dynamic IP adress could receive a different IP address every time it accesses the network. Dynamic IP addresses are particularly useful in scenarios where devices connect and disconnect frequently, such as in-home networks, public Wi-Fi, or mobile data connections.
    * **DHCP** (Dynamic Host Configuration Protocol) server -> automatically assigning dynamic IP addresses. We would require manual configuration without DHCP server.
* Primary reasons for using Dynamic Addressing
    * Efficient allocation of IP addresses. IPv4 can provide around 4.3 billion unique addresses however this number in not sufficient for the growing number of devices being connected to the Internet.
    * Additionally, it provides some privacy, as the changing IP makes it harder to track a user over time.
* Let's talk about IP adress range. 192.168.0.1 - 192.168.0.254 -> Third part (the part with 0 here) may vary. This is known as a "Class C Network", it contains 256 ip addresses. IP addresses that starts with "192.168." are one of a few ip ranges reserved for private use. This makes them ideal for home networks as they are designed for local use only and aren't rootable over the internet.

### Research About Topic
* I can learn my local ip and some other info with "ipconfig"(for windows) and "ip addr show" commands. However I can't learn my public ip with that commands. To know my public IP, I have to ask an external server, my computer has no way of "seeing" it directly. Here is why:
    * When we bought an internet service from an ISP(Internet Service Provider), we got a thin box. I learned that box is actually named "modem-router combo". With the help of modem-router combo, we can use our internet. And it is doing lots of things inside. I mentioned DHCP server on top my notes. Modem-router combo is actually is a DHCP server too.
    * On the internet, network devices use internet protocol(IP) for communication and transmission. **Public IP address** is a unique numerical value assigned to a device connected to the Internet. When devices make actions(communication and transmission) on the internet, they are using their public IP address given by their ISP(Internet Service Provider). Public IP addresses are actually routable on the Internet, which means that they can be accessed and communicated through any device, from any part or from any region of the world. In IPv4(Internet Protocol version 4), Public IP addresses are assigned to devices on the internet(to the network devices) in the form of classes. These classes are defined by the standard Internet Assigned Numbers Authority(IANA). Internet Protocol version 6 **(IPv6) Standard is classless** - it does not have different classes of IP addresses like the IPv4 standard.
    * Let's talk about IPv4 In the IPv4 IP address space, there are five classes: A, B, C, D and E. Each class has a specific range of IP adresses (and ultimately dictates the number of devices you can have on your network). Primarily, class A, B, and C are used by the majority of devices on the Internet. Class D and E are for special uses. The four octets that make up an IPv4 addresses are conventionally represented by a.b.c.d - such as "127.10.20.30".
    * My modem-router combo also does Network Address Translation(NAT). **NAT is the router side's job btw, therefore we can go and say router instead of modem-router combo**. Understanding NAT and how it is working can help also how our devices communicate with internet. My devices have Private IPs, I only have one public IP from my ISP and that is on my modem-router combo. When I use the internet from my mobile phone, Network Address Translation inside of the modem-router combo works and then hides my Private ID, and show me to the internet with that Public ID.
    * **In a nutshell**, my modem-router combo holds my Public ID and my devices don't have Public IDs. I am communicating with my modem-router combo's Public IP when I use the internet. My modem-router combo is not giving me it's Public IP directly, especially when I use "ip addr show"(linux command) or "ipconfig"(windows command) commands. But when I make a request to a website on the internet, the request leaves my router. The server sees the source IP of the packet, which is my router's public IP. That's why external services can tell me my public IP instantly.

### Some links that I liked and wanted to save it
I also used this links while taking notes. So, we can think of here as a bibliography too.
* [How does the internet work? from cloudflare](https://www.cloudflare.com/learning/network-layer/how-does-the-internet-work/)
* https://www.internetsociety.org/resources/doc/2014/iana-functions-the-basics/
* [IPv4 classes explanation](https://www.meridianoutpost.com/resources/articles/IP-classes.php)
* [IPv6 explanation with examples](https://www.meridianoutpost.com/resources/articles/IPv6-explained-with-examples.php)
* [Internet Protocol version 4 (IPv4) specification](https://www.rfc-editor.org/rfc/rfc791)
* [Internet Protocol version 6 (IPv6) specification](https://datatracker.ietf.org/doc/html/rfc8200)

## Random Notes, Links and Notes

* [ARP Cache - Wikipedia](https://en.wikipedia.org/wiki/ARP_cache)
* [Computer data storage - Wikipedia](https://en.wikipedia.org/wiki/Computer_data_storage) -> I went here because of a curiosity about how version control thing work behind with changes happening in files. So I want to learn more about how are we saving and keep track of the data??
    * About git's vcs -> [Distributed Version Control](https://en.wikipedia.org/wiki/Distributed_version_control)
* [Shebang in Unix](https://en.wikipedia.org/wiki/Shebang_%28Unix%29)
* [WebDAV](https://wiki.archlinux.org/title/WebDAV)

## About Free Software and Many More

### Sources

* [GNU](https://www.gnu.org/) -> Supported by FSF
* [Free Software Foundation](https://www.fsf.org/)
    > "The FSF publishes the GNU General Public License (GNU GPL), the world's most popular free software license, and the only license written with the express purpose of promoting and preserving software freedom"
* [Open Source Hardware Association (OSHWA)](https://oshwa.org/)
* [Open-design Movement](https://en.wikipedia.org/wiki/Open-design_movement)
* [The Open Source Definition Policy](https://en.wikipedia.org/wiki/The_Open_Source_Definition)
    * [Open Source Initiative](https://en.wikipedia.org/wiki/Open_Source_Initiative)
    * [](https://lists.debian.org/debian-announce/1997/msg00017.html)
* [Open Collective](https://opencollective.com/collectives)
* [LibrePhone Project from FSF](https://librephone.fsf.org/) -> I'm following.
* [Free System Distribution Guidelines (GNU FSDG)](https://www.gnu.org/distros/free-system-distribution-guidelines.html) -> This is the reason why GNU is not endorsing many well-known GNU/Linux distros.

### Sources with Explanations

* [Free Software Foundation's Free Software Gang](https://www.fsf.org/working-together/gang) There are thousands of pieces of free software, many of which are listed in Free Software Foundation's directory of free software, but of these projects, a few dozen are extremely common — they call these the free software gang.
* https://directory.fsf.org/wiki/GNU -> automatically-generated list of all GNU packages indexed by the Free Software Directory

## Things I will Research and Learn Further

1. Individual Freedom & Rights
2. Property vs. Commons
3. Voluntary Collabration & Peer Production
4. Open Source & Open Design
5. Licensing
6. Hacker Culture & Ethics
7. Organizations created about those topics and their work 