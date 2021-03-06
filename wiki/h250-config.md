
##CC3D配置向导
作为一个之前对CC3D没有接触的新手，我们应该怎样快速入门CC3D让H250飞起来呢？OpenPilot CC3D拥有一个非常详尽的上位机，下面提供了百度云和官网下载的链接，读者可自行下载，14.01版本界面语言为English，当然地面站有汉化版，下面以版本为14.01为例介绍CC3D向导配置过程。

<a href="http://pan.baidu.com/s/1o6so6Ki" class="btn btn-lg btn-outline" role="button" target="_blank" >CC3D上位机（百度云）</a>
<a href="https://wiki.openpilot.org/display/WIKI/OpenPilot+Downloads" class="btn btn-lg btn-outline" role="button" target="_blank" >CC3D上位机（CC3D官网）</a>

##地面站的安装
点击CC3D上位机安装程序OpenPilot-RELEASE-14.01-win32.exe，默认安装，一路next即可。安装最后窗口弹出提示安装驱动，点击确认安装即可。安装驱动程序之后用数据线将CC3D与电脑连接，有可能你的电脑会提示该驱动安装未成功，在设备管理器里COM端口有出现但是Copter Control黄色感叹号标识，如下图所示。这个时候，其实上位机和CC3D飞控已经可以正常通信。

![](/assets/img/cc3d-driver.png)

##CC3D向导配置
进入地面站，首先查看端口通信是否连接，点击Vehicle Setup Wizard进入向导配置界面如图所示。

> CC3D飞控使用mini USB接口和上位机相连。

![](/assets/img/cc3d-1.png)

进入设置向导后，会出现红色标识，上位机非常人性的提示在配置之前卸掉桨叶，以防意外发生。next进入下一界面，固件升级界面，提示你需要将固件版本与地面站版本保持一致，初次配置，建议Upgrade升级固件。升级固件步骤：

* 断开航模电池，拔掉USB线，保证CC3D飞控已经完全断电，没有LED亮起
* 点击Upgrade按钮
* 根据进度条上的提示，待进度条走动时迅速插上USB数据线，地面站将自动写入最新固件。

![](/assets/img/h250-config-3.png)

飞控写入最新固件后，next进入遥控接收器的配置，有PWM/PPM/Futaba/Spektrum四种可选。我们使用的是FS-T6遥控套件，选择PWM通信方式。至于这4中遥控接收器的特点和区别，可以参考todo。

![](/assets/img/h250-config-4.png)

next下一步将会提示选择飞机的类型，有Multirotor、直升机、固定翼及车类选项，目前14.01版本只支持Multirotor和固定翼，选择Multirotor。

![](/assets/img/h250-config-5.png)

下一步将要选择多轴飞行器的机型，Multirotor type下拉框有三轴、四轴、六轴及各种飞行模式可选，右边窗口将会有示意图示意所选择的类型及各个电机转动的方向。选择四轴飞行器，X模式，即Quadcopter X。

![](/assets/img/h250-config-6.png)

next下一项进入电调的选择界面，有高速电调和标准电调两项可选，选择对应电调同时还要告知工作信号的类型，H250选择高速电调；

![](/assets/img/h250-config-7.png)

上位机将会把刚刚所配置的信息显示，确认next，进入传感器校准程序界面。在进入传感器校准之前，需要将飞控板保持水平状态，避免误差。

![](/assets/img/h250-config-8.png)

**硬件配置总结:关于配置这块，如果担心记不清楚选项或者初次接触不知如何入设置，我们就按默认选项即可，CC3D的默认选项与H250完全一致。**

## 电机输出校准

校准传感器Next进入电机输出校准界面。在这里提醒大家卸掉桨叶接通电源！输出校准是设置电机的中性环境。方法是点击Start，鼠标拖动滑块向右移动直到电机转动，然后点击Stop，待电机完全停下，点击开始，观察点击能否自己启动，左右移动滑块调节电机启动的临界点。这里需要注意电机的位置及电机的旋转方向，若电机位置不一致，匹配飞控输出通道与电机所对应电调；若旋转方向不一致，只需将电机的任意两根线互换即可。

