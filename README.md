# STM32_PracticeProject

[cite_start]基于 STM32 的双机通讯直流电机 PID 闭环控制系统 [cite: 1][cite_start]。本项目实现了一个由上位机和下位机组成的协同控制系统 [cite: 2, 3, 8][cite_start]。上位机负责 ADC 信号采集、按键逻辑处理及指令下发；下位机负责电机测速、PID 调控、Flash 存储、OLED 显示及 MPU6050 姿态解算 [cite: 4, 5, 6, 7, 9, 10, 11, 12, 13]。

### 上位机功能：
* [cite_start]**ADC 采集**：采集电位器数值并映射，正常挡位 -100～+100，低速档 -50～+50 [cite: 4]。
* [cite_start]**按键 1**：一键启停电机，上电默认为停止状态 [cite: 5]。
* [cite_start]**按键 2**：切换速度挡位（正常/低速） [cite: 6]。
* [cite_start]**通讯**：通过 USART 将电机状态、挡位及设定速度传给下位机 [cite: 7]。

### 下位机功能：
* [cite_start]**速度闭环**：通过编码器读取实际转速 [cite: 9][cite_start]，并利用 PID 调控使速度稳定 [cite: 10]。
* [cite_start]**数据存储**：通过 Flash 保存并刷新按键 1 触发期间的实际电机速度 [cite: 11]。
* [cite_start]**实时显示**：通过 IIC 接口驱动 0.96 寸 OLED，显示启停状态、挡位、设定/实际速度及 Flash 值 [cite: 12]。
* [cite_start]**姿态解算**：使用 MPU6050 陀螺仪，将三轴数据转换为欧拉角（Yaw, Roll, Pitch）并显示 [cite: 13]。
