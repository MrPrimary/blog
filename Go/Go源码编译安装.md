从源码安装，首先要进行编译。Go 1.5实现了bootstrapping，因此编译1.5以后的版本和编译1.5以前的版本会略有不同。bootstrapping是编译器领域的一个术语，中文翻译为自举或自展，通俗地讲“用要编译的目标语言编写其编译器（汇编器）”。Go1.5开始编译器和运行时完全用Go语言编写（还有少量汇编）；go1.4是最后一个用C编写工具链的发布。

### 编译Go1.4，Centos8系统

```
wget https://storage.googleapis.com/golang/go1.4-bootstrap-20170531.tar.gz
tar zxvf go1.4-bootstrap-20170531.tar.gz -C /home/primary
cd go/src
/make.bash

//成功后会出现如下信息
---
Installed Go for linux/amd64 in /home/primary/go
Installed commands in /home/primary/go/bin
//重命名1.4文件夹，并添加GOROOT_BOOTSTRAP环境变量
mv go go1.4  
export GOROOT_BOOTSTRAP=/home/primary/go1.4
```

### 编译Go1.5及以上版本

Go 1.5开始编译器和运行时用go自身编写，要编译它们，首先要安装go编译器。all.bash 编译脚本会在$GOROOT_BOOTSTRAP环境变量中查找一个已经存在的go tool chain，实际上就是要有一个编译好的bin/go程序，$GOROOT_BOOTSTRAP/bin/go 应该是go二进制命令。有很多选择，可以在官网(<https://golang.org/dl/>)下载go发布包；也可以用go1.4源码编译，也就是按照上面的步骤编译go1.4，然后再去编译更高版本的go。

如果没有安装go编译器，直接运行src/all.bash，会出现错误：
```
[primary@Greenplum src]$ ./all.bash 
Building Go cmd/dist using /home/primary/go1.4.
ERROR: Cannot find /home/primary/go1.4/bin/go.
Set $GOROOT_BOOTSTRAP to a working Go tree >= Go 1.4.
```
#### go1.13安装
```
tar zxvf go1.13.1.src.tar.gz -C /home/primary
cd go/src  
./all.bash 
```
#### 设置环境变量
```
export PATH=$PATH:/home/go/bin
[primary@Greenplum ~]$ go version
go version go1.13.1 linux/amd64
```