![](/assets/img/h250-config-9.png)

电机2、3、4的输出校准同电机1一样，按照电机1的设置步骤即可。四个电机参数设定之后，next进入参数写入界面，点击save。

![](/assets/img/h250-config-10.png)

## 遥控器配置

CC3D的地面站在配置遥控时默认把油门解锁关闭，笔者建议配置遥控参数先检查油门有没有锁定，以防配置过程中忘记卸掉电池造成不必要的伤害。承接上面的配置过程，点击Radio Setup Wizard直接进入遥控配置界面。也可以点击Finish退出，从Configuration->Input->Start Configuration Wizard进入配置界面。如下图所示。

![](/assets/img/h250-config-11.png)

![](/assets/img/cc3d-rc-1.png)

进入遥控配置向导后，操作将会提示按照屏幕上的指示去操控遥控杆，任意时刻都可以取消或者返回上一步。将接收器和CC3D连接正确，**CC3D使用电池供电**，开启遥控器电源。看到接收器FS-R6B上红色的LED亮起，则表示遥控器和接收器连接（对频）成功，可以进行后面的操作。如果LED未亮起，可以从下面几点检查：

* 接收器和CC3D连接是否正确。注意连接线的正反和顺序。
* CC3D电源供电是否开启。测试发现，只使用USB给CC3D供电是无法满足接收器的供电的。
* 接收器和遥控器是否需要对频。有关对频问题，参考todo。

Next，进入遥控器发射机类型选择，acro类型或者直升机类型。acro类型适用于固定翼或四轴，我们选择acro类型。

![](/assets/img/h250-config-14.png)

Next，进入遥控器操作模式选择，也就是常说的美国手或者日本手选择。提供4种模式，根据个人习惯去选择，笔者选择默认模式美国手，即Mode 2。油门和方向在左，俯仰和横滚在右。

![](/assets/img/h250-config-15.png)

Next，根据屏幕指示去操作遥控器，分别对油门、横滚、俯仰、方向即模式进行校准。

![](/assets/img/h250-config-16.png)

Next，飞行模式校准，这里由于笔者使用的是富斯T6的遥控，没有对应的通道切换开关，但是富斯T6的VRA旋钮开关与之对应，可通过旋钮开关进行配置。Next还有关于Accessory0、Accessory1、Accessory2的配置，没有对应开关选择点击next直接跳过。

![](/assets/img/h250-config-20.png)

各项对应配置完成之后，操作界面将会提示将各通道开关归中。笔者遥控没有后面对应的遥控通道，在配置中直接跳过，这里选择跳过。

![](/assets/img/h250-config-21.png)

Next，操作提示随意拨动油门、横滚、俯仰、方向摇杆及模式切换开关，观察是否与实际的摇杆动作方向一致。若某个通道方向相反，可以通过勾选其对应通过取反，无需在遥控器上配置，如图所示。

![](/assets/img/h250-config-22.png)

截止以上，遥控的通道操作基本配置完成，点击右下角save保存，next进入遥控的解锁配置操作，CC3D的地面站在配置遥控时默认把油门解锁关闭，解锁方式根据自己的个人习惯而定，提供自定义解锁方式，下面还有一个配置栏是设定无信号接收等待时间自动上锁，默认为30s。一般我们都会配置解锁操作为：油门拉到最低（throttle off），同时右手摇杆向左横打（roll left）。

最后点击save保存设置。

*![](/assets/img/cc3d-rc-2.png)

最后可以测试遥控器配置是否正确。为了安全首先去掉桨叶。将CC3D上电，并且连上遥控器，可以看到CC3D上蓝色LED慢速闪烁，接收机上红色LED亮起。按照上面设定的解锁操作解锁飞机。如果解锁成功，CC3D上蓝色LED会快速闪烁。轻推油门到一定值，这时候电机就会开始转动。

## 遥控数据解读及手动配参
