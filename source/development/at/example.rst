参考示例
===================

一、创建STA与服务器进行TCP通讯
------------------------------

**设备端**\ ：

**1.设置工作模式**

AT+CWMODE=1

响应：

OK

**2.扫描周围路由信息**

AT+CWLAP

响应：

+CWLAP:(4,“ChinaNet-pYvA”,-70,“54:e0:61:15:96:89”,3)

+CWLAP:(4,“ChinaNet-UMSH”,-66,“f0:92:b4:28:c0:31”,3)

+CWLAP:(4,“WX_ThingsTurn”,-7,“2e:b2:1a:df:98:5b”,7)

OK

**3.设置要加入的AP的参数**

AT+CWJAP=“WX_ThingsTurn”,“thingsturn2018”

响应：

WIFI CONNECTED

WIFI GOT IP

OK

**4.创建TCP连接**

AT+CIPSTART=“TCP”,“192.168.2.198”,10001
//IP和端口按照实际参数填写，本参数为参考

响应：

CONNECT

OK

**5.发送发送数据的指令**

AT+CIPSEND=5

响应：

> //出现发送标识符，等待发送数据

**6.发送数据**

12345 //该处为实际发送的参数，不显示

响应：

SEND OK

**7.查询网络连接状态**

AT+CIPSTATUS

响应：

STATUS:3

+CIPSTATUS:0,“TCP”,“192.168.2.198”,10001,50831,0

二、创建STA与服务器进行透传TCP通讯
----------------------------------

**首先执行 一、创建STA与服务器进行TCP通讯**

**设备端**

**1.设置进入透传模式**

AT+CIPMODE=1

响应：

SEND OK

**2.触发透传模式**

AT+CIPSEND

响应：

> //触发透传模式后，后续可以直接发送数据，不会对指令进行响应

**服务器端：**

**3.服务器端发送数据**

12345

**设备端：**

**4.设备接收到数据:**

Server test

Server test

Server test

**5.退出透传模式**

+++ //不要加回车换行符

响应：

> //触发透传模式后，后续可以直接发送数据，不会对指令进行响应

三、创建STA上电保存进入透传模式
-------------------------------

**设备端：**

**1.设置工作模式**

AT+CWMODE=1

响应：

OK

**2.扫描周围路由信息**

AT+CWLAP

响应：

+CWLAP:(4,“ChinaNet-pYvA”,-70,“54:e0:61:15:96:89”,3)

+CWLAP:(4,“ChinaNet-UMSH”,-66,“f0:92:b4:28:c0:31”,3)

+CWLAP:(4,“WX_ThingsTurn”,-7,“2e:b2:1a:df:98:5b”,7)

OK

**3.设置要加入的AP的参数**

AT+CWJAP=“WX_ThingsTurn”,“thingsturn2018”

响应：

WIFI CONNECTED

WIFI GOT IP

OK

**4.保存透传到flash**

AT+SAVETRANSLINK=1,“192.168.2.198”,10001,“TCP”

响应：

OK

**5.复位**

AT+RST

响应：

OK

**6.退出透传模式**

+++ //不要加回车换行符  
`注意，无论上电有没有联网成功，模组都会处于透传模式，此时发送任何命令都会以数据的形式发出去，不会被响应`

响应：

四、创建AP作为服务器开启多链接通讯
----------------------------------

**设备端**

**1.设置工作模式**

AT+CWMODE=2

响应：

OK

**2.设置要创建的AP的参数**

AT+CWSAP=“ThingsTurn”,“123456789”,5,3

响应：

OK

**3.查询创建的AP的参数**

AT+CWSAP?

响应：

+CWSAP:“ThingsTurn”,“123456789”,5,3,4,0

OK

**4.使能多链接**

AT+CIPMUX=1

响应：

OK

**5.创建服务器**

AT+CIPSERVER=1,10000

响应：

OK

**客户端：**

**注：客户端可以用PC软件或者其他软件模拟，所有客户端必须和设备端再同一个局域网内，否则无法连接通讯。**

**6.使用PC软件或者其他w600系列模组作为客户端连接设备端**

.. image:: example.assets/wps69DD.tmp.jpg
   :width: 500px
   :align: center 

**7.客户端发送数据到服务器**

.. image:: example.assets/wpsD877.tmp.jpg
   :width: 500px
   :align: center 

**设备端**

**8.服务器设备端发送数据到所有的客户端**

.. image:: example.assets/wps8060.tmp.jpg
   :width: 500px
   :align: center 

五、智能配网（smartconfig）
---------------------------

**使用智能配网的方式，通过手机让设备连上路由（支持微信、app)**

.. image:: example.assets/wps13EC.tmp.jpg
   :width: 500px
   :align: center 
   
.. image:: example.assets/wpsA803.tmp.jpg
   :width: 500px
   :align: center 

六、修改波特率
--------------

**注意V1.0.10 版本不支持流控设置**

.. image:: example.assets/wpsC030.tmp.jpg
   :width: 500px
   :align: center 

七、恢复出厂设置
----------------

**注：在调试阶段，一些指令的参数会被保存，上电是自动设置，会影响调试，建议使用AT+RESTORE清除这些配置，而不是使用AT+RST复位。**


.. image:: example.assets/wps2738.tmp.jpg
   :width: 500px
   :align: center 















