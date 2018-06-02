

# 芯片简介
SD3078是一个自带晶振的时钟芯片，同常见的DS1302比较，内部晶振稳定性更高，不需要外部参数调节。
SD3078的时间寄存器同DS1307相同，树莓派自带驱动，不需要再编译驱动内核。

# 操作顺序

* ##  树莓派设置中打开I2C通讯
* ##  系统内核添加驱动模块
* ##  使用I2Ctools寻找地址
SD3078固定地址0X32
* ##  打开写保护
> sudo i2cset -y 1 0x32 0x10 0xff
> sudo i2cset -y 1 0x32 0x0f 0x85

* ##  向系统添加新设备
> echo ds1307 0x32 | sudo tee  /sys/class/i2c-adapter/i2c-1/new_device
* ##  检查设备是否已经占用
* ##  写入时钟数据
> sudo hwclock -w
