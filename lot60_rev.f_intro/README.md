### 刷机改配列
蓝牙固件有三个:

```
rev_f-nrf52-2019_12_02-db6e8ae.zip 原厂固件
nrf52_clean_rev.f.zip 重置固件
rev_f-nrf52-2019_12_26-b1be777-dirty.zip 刷配列固件
```
原厂固件刷配列有bug,刷配列固件连接 macbook 蓝牙有 bug,所以改配列(必然需要一台 windows 机)按照如下顺序操作:

0. 拔电池, 使用 usb 线供电
1. 进入 DFU, iPhone 使用 nRF Connect 刷 nrf52_clean_rev.f.zip
2. 拔 usb 线, 再次进入 DFU, 刷 rev_f-nrf52-2019_12_26-b1be777-dirty.zip
3. 使用 KeymapDownloader_1.0.3.exe 刷入配列(刷配列键盘不需要进入任何模式,直接插线就完事)
4. 刷回 rev_f-nrf52-2019_12_02-db6e8ae.zip; 刚刚刷入的配列将会被保留

### 如何进入 DFU

1. 拔电池, usb 线连接电脑,
2. 将键盘翻到背面，找到 GPIO0 接口。使用镊子将 GPIO0 接口与 GND 接口连接。
3. 按下 RESET 按钮使键盘强制重启
4. 蓝牙会搜索到一个名为DFUTarg的设备，表明已经进入 DFU 模式了。进入 DFU 模式后即可断开 GPIO0 和 GND 的连接。

### Mac 蓝牙列表里扫描不到键盘

sudo rm /Library/Preferences/com.apple.Bluetooth.plist, 重启

### Command键没反应,或者其他按键不对

请将键盘关机。重新开机时，按下Space+BackSpace重置 EEPROM 的设定。

### 蓝牙连接问题

1. 手动休眠键盘
2. 在开机时按下Space+E即可删除绑定。（即在休眠后，按下 Space+U+E 开机）