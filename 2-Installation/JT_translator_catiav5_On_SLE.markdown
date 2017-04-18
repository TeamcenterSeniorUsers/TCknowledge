## JT translator for catiaV5 on SUSE Linux 

- SUSE Linux Enterprise 11 SP4 虚拟机安装

- JDK1.7.0_80 在linux 上的安装

- SPLM License server 在Linux上的安装和查看 (可选)

### catia JT 转换器安装准备

- 安装介质
从 Siemens GTAC 下载需要安装的版本，本次安装下载的是如下的版本：
```
PLM_Components_JT_Bidirectional_Translator_for_CATIAV5_v11.1.tar.gz
```

- 解压缩安装包到临时目录

```
/## 如果没有 /home/infodba/temp 需要新建文件夹
tar zxvf PLM_Components_JT_Bidirectional_Translator_for_CATIAV5_v11.1.tar.gz -C /home/infodba/temp
```

### 安装过程

- 启动安装
```
su root
cd /home/infodba/temp/CDROM/
./install
```
- 点击 Install Software...
如果是非 root 用户会提示建议以 root 用户登录，是否继续
- Welcome 继续
- 选择安装文件夹路径，默认到 /opt
- 确认系统平台，Linux (64 bit)
- 选择安装语言，默认 English
- 选择安装组建，在 Components 内显示选中了 JT Bi-directional Translator for CATIA V5
- 确认安装信息
- 安装进行中
- 安装完成 Finish

### 安装完成配置 license

在安装目录下的 license 文件夹内新建 license.dat 文件
```
/# /opt/Siemens/JTTranslators/CATIAV5/11_1/license/license.dat
/# 文件内容如下,IP地址或者机器名是 license 服务器的地址：
SERVER 172.18.85.17 ANY TCP:28000
USER_SERVER
```

### 安装完成后用界面执行转换

- 默认启动命令
```
cd /opt/Siemens/JTTranslators/CATIAV5/11_1/bin
./OS_GUI
```
- 可以在自己的 home/bin 目录建立一个软链接启动
然后在需要转换的地方都可以通过运行 `catiav5tojt` 启动转换界面
```
cd ~/bin
ln -s /opt/Siemens/JTTranslators/CATIAV5/11_1/bin/OS_GUI catiav5tojt
```
### trubleshoot

- libXm.so.3

运行 install 时提示
```
error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
```
解决方式
1. 下载 openmotif22-libs-32bit-2.2.4-192.1.3x86_64.rpm
2. 运行 `sudo rpm -ivh openmotif22-libs-32bit-2.2.4-192.1.3x86_64.rpm`

可以在 https://www.rpmfind.net/linux/rpm2html/search.php?query=openmotif 找到 rpm 包。注意选择适合的操作系统版本。SUSE 系列可以用 OpenSuSE 的 rpm 包 
