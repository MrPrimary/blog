### 如何查看文件的md5校验码、sha1校验码和sha256校验码
本文是基于Windows 10系统和ubuntu 14.04系统环境，使用命令查看文件的md5校验码、sha1校验码和sha256校验码：
* Windows 10
* Ubuntu 14.04
---
#### Windows命令
* 进入cmd命令终端，键入如下的命令
```
# 查看文件的md5校验码
certutil -hashfile filename MD5
# 查看文件的sha1校验码
certutil -hashfile filename SHA1
# 查看文件的sha256校验码
certutil -hashfile filename SHA256
```
#### Linux命令
* 进入命令终端，键入如下的命令
```
# 查看文件的md5校验码
md5sum filename
# 查看文件的sha1校验码
sha1sum filename
# 查看文件的sha256校验码
sha256sum filename
```