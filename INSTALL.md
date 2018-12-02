# P4wnP1 安装指南
以下教程在 Zero W 测试通过，Zero 并不完全适用。
## 第一步 - 安装 Raspbian Lite
 1.  下载镜像：[官网镜像下载](https://www.raspberrypi.org/downloads/raspbian/)
 2.  按照官方教程写入即可，然后在 boot 分区创建一个名为“ssh”的空白文件以开启 ssh 。

## 第二步 - 使 Raspberry Pi 连接到互联网

有几种方法可以做到：

 - 将 Android 连接到互联网后，通过 OTG 转接线连接到 Zero（W）的 USB 口，开启 Android 设备的“USB 网络共享”即可。
 - 将已写入系统的 SD 卡插入带有网络接口的 Raspberry Pi 启动进行配置，如RPi 3B，配置完成后再插入 Zero（W）使用。
 - 在已启动的 Linux 系统挂载 SD 卡的 rootfs 分区，编写连接 wifi 的配置文件后启动。（仅适用于 Zero W，未测试）
 - 启用 Zero（W）的 USB 以太网适配器模式，然后连接到 Windows 或 Linux 系统。（此方法会对更新软件包有影响，不推荐）
 - 将 SD 卡挂载到已启动的 Linux 系统，chroot 到 SD 卡的系统进行配置。（高级选项，影响未知，跨架构请参考[这个](https://www.zhihu.com/question/52228403/answer/273781342))

使 Raspberry Pi 连接到互联网后，你可以根据连接的方式，选择适当的方法连接到 Raspberry Pi 的 ssh ，并使用官方提供的用户名和密码登录。

## 安装 P4wnP1

按顺序输入以下命令以 P4wnP1:

    sudo apt update
    sudo apt -y install git
    cd /home/pi
    git clone --recursive https://github.com/mame82/P4wnP1
    cd P4wnP1
    ./install.sh

因为该存储库引用了其他存储库的文件，所以使用 git 克隆文件需要 `--recursive` 选项。

可使用 [原项目](https://github.com/mame82/P4wnP1) 或 [本fork项目](https://github.com/Moe-New/P4wnP1)。

执行 `./install.sh` 后将会开始安装，安装设置过程需要一些时间，请耐心等待，如果安装成功或者遇到错误，信息将会显示。

## 运行 P4wnP1

如果没有错误，你可以关闭 Raspberry Pi 并使用 USB数据线将 Zero（W）的 USB 口连接到 PC。
默认启用的 payload 是 network_only ，该模式启用了 Zero（W）的 USB 以太网适配器模式，可在 Windows 或 Linux 下连接以进行下一步配置。

