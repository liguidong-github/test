# MotorAppP3-2 V1.0版本更改记录  
   提交者: 李贵东 日期: 2021年1月19日
#### bug修复：俯仰轴回零标定失败。
1. 将Hall_Switch1()函数屏蔽，使用EXTI_Line4(stm32f10x_it.c)检测俯仰轴零位信息。
2. EXTI4_IRQHandler函数中，屏蔽My_SWStructure.Hall_SW1 = 1; 增加DevPara.Close_Switch1 = 1;
* 2、bug修复：方向轴回零标定失败。
       将POS_Switch1()函数屏蔽，使用EXTI_Line8(stm32f10x_it.c)检测方向轴零位信息。
       EXTI9_5_IRQHandler函数中，增加DevPara.Close_Switch3 =1;
* 3、bug修复：当俯仰轴细分数为16时，跑不到上位机设置转的特定角度。
       ClearResetMotor函数中，函数内增加4细分、16细分对应的管脚IO控制 (条件编译)。
* 4、user_conf.h中，将宏定义SUBDIV改为 2，推杆/方向轴细分数均设置为16。
* 5、user_conf.h中，增加 RETARDER条件编译项。
* 6、
* 7、

# Sn1MotorPutter功能
* 实现控制器定日镜运转，--> 通过控制2个步进电机-->一个步进电机对于减速机，一个对于推杆
* 俯仰轴：使用AK7451磁编码器，方位轴：使用的AS5600此编码器
* 推杆有2种分为P3-2推杆和P4-2推杆，通过user_conf.h文件条件编译，编译对应推杆程序

