# 如何让mac电脑可以在不装第三方软件的情况下读取NTFS硬盘

1. 硬盘连接电脑
2. 找到硬盘的 Device Node
   ```
    diskutil info /Volumes/Elements 
   ```
3. 弹出你的硬盘
   ```
    hdiutil eject /Volumes/Elements
   ```
4. 创建一个目录用来挂在硬盘
   ```
    sudo mkdir /Volumes/MYHD
   ```
5. 将硬盘挂在到该目录
   ```
    sudo mount_ntfs -o rw,nobrowse /dev/disk2s1 /Volumes/MYHD/
   ```