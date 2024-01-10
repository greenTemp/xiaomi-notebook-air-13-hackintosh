# xiaomi notebook air 13.3 hackintosh

## 说明

EFI文件由[这个项目](https://github.com/johnnynunez/Xiaomi-Mi-Air)修改而来，主要解决了原版EFI连接wifi时电脑自动重启的问题，在此对原版EFI文件的作者表示感谢

支持的macOS版本：macOS 12.00 Monterey

其他macOS版本未做测试

---

## 适用设备

本引导程序适用于2017款小米笔记本notebook air 13.3，配置如下

* CPU：i5-7200U
* 内存：8G
* 硬盘：256G
* 显卡：hd620核显 + MX150独立显卡
* 屏幕分辨率：1920*1080
* 无线网卡：ac8265 with 蓝牙4.1

目前仅对以上设备的原厂配件版本兼容，其他设备和配件使用情况未做测试

---

## 功能情况

可以正常使用的功能请看[这里](https://github.com/johnnynunez/Xiaomi-Mi-Air#what-is-working)

除了上面写到的功能，自测wifi和蓝牙也可以正常使用，使用wifi不需要安装HeliPort，随航和隔空投送功能没做测试

无法正常使用的功能请看[这里](https://github.com/johnnynunez/Xiaomi-Mi-Air#not-working)

目前已知问题：触摸板在使用手势时，偶尔会失灵，如果出现失灵的情况，按下command+tab键切换窗口之后，触摸板即可恢复正常使用

## 使用方式

1. 下载系统镜像，制作系统安装u盘

    不建议使用gibMacOS来制作系统安装u盘，也可能是我不会用，我使用gibMacOS就从来没制作成功过

    建议使用[OpenCore官方的方法](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#creating-the-usb)制作安装u盘

    注意：OpenCore官方下载镜像的命令有误，需要使用*python*命令，而不能用*python3*

    把下载好的镜像放入u盘后，需要[下载](https://github.com/greenTemp/xiaomi-notebook-air-13-hackintosh/archive/refs/heads/main.zip)本项目里的EFI文件，放入u盘根目录

3. 更新config.plist文件里的设备信息

    可以参考[司波图的视频](https://www.youtube.com/watch?v=EN0pD_6pf8o&t=677s)进行操作

4. 使用制作好的系统安装u盘安装系统

    安装系统之前需要首先设置bios，具体方式可以参考[国光的黑苹果教程](https://apple.sqlsec.com/5-%E5%AE%9E%E6%88%98%E6%BC%94%E7%A4%BA/5-2.html#2-bios-%E8%AE%BE%E7%BD%AE)

    然后按照[司波图的视频](https://youtu.be/EN0pD_6pf8o?t=1009)安装系统

5. 把引导文件拷贝到硬盘上，以实现脱离u盘引导系统

    先打开`终端`，然后输入以下命令挂载引导分区

    ```
    sudo diskutil mount /dev/disk0s1
    ```

    然后删除分区里的EFI文件夹，把u盘里的EFI文件夹复制到引导分区，完成从硬盘引导系统

    至此系统安装完成，enjoy
