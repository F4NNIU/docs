W600 RT-Thread(体验版)入门指导教程
==================================

1.RT-Thread 简介
----------------

`RT-Thread <http://www.rt-thread.org/>`__
是一个来自中国的开源物联网操作系统，它具备非常强的可伸缩能力：从一个可以运行在
ARM Cortex-M0 芯片上的极小内核，到中等的 ARM Cortex-M3/4/7
系统，甚至是运行于 MIPS32、ARM Cortex-A 系列处理器上。 RT-Thread
项目的源代码托管在 `GitHub repo <https://github.com/rt-thread>`__ 上。

2.准备工作
----------

-  W600_RT-Thread 源码：:download:`RT-Thread_W60X_SDK_0.1.0 </download/soc/RT-Thread_W60X_SDK_0.1.0.zip>` 
-  Keil环境搭建：`SOC二次开发入门指导 </development/soc/start>`__
-  RT-Thread
   env工具：https://github.com/RT-Thread/env
-  串口下载工具：`串口调试助手 </download/tools>`__ 
-  开发板 TB-01开发板（\ `购买链接 <http://shop.thingsturn.com/>`__\ ）

3.环境搭建
----------

3.1编译环境搭建
~~~~~~~~~~~~~~~

该SDK可以由Keil直接编译，详情参考 `SOC开发入门指导 </development/soc/start>`__

3.2 工程目录介绍
~~~~~~~~~~~~~~~~

.. image:: start.assets/1551025944478.png


docs文件夹下放着W600_RTT相关的参考文档，建议先阅读
UM3103-RT-Thread-W60X-SDK 快速上手.pdf 和 UM3101-RT-Thread-W60X-SDK
开发手册.pdf

4.编译烧录
----------

4.1编译
~~~~~~~

W600_RT-Thread_SDK（体验版）提供了三个Demo，让用户体验W600_RT-Thread的特别之处，找到目录RT-Thread_W60X_SDK:raw-latex:`\examples`，进入各个Demo中双击project.uvprojx工程文件，直接编译即可（注意，一定要完成2.准备工作中的Keil环境搭建）。

固件生成在RT-Thread_W60X_SDK\examples\Bin目录下`。

.. image:: start.assets/1551026444198.png


.. image:: start.assets/1551026555274.png

4.2 烧录
~~~~~~~~

可烧录文件为xxx.fls（文件名后缀为.fls）；

烧录方式参考如下截图（截图为Demo:02_micropython的演示效果）；

烧录遇到问题的用户请参考: `W600固件烧录指南 </application_note/download_firmware/>`__

.. image:: start.assets/1551026780483.png

