# HOKUYO UST-10LX 配置说明

## 1. 安装 urg_node ROS功能包

```shell
$ sudo apt install ros-melodic-urg-node
```

## 2. 修改 IP 地址

- 在有线网络设置中用手动模式修改 ip 为192.168.0.xx

- ```shell
  $ ping 192.168.0.10
  ```

## 3. 启动激光节点

```shell
$ roscore
$ rosrun urg_node urg_node _ip_address:=192.168.0.10
```

## 4. 查看激光数据

在 rviz 中添加 topic /scan 下的 LaserScan，修改 Frame 为 laser 即可看到激光雷达实时得到的图像

## 5. Cartographer 建图

在 cartographer_ros 包的 launch 和 configuration_files 中分别加入自定义 launch 和 参数配置文件 demo_hokuyo.launch 和 hokuyo.lua （Download from <https://github.com/ppppplus/HOKUYO-SLAM/tree/main/src>），先按照 3 启动激光节点，再运行

```shell
$ roslaunch cartographer_ros demo_hokuyo.launch
```

## 6. 其他

额定功率为 12V / 0.25A，官方文档可见<https://github.com/ppppplus/HOKUYO-SLAM/tree/main/doc>

