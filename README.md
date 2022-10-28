## 注意事项

root密码为空
WiFi SSID 为 R3D-WiFi；密码为空
路由器地址：192.168.15.1

添加了passwall等


## 安装依存

```
sudo apt-get install git git-core curl rsync
sudo apt-get install build-essential gawk gcc-multilib flex git gettext libncurses5-dev libssl-dev
sudo apt-get install python3-distutils rsync unzip zlib1g-dev
```

## 编译固件

```
git clone https://github.com/wgjwillis/xiaomi-R3D-openwrt.git openwrt
cd openwrt

./scripts/feeds update -a && ./scripts/feeds install -a

选择自己需要的路由器，以及包。
make menuconfig

下载源码。
make download V=s -j1
开始编译。
make V=s -j1

```
