## 在VirtualBOX虚拟机软件上安装SUSE Linux 企业版 11 SP4

## 准备工作

- SUSE Linux Enterprise 11 SP4 安装介质下载

从 [SUSE 官方网站](https://www.suse.com/products/server/download/) 选择下载版本的类型。此次下载选择 [SUSE Linux Enterprise Server 11 SP4 AMD64/Intel 64](https://www.suse.com/eval/download/?build=l7C51hFz57E~&event_id=SGDGNTD18119&event_name=Eval%3A%20SLES%2011%20SP4%20AMD64%2FIntel64&icid=SGDGNTD18497&login_required=1) 60天试用评估版，下载需要注册一个账户。

进入页面后，选择下载：SLES-11-SP4-DVD-x86_64-GM-DVD1.iso 3.2GB 和 SLES-11-SP4-DVD-X86_64-GM-DVD2.iso 5.2GB.

下载的链接地址类似如下:

http://cdn.microfocus.com/prot/l7C51hFz57E~/SLES-11-SP4-DVD-x86_64-GM-DVD1.iso

http://cdn.microfocus.com/prot/l7C51hFz57E~/SLES-11-SP4-DVD-x86_64-GM-DVD2.iso

- VirtualBOX 虚拟机软件安装

从 [VirtualBOX 官方网站](https://www.virtualbox.org/wiki/Downloads) 选择下载适合自己操作系统版本的安装包。

比如当前可以下载的 Windows 版本的下载链接地址如下：

http://download.virtualbox.org/virtualbox/5.1.16/VirtualBox-5.1.16-113841-Win.exe

## 安装过程

- 创建新的虚拟机配置

1. 点击图标`New`, 或者从菜单：`Machine --> New...`
2. 新建系统界面，输入名称.Name:`SLE11sp4`, 类型选择 Type:Linux, 版本选择 Version:openSUSE(64-bit)
3. 设置内存大小。虚拟机的内存大小最大设置为主机的一半。
4. 新建硬盘。选择现在创建1个虚拟硬盘。
5. 选择磁盘类型，默认 VDI。
6. 默认选择动态扩展。
7. 选择虚拟硬盘保存的文件夹位置和虚拟硬盘的大小。Linux虚拟机硬盘建议大于8G以上。
8. 选择刚建立的虚拟机，点击图标`Settings`.
9. 在`General--> Advanced`内设置剪贴板的共享
10. 在`System --> Processor`内设置使用几个cpu核心
11. 在`Storage --> ` 添加更多的硬盘或者光驱。在光驱内添加进iso镜像。
12. 不需要声音，在`Audio`取消声音
13. 在`Network`设定虚拟机的网络类型。
14. 在`Shared Folders`内添加共享主机的文件夹。

- 在光驱内添加 下载好的SLE11SP4-DVD1的iso镜像文件。

- 点击`Start`，启动虚拟机。

- 选择 Installation 开始安装
- 默认 English(US), 勾选`I Agree to the License Terms.` __Next__
- 安装程序初始化中，完成后点击__Next__
- Media Check (usrional)
- Select Mode
  * 默认 New Installation
- 区域和时区设定
  * Regin:  Asia
  * Time Zone: Beijing
- Choose Scenario
  * 默认 Physical Machine
- 确认安装配置，开始安装
  * 默认分区只设置了swap和root
- 安装开始
- 安装完成后，重新启动
默认选择从硬盘启动
- 开始配置
- 设置root管理员的password。`tcAdmin`
- Hostname:`SLE11SP4TC10`
- 关闭防火墙(正式系统需要配置好)
- 开启SSH服务，可以用ssh远程访问
- 不测试互联网连接
- 默认网络服务配置
  * 默认的CA 管理
  * 不配置LDAP服务
- 用户认证模式
  * 默认的Local(/etc/passwd)
- 新建本地用户
  * Username:tcAdmin/tcAdmin
- 硬件确认
- 安装完成


