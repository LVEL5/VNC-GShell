## 𝗖𝗟𝗢𝗨𝗗𝗦𝗛𝗘𝗟𝗟  𝗩𝗡𝗖  𝗘𝗫𝗣𝗟𝗢𝗜𝗧
![LOGO][1]
#### 𝗔𝗕𝗢𝗨𝗧 𝗣𝗥𝗢𝗝𝗘𝗖𝗧
`docker-ubuntu-vnc-desktop` is a Docker image to provide web VNC interface to access Ubuntu LXDE/LxQT desktop environment.

![DESKTOP][2]


# ![UBUNTU LOGO][3] 𝗙𝗟𝗔𝗩𝗢𝗥𝗦
***Choose your favorite Ubuntu version with tags***

 - focal: Ubuntu 20.04 (latest)
 - focal-lxqt: Ubuntu 20.04 LXQt
 - bionic: Ubuntu 18.04
 - bionic-lxqt: Ubuntu 18.04 LXQt
 - xenial: Ubuntu 16.04 (deprecated)
 - trusty: Ubuntu 14.04 (deprecated)


## 𝗚𝗘𝗧 𝗦𝗧𝗔𝗥𝗧𝗘𝗗

##### Open Google [**Cloudshell**](https://shell.cloud.google.com/?show=ide,terminal&authuser=1&fromcloudshell=true)

![GSHELL][4]

### 𝗥𝗨𝗡 𝗖𝗢𝗠𝗠𝗔𝗡𝗗𝗦 𝗕𝗘𝗟𝗢𝗪

    docker run -p 6070:80 dorowu/ubuntu-desktop-lxde-vnc

#### 𝗖𝗛𝗔𝗡𝗚𝗘 𝗣𝗢𝗥𝗧
#### 𝗣𝗢𝗥𝗧 : `6070`
![Port Setting](https://i.ibb.co/k0sTNcY/Screenshot-2023-12-23-5-37-51-AM.png)  ![Change Port](https://i.ibb.co/vQNHtbh/Screenshot-2023-12-23-5-39-19-AM.png) 

#### 𝗗𝗢𝗖𝗞𝗘𝗥 𝗖𝗢𝗠𝗠𝗔𝗡𝗗𝗦

    docker run -d -t --name [hub name] [new name]
    docker exec -it [new name] [exp: sh]

#### 𝗦𝗬𝗦𝗧𝗘𝗠 𝗨𝗣𝗗𝗔𝗧𝗘 & 𝗜𝗡𝗦𝗧𝗔𝗟𝗟 𝗧𝗢𝗢𝗟𝗦

    sudo su
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 6494C6D6997C215E
    apt-get update -y
    apt-get upgrade -y

#### 𝗜𝗡𝗦𝗧𝗔𝗟𝗟 𝗨𝗕𝗨𝗡𝗧𝗨 𝗣𝗥𝗢𝗗𝗨𝗖𝗧𝗜𝗩𝗜𝗧𝗬 𝗦𝗢𝗙𝗧𝗪𝗔𝗥𝗘
    apt install ubuntu-gnome-desktop
#### 𝗗𝗢 𝗨𝗕𝗨𝗡𝗧𝗨 𝗥𝗘𝗟𝗘𝗔𝗦𝗘 𝗨𝗣𝗚𝗥𝗔𝗗𝗘 | optional
    do-release-upgrade

#### 𝗨𝗕𝗨𝗡𝗧𝗨 𝗦𝗢𝗙𝗧𝗪𝗔𝗥𝗘 𝗖𝗘𝗡𝗧𝗘𝗥
    apt install gnome-software



----------


#### 🔊 𝗦𝗢𝗨𝗡𝗗 ᴘ️ʀᴇᴠɪᴇᴡ ᴠᴇʀꜱɪᴏɴ ᴀɴᴅ ʟɪɴᴜx ᴏɴʟʏ 
> It only works in Linux.
First of all, insert kernel module snd-aloop and specify 2 as the index of sound loop device

    sudo modprobe snd-aloop index=2
Start the container

    docker run -it --rm -p 6080:80 --device /dev/snd -e ALSADEV=hw:2,0 dorowu/ubuntu-desktop-lxde-vnc

where `--device /dev/snd -e ALSADEV=hw:2,0` means to grant sound device to container and set basic ASLA config to use card 2.

Launch a browser with URL http://127.0.0.1:6080/#/?video, where video means to start with video mode. Now you can start Chromium in start menu (Internet -> Chromium Web Browser Sound) and try to play some video.

Following is the screen capture of these operations. Turn on your sound at the end of video!

![YouTube][5]


----------



## 𝗪𝗔𝗥𝗡𝗜𝗡𝗚: 𝗗𝗲𝗽𝗿𝗲𝗰𝗮𝘁𝗲𝗱

Dockerfile and configuration can be generated by template.

- arch: one of `amd64` or `armhf`
- flavor: refer to file in `flavor/flavor.yml`
- image: base image
- desktop: desktop environment which is set in flavor
- `addon_package`: Debian package to be installed which is set in flavor

Dockerfile and configuration are re-generate if they do not exist. Or you may force to re-generate by removing them with the command make clean.


### ⓘ 𝗧𝗿𝗼𝘂𝗯𝗹𝗲𝘀𝗵𝗼𝗼𝘁𝗶𝗻𝗴 𝗮𝗻𝗱 𝗙𝗔𝗤
1. boot2docker connection issue 👉 [HERE](https://github.com/fcwu/docker-ubuntu-vnc-desktop/issues/2)
2. Multi-language supports 👉 [HERE](https://github.com/fcwu/docker-ubuntu-vnc-desktop/issues/80)
3. Autostart 👉 [HERE](https://github.com/fcwu/docker-ubuntu-vnc-desktop/issues/85#issuecomment-466778407)
4. x11vnc arguments (multiptr) 👉 [HERE](https://github.com/fcwu/docker-ubuntu-vnc-desktop/issues/101)
5. firefox/chrome crash `/dev/shm` 👉 [HERE](https://github.com/fcwu/docker-ubuntu-vnc-desktop/issues/112)
6. resize display size without destroying container 👉 [HERE](https://github.com/fcwu/docker-ubuntu-vnc-desktop/issues/115#issuecomment-52242603) 


----------

![LINUX][6]

#### </> 𝗦𝗢𝗨𝗥𝗖𝗘 CODE
| Website | Link | 
| -------- | -------- |
|𝗗𝗼𝗰𝗸𝗲𝗿|https://hub.docker.com/r/dorowu/ubuntu-desktop-lxde-vnc|
|𝗚𝗶𝘁𝗵𝘂𝗯|https://github.com/fcwu/docker-ubuntu-vnc-desktop|


# 𝗟𝗣-𝟬𝟮



  [1]: https://i.ibb.co/tK0h6mg/image.png
  [2]: https://i.ibb.co/2q0C1qN/Screenshot-2023-12-23-5-48-21-AM.png
  [3]: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSr7x7rR8pCp-BAuUFCvyHzUhEI7usAW0iKwCiLe_s6I5lUEDe-n-pOl9XtFFlowcWRMQ&usqp=CAU
  [4]: https://i.ibb.co/ySBTs48/Screenshot-2023-12-23-5-24-23-AM.jpg
  [5]: http://img.youtube.com/vi/Kv9FGClP1-k/0.jpg
  [6]: https://i.ibb.co/mNzXrm7/image.png
