![](https://assets.fireside.fm/file/fireside-images/podcasts/images/7/7296e34a-2697-479a-adfb-ad32329dd0b0/header.jpg)
## 5: ZFS Isn’t the Only Option 

[Link to audio] (https://selfhosted.show/5)
Chris is currently hating [Shinobi](https://shinobi.video/) the open source CCTV solution running on the Raspberry Pi 4. He has bought five Wyze Cams and flashed them with [custom firmware](https://www.reddit.com/r/wyzecam/comments/7w4kx4/openipc_open_source_firmware_with_rtsp_for/) so he can stream the RTSP feed to Shinobi. Chris is currently having issues that Shinobi does not support motion detection and requires a plugin but currently is broken on ARM. With 3 ca

a feeds it maxes out all the cores on the Pi 4. Chris is running his RSTP feeds via home assistant for a temporary solution.

Alex mentions [statping](https://hub.docker.com/r/hunterlong/statping) and how he broke the container and how he uses [docker-compose](https://docs.docker.com/compose/) to manage his containers. He used the following to update his containers.
```
docker-compose pull
docker-compose up
```
Alex was using his [slate openwrt travel router](https://openwrt.org/toh/gl.inet/gl-ar750s) with [wireguard](https://www.wireguard.com/) in a hotel room to connect to his DO droplet to update his dockers containers. While updating the containers it broke statping. Looking at the [logs](https://docs.docker.com/compose/reference/logs/) it showed him that he was running the wrong version of progressSQL. He added a tag to docker-compose.yml file not to pull the latest version of progressSQL. Within 8 sec of doing 'docker-compose up' statping was up and working again,

Chris talked about how his current storage setup is failing him. He is currently using multi disks connected to Pi 4 via USB3 which randomly disconnecting compared to SATA. Chris mentioned [Samsung SSD 970 Evo Plus rugged 1TB drive](www.need.link) he has been using. Alex mentioned [linus tech video about a 3.8TB SSD](www.need.link) and he also mentioned [his blog on his workflow on his photograph.](https://blog.ktz.me/my-photography-workflow/)

Chris talked about buying a 4th Raspberry Pi or should he have one Raspberry Pi with multiple hard drives hanging off it but using a SD card or small SSD for the root partition. Chris asked Alex for advice on [mergerFS](https://github.com/trapexit/mergerfs).They recorded a [Jupiter Extras episode](https://extras.show/28) with the creator of mergerfs. Alex mentioned his episode of [Brunch with Brent: Meet Alex from Self Hosted](https://extras.show/7) how he got into the whole self hosting his data and also mentioned his [blog on The Perfect Media Server - 2019 Edition](https://blog.linuxserver.io/2019/07/16/perfect-media-server-2019/)

Alex mentioned that you get better Plex performance by putting your Plex metadata on an SSD rather than a spinning disk to get better performance. Chris mentioned that he uses spinning disks for his work flow - he using 10k rpm disks in a RAID0. RAID0 means data in striped across disk in the array which gives an increase in performance. But if any of the disk fail in the array all data will be lost. Chris  named this volume "scary RAID"
 
Alex mentioned a [2016 guide on buy hard drive](www.need.link). Alex also mention a hidden cost of running ZFS at home. Alex mentions that he was buying single drive either monthly or every 6 months, which does not really fit with the ZFS model where you need to work out what capacity and drives needed to run ZFS,If you need to upgrade your ZFS pool you need to buy multi disks. Since moving to America, Alex has found out about best buy and can buy 10tb WD in a case, but are easy to remove. Alex mentioned about a [mod of 3.3v rail in the sata spec](www.need.link) to reset hard drive without being present.

Alex describes what mergesfs is that you can use any size of disk or any type of disk sata, usb3 and combine them with only a single mount point. mergerfs is does  pairty device it 22:40. It is a fused mount point so that all devices are found under one place. If you want parity meaning if you want to recovery from a drive failure you need to use snapraid. They Discusses [unraid](https://unraid.net/) and [open media vault](https://www.openmediavault.org/).

Alex and Chris recap on what you need to think about when you are considering a storage solution, how fast the disks need to be, how much storage you need, the usage/ IO requirement, future expansion, redundancy and your budget. Chris mentioned since going audio-only his requirement has dropped dramatically.

Chris compares ZFS and MergesFS.That you Can pull the disk using MergesFS from one computer to other computer and can see the data on another system as it uses normal underlaying linux file syster . Alex configures  mergerfs in one line in his FS tab file:

```
FSTAB FILe???
```

Alex mention that with snapraid the parity disk needs to be as big or larger then the biggest data drive.snapraid can support up to six parity drive. Chris is wondering if that if there is a Sata hat on the raspberry pi. Alex recommends running a small i5-i386 to do this solution. But Chris like the idea of raspberry pi as they are cheap and easily replaced and they run off DC for his RV. 

Alex mentions that Snapraid does checksumming at file level every time is calculating parity but not block level like ZFS. With snap raid scrub it check the checksum and file. ZFS provides comparison, encryption and for backup zfs send and recive. Chris mention that he take his Freenas off the storage server at the studio as Chris is not the right person for the Freenas, as everything is done through the gui and he is not familiar with freebsd if there if there is a problem. Once he has flip over the server to linux he has used at 100% more. Alex mention that he look at rysnc to transfer the data offsite to protect against deletion or cyrptolocking, they also mention [Duplicati](www.duplicati.com) for crating offsite encrypted backups.

Alex mention the [Brunch with Brent: Allan Jude](https://extras.show/22) podcast
