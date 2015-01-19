---
layout: post
title: 使用U盘安装Linux系统
---

### 安装前
    确认Bios中已挂载相应的硬盘个数（Bios中查询），raid设置可以咨询主板供应商。

### 使用UltraISO制作U盘Linux引导
+ 准备材料
  	- 8G U盘一个
      - ios 文件
      - UltraISO

##### *制作U盘引导（以Centos为例）*

#####    1. 使用UltraISO软件，打开需要安装的Linux iso文件

   ![](http://i.imgur.com/h7J27Jd.png)
   ![](http://i.imgur.com/SmKKvJW.jpg)
   ![](http://i.imgur.com/741VO8x.jpg)
   
#####    2. 开始将iso写入U盘

   ![](http://i.imgur.com/IFHXxMV.jpg)

#####    2.1  格式化U盘

   ![](http://i.imgur.com/lr8eYHm.jpg)
#####    2.2  设置便捷启动

   ![](http://i.imgur.com/GLqnltY.jpg)

#####    2.3  iso写入U盘

   ![](http://i.imgur.com/1YfejbN.jpg)
   ![](http://i.imgur.com/0KKGDTe.jpg)

#####    2.4  删除U盘中的Package与EFI文件夹（若EFI文件夹不存在则忽略），并将需要安装的Linux 

iso文件全部复制在U盘根目录下(红色为需要删除的，蓝色是需要添加的)
   ![](http://i.imgur.com/0rOD50V.jpg)

### 安装Linux（以Centos举例）
    安装过程不再赘述，仅需要赘述一步。
    如下图：勾选 Install boot loader on /dev/sda(复选框)
           点击 更改设备弹出引导程序设备对话框 
           选择 Master Boot Record(MBR) -/dev/sda(单选按钮) 
           设置 BIOS驱动器顺序 
           第一BIOS驱动器：选择sda（本地磁盘驱动器）(选择硬盘启动) 
           第二BIOS驱动器：选择sdb（U盘驱动器）
           点击确定

#####U盘安装Linux网上文档陷阱重重，现将多篇文档进行汇总，并顺利亲测完成安装操作。
出处：[百度经验](http://wenku.baidu.com/link?url=Qr6oIoUrU9cp_t8hd1nriPri8VMfcowkIVVtz2Vv8t1e3_nItB06jSoW64LKk9nc6uuSjaV5dM9g5D2DFwVYpVoTzA_CEfn0w4OEdHDhmtO)，[百度百科](http://wenku.baidu.com/link?url=Qr6oIoUrU9cp_t8hd1nriPri8VMfcowkIVVtz2Vv8t1e3_nItB06jSoW64LKk9nc6uuSjaV5dM9g5D2DFwVYpVoTzA_CEfn0w4OEdHDhmtO "百度百科")

