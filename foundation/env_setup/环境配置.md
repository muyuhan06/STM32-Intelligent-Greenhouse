# env_setup 项目环境配置

## Keil MDK-Community 完整配置指南

**适用场景**：【智能温室项目】的STM32 Cortex-M 单片机开发（学生/创客/非商业用途）
**文档目标**：通过 **step-by-step 流程+关键截图**，完成从“**下载安装**”到“**环境验证**”的全流程配置


### **一、准备工作**
1. **注册 ARM 账号**：

   访问 [ARM 注册页](https://developer.arm.com/register)，选择**非商业身份**（学生/创客），填写真实信息并验证邮箱。（激活**必需**）

   ![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/注册ARM.png)
2. **确认芯片型号**：

  明确需开发的 STM32 芯片系列【 `STM32F103C8T6`】，后续安装对应支持包。

3. **网络连接**：

  激活及支持包安装需联网


### **二、核心配置流程**

#### **1. 下载**
**操作步骤**：

- 访问 Keil 官网下载页：[MDK-ARM Downloads](https://www.keil.com/download/product/)；

![下载MDK-Arm](https://raw.githubusercontent.com/muyuhan06/image-repo/main/image-20250721220227167.png)

点击MDK-Arm

- 填写表单获取软件

![填写表单](https://raw.githubusercontent.com/muyuhan06/image-repo/main/image-20250721220505494.png)

- 提交表单后，点击  `MDK542A.EXE`  开始下载安装包

  ![安装版本](https://raw.githubusercontent.com/muyuhan06/image-repo/main/安装版本.png)


#### **2. 安装 **
**操作步骤**：

- 双击下载的 `MDK542A.EXE`，勾选**“I agree to the terms…”**（同意许可）；
- 选择安装路径（默认路径）；

![安装路径](https://raw.githubusercontent.com/muyuhan06/image-repo/main/安装路径.png)

- 填写用户信息（建议与前面一致）；
- 点击**“Install”**，等待安装完成（约 2 分钟），点击**“Finish”**。


#### **3. 激活**
**操作步骤**：

- 打开桌面快捷方式 `Keil uVision5`；
- 点击菜单栏 **File → License Management**（文件→许可证管理）；
- 切换到**“User-Based License”** 标签页，点击**“Activate / Deactivate…”**（激活/注销）；
- 自动打开**Arm License Management Utility 1.3.5**，保持**“License Server”** 选中，服务器地址填 `https://mdk-preview.keil.arm.com`；

![激活码按官网教程](https://raw.githubusercontent.com/muyuhan06/image-repo/main/激活码按官网教程.png)

- 点击**“Query”**，（可能需要登录 ARM 账号输入注册邮箱和密码）；
- 验证成功后，工具会显示**激活状态**（产品名称、有效期、缓存时间）。

![使用期限](https://raw.githubusercontent.com/muyuhan06/image-repo/main/使用期限.png)


#### **4. 安装 STM32 设备支持包**
**操作步骤**：

- 在`Keil uVision5`中，点击工具栏**“Pack Installer”**（或按 `Ctrl+P`）；

![PackInstaller](https://raw.githubusercontent.com/muyuhan06/image-repo/main/image-20250721222518120.png)

【我是在安装时直接弹出界面，重新打开软件后使用快捷键并没有打开，在工具栏打开的】

- 左侧**“Devices”** 栏展开**“STMicroelectronics → STM32F1 Series”**（选择你的芯片系列）；

- 右侧**“Packs”** 栏找到**“Keil::STM32F1xx_DFP”**（对应 F1 系列），点击**“Install”**（若已安装，状态为“Up to date”）；

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/插件包安装.png)

- 等待下载安装完成（约 1 分钟）。

#### **5. 验证**

（纯软件测试——硬件没到货）

**操作步骤**：
- 点击菜单栏 **Project → New μVision Project**（新建工程）；
- 选择保存路径（如 `C:\Projects\STM32_Test`），输入工程名（如 `STM32_Test`）；
- 搜索并选择芯片型号（如 `STM32F103C8Tx`），点击**“OK”**；
- 在**“Manage Run-Time Environment”** 窗口中，勾选：
- **CMSIS → Core**（Cortex-M 内核支持）；
- **Device → Startup**（芯片启动文件）；

![勾选](https://raw.githubusercontent.com/muyuhan06/image-repo/main/Manage%20Run-Time%20Environment.png)

- 点击**“OK”**，生成空工程；
- 点击工具栏**“Build”**（或按 `F7`），查看编译输出。

![成功创建空项目](https://raw.githubusercontent.com/muyuhan06/image-repo/main/成功创建空项目.png)

0 Error 0 warning；没问题OK 

**tips:**

如果只按照步骤来会出现问题，因为需要提前准备好main.c

我依旧准备的是一个空文件


### **三、常见问题排查**
**问题1：编译时“头文件缺失”（如 `stm32f103xb.h` 找不到）**

- **现象**：编译输出显示“fatal error: stm32f103xb.h: No such file or directory”；
- **解决方案**：打开 Pack Installer，确认**Keil::STM32F1xx_DFP** 已安装（状态为“Up to date”）；【见二、4.】

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/%E6%8F%92%E4%BB%B6%E5%8C%85%E5%AE%89%E8%A3%85.png)

**问题2：安装时“权限不足”**

- **现象**：安装向导提示“无法写入文件”；
- **解决方案**：右键点击安装包，选择**“以管理员身份运行”**；

![文件无法写入](https://raw.githubusercontent.com/muyuhan06/image-repo/main/问题排查—无法写入文件.png)


### **四、总结**
#### **配置完成标志**
- [x] μVision IDE 可正常启动；
- [x] 激活状态显示“Keil MDK Community”（长期有效）；
- [x] STM32 设备支持包已安装；
- [x] 空工程编译无错误。

遵循以上流程，即可完成 Keil MDK-Community 的完整配置，为 STM32 开发做好准备！ 🚀

## STM32CubeMX 完整配置指南

本指南旨在帮助新手快速搭建**STM32F103C8T6**开发环境，基于**STM32CubeMX+Keil MDK**实现智能温室系统的基础功能（如LED闪烁、传感器采集等）。

### **一、前置条件**

1. **软件准备**：已安装**Keil MDK Community Edition**（激活并安装STM32F1支持包）；
2. **硬件准备（后续需要）**：STM32F103C8T6最小系统板、ST-Link调试器、传感器（DHT11温湿度、光敏电阻等）。

### **二、STM32CubeMX 安装步骤**

#### 1. 下载

下载需要注册或登陆账户

- 进入ST官网注册账号——[官网首页](https://www.st.com.cn/content/st_com/zh.html)

- 注册后登录（会发送邮件填写密码，保存好）

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.1注册后登录myST账号.png)

- 在首页搜索产品型号，点击产品型号`STM32CubeMX`进入下载页面

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.2产品位置.png)

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.3获取软件.png)

- 选择**Windows Installer**（适合Windows系统），登录ST账号后下载。【一开始登陆好的再进去就不用登陆了，是不是很方便】，点击后会弹出协议，必须接受，然后就开始下载

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.4选择适合的版本，建议最新.png)

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.5接受协议.png)

#### 2. 安装

- 找到下载的安装包（`STM32CubeMX-6.15.0-win.exe`），**右键→以管理员身份运行**；
- 选择安装语言（默认中文），同意许可协议；
- 保持默认安装路径，点击“安装”；
- 一直默认

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.6%E7%BB%A7%E7%BB%AD%E5%8B%BE%E9%80%89%E6%BF%80%E6%B4%BBnext.png)

#### 3.**安装STM32F1 Series支持包**

-------

STM32CubeF1是STM32F1系列芯片（如STM32F103C8T6）的**核心支持包**，包含：

- 该系列芯片的**引脚定义**（如PC13、PA1等）

- **HAL库驱动**（GPIO、ADC、UART等外设初始化代码）

- **时钟树配置模板**（如8MHz晶振→72MHz系统时钟）

其为CubeMX生成STM32F103C8T6正确代码的基础，**无此包则无法支持该芯片**，会导致“芯片未支持”提示或初始化逻辑错误。

------

打开软件，如图步骤，第④之后依旧会用到账号登陆

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.7安装支持包.png)

成功

![](https://raw.githubusercontent.com/muyuhan06/image-repo/main/2.8支持包成功.png)

## **扩展阅读资源**

### 一、STM32CubeMX User Manual.pdf

​     STM32CubeMX 工具的用户手册，详细介绍了这款图形化工具的功能，包括 STM32 微控制器及开发板的选择、引脚和时钟树配置、外设与中间件设置、初始化 C 代码生成等。还涵盖安装运行、用户界面操作、代码生成规则及多个使用教程，为开发者配置 STM32 项目提供全面指导

### 二、STM32F10xxx 官方手册（RM0008）.pdf

​        STM32F10xxx 系列微控制器的官方技术参考手册，面向开发者提供内存和外设使用的完整信息，涵盖内存架构、电源控制、时钟系统、I/O 端口、定时器、通信接口等模块的工作原理与配置方法，是软件开发的核心参考资料

### 三、STM32F103C8Tdatasheet.pdf

​        STM32F103C8 型号微控制器的数据手册，聚焦硬件特性，包括 CPU 内核、存储容量（64/128KB Flash、20KB SRAM）、引脚定义、电气参数、封装信息及订购方案等，供硬件设计和器件选型参考。

