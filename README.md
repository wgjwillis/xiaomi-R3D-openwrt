## 支持说明

固件支持小米R3D R3G等。



## 注意事项

root密码为空

WiFi SSID 为 OpenWrt，双频合一；密码为空

路由器地址：192.168.15.1

添加了passwall等

alpinefancontrol 为R3D专用风扇控制。其他路由器建议 编辑feeds.conf.default文件屏蔽 src-git alpinefancontrol https://github.com/openwrt-xiaomi/openwrt-alpine-fan-control.git 这行。

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

## 问题及处理方法

1，报错：Hash of the local file jq-1.6.tar.gz does not match (file: 5de8c8e29aaa3fb9cc6b47bb27299f271354ebb72514e3accadc7d38b5bbaa72, requested: 9625784cf2e4fd9842f1d407681ce4878b5b0dcddbcd31c6135114a30c71e6a8)
```
sed -ri 's#9625784cf2e4fd9842f1d407681ce4878b5b0dcddbcd31c6135114a30c71e6a8#5de8c8e29aaa3fb9cc6b47bb27299f271354ebb72514e3accadc7d38b5bbaa72#' ./feeds/packages/utils/jq/Makefile
```

## 墙内设置
1，git代理
```
git config --global http.proxy 'http://127.0.0.1:1080'
git config --global https.proxy 'http://127.0.0.1:1080'
```
设置完之后可以使用这个命令查看 Git 的配置。
```
git config --list
```
取消git代理
```
git config --global --unset http.proxy
git config --global --unset https.proxy
```

2，GO代理
```
export GOPROXY=https://proxy.golang.com.cn,direct
```
## WSL设置
```
source /etc/environment
```

## 其他修改
1，修改主机名、时区、NTP服务器等。。。
```
vi package/base-files/files/bin下的config_generate
```


