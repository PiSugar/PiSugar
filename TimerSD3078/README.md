

# 芯片简介
SD3078是一个自带晶振的时钟芯片，同常见的DS1302比较，内部晶振稳定性更高，不需要外部参数调节。
SD3078的时间寄存器同DS1307相同，树莓派自带驱动，不需要再编译驱动内核。

# 操作顺序

## 打开写保护
sudo i2cset -y 1 0x32 0x10 0xff
sudo i2cset -y 1 0x32 0x0f 0x85

## 写入系统文件
echo ds1307 0x32 | sudo tee  /sys/class/i2c-adapter/i2c-1/new_device

## 写入时钟数据
sudo hwclock -w
