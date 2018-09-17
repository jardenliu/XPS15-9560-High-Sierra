# XPS15-9560-High-Sierra
> XPS15 9560 吃苹果Clover
/Users/jarden/hackintosh/XPS15-9560-High-Sierra/Post-install/kexts/
本项目同步到码云仓库，方便访问github速度慢的朋友们
[https://gitee.com/yeliujun/XPS15-9560-High-Sierra](https://gitee.com/yeliujun/XPS15-9560-High-Sierra)

## 更新日志

#### 2018-09-18 （10.13最后一次更新配置）
1. 升级Clover到4671, 当前配置兼容10.14(Mojave)，可以无痛升级
1. 更换触摸板和触屏驱动为`VoodooI2C`, 更接近白果体验，详见第五步。👇
2. 更换新显卡驱动`WhateverGreen`.
3. 加入了风扇传感器，虽然毫无卵用

- [jardenliu/XPS15-9560-Mojave](https://github.com/jardenliu/XPS15-9560-Mojave)即将到来

#### 2018-07-11 （重要问题修复）
1. 修复了一个长期以来忽略的`睡眠唤醒无声`问题（主要是我自己用的配置和这个还是有点区别的，哈哈哈！！！）
2. 如果不想覆盖你的现在用的配置，这里提供一个教程 [猛戳这里](https://github.com/jardenliu/XPS15-9560-High-Sierra/blob/master/%E5%94%A4%E9%86%92%E6%97%A0%E5%A3%B0%E4%BF%AE%E5%A4%8D%E6%95%99%E7%A8%8B.md)。

#### 2018-07-10(适配10.13.6)
1. 升级Clover到4595
2. 用ApfsDriverLoader-64.efi替换了apfs.efi

#### 2018-06-05
1. 添加了wifi、显卡、USB控制器等设备的信息。
2. 给HD630打了补丁，从1536M->2048M
3. 解锁了博通wifi全频段信号

#### 2018-05-26
1. 修正DW1830蓝牙唤醒不可用的问题，使用方法，用Post-install/DW1830BT的`SSDT-UIAC.aml`替换CLOVER/ACPI/patched的。

#### 2018-05-23 
1. 升级Clover版本到4494，兼容新旧版的Clover Configurator（主要是新旧版的Fix header位置发生变化）。

#### 2018-04-30 
1. CPU变频优化，将最低频率`1.3GHz`降到`0.8GHz`，添加`CPUFriendDataProvider.kext`，此kext只适用于`SMBIOS:Macbook Pro14,3`。
2. 添加`ALC298PluginFix`，耳机插拔状态切换方案二。

#### 2018-04-27 (适配10.13.4 安全更新版本)
1. 更新了自用的主题(Universe)
2. 使用kextsToPatch对AppleGraphicsDevicePolicy进行patch，替代`NvidiaGraphicsFixup`，修正HDMI输出黑屏的问题

---
 
## 本机配置
- CPU：Intel I7 7700HQ
- 内存：16G(8G*2) 2400MHz DDR4
- 硬盘：东芝 NVMe 512G
- WIFI网卡：已更换为博通DW1830
- 屏幕分辨率：4K触控屏(Mac os下面可以单点触控)
* (1080p的同学可以移除CoreDisplayFixup.kext)


## 使用情况
- 除了下面问题以外，其他全部都能用！

 *已知问题*
- 雷电3接口不支持热插拔。
- 读卡器无法使用
- 独显无法使用
- 触摸板在三指上下左右滑时，偶尔误触

## 安装提示
安装或更新系统之前可以下载我提供kext，确保kext的驱动是最新的，避免驱动不支持最新版本。

---
**安装篇**
## 第一步：安装

## 全新安装(大概流程)

1. 制作启动U盘和启动，上远景搜吧，一堆教程。 (系统镜像请自己找，随便找一个懒人包也行。使用懒人包的请把我提供的Clover覆盖懒人包里面的)。
2. 镜像推荐到[黑果小兵的博客](https://blog.daliansky.net/) ，找最新版本下载。配置没有测试过旧版本，所以推荐使用最新版本。
3. 安装MacOS
4. 把Clover安装到硬盘EFI中(详细教程自己找，黑果小兵的博客也有写)

> 注意事项
- CLOVER推荐使用最新版本。
- 安装在SSD中最好使用APFS。若安装在HDD中请不要使用(非常非常慢)，HDD硬盘推荐使用HFS+。
- `特别注意!!!`,进入系统后别急急忙忙登陆你尊贵的AppleID(请看第3步)
- APFS需要UEFI驱动支持，请把CLOVER/drivers64UEFI/apfs.efi添加到你的Clover中。


# 第二步：安装kext
> RehabMan建议将部分注入的kext放入到/S/L/E中，已获得更接近白苹果的启动方式。

## 以下方法二选一

### 1.安装kext到Clover

1. 把`Post-install/Other-kexts`文件夹里面的全部kext复制到`EFI/clover/kexts/Other`中


### 2.安装kext到SLE(推荐)(安装系统完成后)

> 强烈推荐使用`Kext Utility`以免去各种麻烦

1. 打开`Kext Utility`把`Post-install/SLE-kexts`文件夹里面的全部kext扔进软件里等待完成
2. 先重启机子以防出问题再接着第三步


# 第三步：登陆你的AppleID(不用白果三码)

警告：不完成该步骤，登录AppleID将会面临封号的风险

使用白果三码注意机子型号要匹配！否则我也不知道官方会对你的账号做什么 =w=

> 请保证目前你的电脑没有登陆过AppleID，关于如何重设AppleID请看[这里](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/)

### 蒂花之秀同学，开始你的操作

工具：`Clover Configurator`
1. 打开config.plist
2. SMBIOS栏 在Serial Number隔壁有个Generate New小按钮，按下去随机生成Serial Number(不断按到你乐意停下来为止)
3. Systeam Parameters栏 Custom UUID下也有一个Generate New小按钮，重复
4. Rt Variables栏 ROM下面也有一个Generate New小按钮，重复
5. 保存重启
6. 重启后，就可以登录你的Apple Id了.

# 第四步：解决二合一耳机接口

## 以下方法二选一

方案一：
1. 解压`Post-install/ComboJack Installer.zip` (感谢[KNNSpeed](https://www.tonymacx86.com/threads/guide-dell-xps-15-9560-4k-touch-1tb-ssd-32gb-ram-100-adobergb.224486/page-9#post-1539760)提供的补丁)
2. 使用终端cd到ComboJack Installer文件夹
3. 执行命令`./install.sh`(提示需要输入密码)
4. 重启

### 使用提示
- 插入耳机后弹出提示窗口(根据提示选择你插入的设备类型即可)
- 睡眠唤醒后请把耳机拔出再插进去重新选择类型使其正常工作
- 虽然耳机能用了，不要对耳机音质抱有任何希望！买个DAC才是正解！

方案二：
1. 双击安装`Post-install/ALC298PluginFix/install双击自动安装.command`，安装ALCPluginFix守护进程。

# ~~第五步：设置触控板手势（过时的）~~
1.  ~~`系统偏好设置`-`键盘`-`快捷键`-`启动台与程序船坞`,设置`显示启动台`快捷键，设置时，四指下滑。~~
2. ~~`系统偏好设置`-`键盘`-`快捷键`-`调度中心`,设置`显示通知中心`快捷键，设置时，双指从触摸板右边缘往左滑。~~

### 手势说明
- ~~双指左边缘往右滑，最小化当前窗口~~
- ~~双指上边缘往下滑，最大化当前窗口~~
- ~~双指右边缘往左滑，显示通知中心~~
- ~~三指上下左右滑，分别对应 `调度中心`, `应用程序窗口`, `向右移动一个空间`, `向左移动一个空间`。（偶尔误触）~~
- ~~四指上下左右滑，分别对应 `显示桌面`, `显示启动台`, `后退`, `前进`~~
- ~~（个人使用的手势，可以根据个人喜好自行设置）~~


# 第五步：VoodooI2C手势（原生体验 VoodooI2C)
- 安装完成后，设置`系统偏好设置`-`触摸板`-`光标与点按`，勾选`轻点来点按`

### 手势说明
- 与白果接近
- 缺点是会`误触`


# 问题解答
## 一、系统小版本更新
1. 更新前请删掉你的`EFI/clover/kexts/Other`中所有kext(注意备份)，然后把我提供的`CLOVER/kexts/Other`里的kext复制进去，在更新完毕后即可还原回去。
2. 请使用`Kext Utility`修复权限并建立缓存(针对kext安装在SLE)
> 可用命令`sudo kextcache -i /`替代

> kext安装在SLE或Clover里都必须要这样做，防止启动时驱动引发错误而造成的更新文件损坏

## 二、关于WIFI网卡问题
   1. 大多数9560配的是killer网卡，驱动无解！可以使用usb网卡或者直接换一个免驱的（推荐DW1830）
   2. 若使用DW1830，你可以尝试加天线来增强2.4Ghz WIFI的稳定性，装好系统之后，在`偏好设置`-`节能`-`电源适配器`中取消勾选`唤醒以供WI-FI网络访问`和`电能小憩`，避免唤醒后网速巨慢无比的问题。



---
# 特别感谢
- [@RehabMan](https://github.com/RehabMan)、[tgmac](https://www.tonymacx86.com/members/tgmac.928166/)提供的教程和有关文件
- [blazinsmokey](https://www.tonymacx86.com/members/blazinsmokey.1188623/)解决了wifi睡眠后无法使用的问题
- [gunslinger23](https://github.com/gunslinger23)提供了自己研究和配置的成果。
