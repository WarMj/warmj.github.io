---
layout: post
title: RedHat7---CentOS-7-忘记root密码修改
description: 时间久了就会忘……
author: "WarMj"
categories: linux
tags: [linux,centos7,redhat]
image: 
---

### 进入互动式命令环境
1. 开机出现 `grub boot loader` 开机选项菜单时，立即点击键盘任意鍵，`boot loader` 会暂停。
2. 按下`e`，编辑选项菜单。
3. 移动上下鍵至 `linux16` 核心命令行：

`linux16 /vmlinuz-3.10.0-123.el7.x86_64 root=UUID=449d53d1-84c2-40c0-b05e-d1900591d71b ro rd.lvm.lv=vg_kvm7usb/swap crashkernel=auto`
`vconsole.keymap=us crashkernel=auto vconsole.font=latarcyrheb-sun16 rd.lvm.lv=vg_kvm7usb/root rhgb quiet LANG=en_US.UTF-8 rd.break`

4. 在核心命令行最后加入**rd.break**。
5. 再按下Ctrl+x 重新以这个设定开机。

### 修改密码
开机后的互动式命令环境，並不是正常开机的系统，正常开机系统挂载在`/sysboot`且挂载成只读，必須重新挂载成可写入，才能修改密码，步骤如下：
1. 重新挂载`/sysroot`成可读可写，并切换到`/sysroot`。

        switch_root:/# mount –o remount,rw /sysroot
        switch_root:/# chroot /sysroot
2. 设定密码

        sh-4.2# passwd
3. 因为在此情況下，SELinux 並沒有启动，对所有文件的更改，可能会造成文档的 context 不正确，为确保开机时重新设定 SELinux context，必須在根目录下添加隐藏文件`.autorelabel`。

        sh-4.2# touch /.autorelabel
4. 退出chroot，并重新开机

        sh-4.2# exit
        switch_root:/# exit
重启后，使用修改后root密码登入即可。

>参考
http://dywang.csie.cyut.edu.tw/moodle23/dywang/download/pdf/rhel7.pdf
