# MAC 地址以及 Monitor 模式

# MAC 地址以及修改方式

## MAC 地址

- Media Access Control 媒体访问控制
  - 永久的
  - 唯一的
  - 物理地址
- 设备制造商分配的

查看 MAC 地址

```bash
ifconfig
```

## 为什么修改 MAC 地址？

1. 可以在网络中匿名
2. 模仿其他设备
3. 绕过过滤器

## 修改 MAC 地址（修改的是内存中的 MAC 地址，而不是修改实际的 MAC 地址，重启后回复原 MAC 地址）

1. 禁用接口

```bash
ifconfig wla0 down
```

2. 修改 MAC 地址（原 MAC 地址：e2:ec:69:f8:5e:4a）前两位须保持一致

```bash
ifconfig wlan0 hw ether e2:11:11:11:11:11
```

3. 启用接口

```bash
ifconfig wlan0 up
```

# 将无线网卡从 managed 模式切换到 monitor 模式

1. 禁用接口

```bash
ifconfig wlan0 down
```

2. 检查是否有其他进程正在使用无线网络接口，并尝试终止这些进程。（确保无线网卡能够正确地切换到监视模式，以便进行网络安全测试。）注意，你需要具有管理员权限才能运行此命令。

```bash
airmon-ng check kill
```

3. 修改为 monitor 模式（如果报错，则跳过第二步）

```bash
iwconfig wlan0 mode monitor
```

4. 启用接口

```bash
ifconfig wlan0 up
```

5. 查看接口状态

```bash
iwconfig
```
