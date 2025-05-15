# <center>VOFA+调节pid参数</center>

## 一、什么是VOFA+  
VOFA+就是一款串口助手，它不仅能够实现基础的串口数据收发，还能实现数据绘图（包括直方图、FFT图），控件编辑，图像显示等功能。使用VOFA+，可以给我们平常的PID调参等调试带来方便。这是VOFA+官网链接，可以在点击超链接进行下载。

### 1.打开vofa界面
[![](https://pic.imgdb.cn/item/67088879d29ded1a8c4fd116.png)](https://pic.imgdb.cn/item/67088879d29ded1a8c4fd116.png)  

### 2.串口协议配置
这里是串口协议和串口一些配置，配置那些跟着代码来就行，波特率9600，无流控，无校验位，8位数据位，1位停止位，端口号是根据自己stm32与电脑相连的端口号一致，端口号可以在设备管理器中查看到。

[![](https://pic.imgdb.cn/item/670888c2d29ded1a8c502336.png)](https://pic.imgdb.cn/item/670888c2d29ded1a8c502336.png)

在这里我们使用justfolat通讯协议。

### 3.放置控件

将控件中的第一个拖出来拖到那个大大的窗口中，然后再双击边缘，就能够放大波形图控件了。当然你不想太大也可以直接就拖动边缘，任意大小。

##### a.波形图
[![](https://pic.imgdb.cn/item/6708890dd29ded1a8c508fd1.png)](https://pic.imgdb.cn/item/6708890dd29ded1a8c508fd1.png)  

#### b.参数控件
[![](https://pic.imgdb.cn/item/67088998d29ded1a8c514451.png)](https://pic.imgdb.cn/item/67088998d29ded1a8c514451.png)

### 4.命令配置
那命令是什么呢，这里我们可以理解成触发了事件（改变了参数），就执行了命令（发送更改后的参数给stm32），以下就是我对命令的配置。名称即为命令的名称，可以跟对应的控件相同名称。如我这里是Kp,即当我的Kp发生数值改变时，命令就会自动发送一个内容为 #P1=%f! 这里的%f即为你Kp的数值。对应的可以设置Ki,Kd的命令，发送内容分别为 #P2=%f! ,#P3=%f! 。这里为什么有123，是因为后面要在stm32中提取该数，然后就可以分别VOFA+发送给stm32是对应哪个需要改变的变量了。

[![](https://pic.imgdb.cn/item/670889f1d29ded1a8c519da5.png)](https://pic.imgdb.cn/item/670889f1d29ded1a8c519da5.png)  
 

## 二、代码实现
以下代码是针对于justfloat通讯协议:

```
void Vofa_data(int data1,int data2)
{
    int data[2];
    float tempFloat[2];   
    uint8_t tempData[12];   

    data[0] = data1;
    //data[1] = data2;


    tempFloat[0] = (float)data[0];    
    //tempFloat[1] = (float)data[1];


    //memcpy(tempData, (uint8_t *)tempFloat, sizeof(tempFloat));  

    tempData[8] = 0x00;//写入结尾数据
    tempData[9] = 0x00;
    tempData[10] = 0x80;
    tempData[11] = 0x7f;
    int ii;
    for(ii=0;ii<=11;ii++){
        //DL_UART_Main_transmitDataBlocking(UART_HMI_INST,tempData[ii]);
    	HAL_UART_Transmit(&huart6, &tempData[ii], 4, 100);

    }
}

```

以上就是我调pid的方法



