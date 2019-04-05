
一、UUID


二、重启网卡异常1
```
Bringing up interface eth0:  Determining if ip address 192.168.88.168 is already in use for device eth0...
                                                           [ OK ]
该警告一般是由于网卡解析arp协议导致的，可在网卡的配置文件中加入ARPCHECK=NO参数来屏蔽该检查
```
