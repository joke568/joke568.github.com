---
layout: post
title: 'linux的目录挂载（转载）'
---

项目初期用户文件较少,全部存储在/home目录下,/home目录没有单独划开分区,随着项目网站做大,用户文件越来越多,/home目录不够空间,想挂载一个新硬盘来负责储存

但发现新挂载/home到新硬盘时,/home原来数据变空了,这个原因是由于linux的VFS（虚拟文件系统）机制导致的,正常登录以后，所看到的各个目录，文件都是内核在加载时候构造在内存中的VFS目录树，而不是直接看到硬盘上的实际目录树。当你挂载某个设备到一个VFS挂载点上时(比如/home），系统就把VFS中的这个挂载点/home指向你最后所挂载的那个设备上。那么你现在访问该挂载点时，就会看到你最后挂载在此处的设备。而之前所挂载的设备依然在那里，只不过挂载点/home已经不再指向之前的设备。所以之前的数据是被隐藏了,但并没有删除,若umount挂载后,数据又重新回来了

基于这种情况,只能通过跳板的方式把原来的/home数据复制到新的/home分区下了 ,如何添加新硬盘,请查找相关资料

'''linux

mkdir /new  ###跳板目录

mount /dev/sdb1 /new  ###首先挂载跳板目录

cp -R /home/*  /new  ###复制/home目录所有数据到/new先

rm -rf /home/*       ####可选,主要为了腾出空间给原来的硬盘

mount /dev/sdb1 /home ###挂载/home 到新硬盘,此时你会神奇的发现之前的/home目录文件已经全部转移过来了,也许你会有点疑问,我并没有复制或移动/new文件到新挂载的/home目录啊,其实此时的/home目录相当于/new目录的硬链接,可以测试下mkdir /new/test 你会发现/home目录也存在test


umount /new ###解除挂载

rm -rf /new ###删除跳板目录

echo  "/dev/sdb1  /home    ext3    defaults    0 0" >> /etc/fstab ###开机启动挂载目录
'''