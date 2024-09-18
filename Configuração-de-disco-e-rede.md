Abaixo seguem como estão montados os filesystems e como está a fstab.

[bulladm@CETIQT ~]$ cat /etc/fstab

UUID=050bbe31-cb07-4610-a5f8-ded2c339669c /                       xfs     defaults        0 0  
UUID=c1764128-43e9-47fe-95c3-7bcc7c0629ae /boot                   xfs     defaults        0 0  
UUID=54CA-693E          /boot/efi               vfat    umask=0077,shortname=winnt 0 0  
/dev/md1 /var/cache/fscache xfs defaults 0 0  
/dev/md0 /scratch  xfs defaults,nofail 0 0  
/dev/md2 /data  xfs defaults,nofail 0 0  

[bulladm@CETIQT ~]$ df -h  
Filesystem      Size  Used Avail Use% Mounted on    
devtmpfs        504G     0  504G   0% /dev    
tmpfs           504G   16K  504G   1% /dev/shm   
tmpfs           504G   11M  504G   1% /run  
tmpfs           504G     0  504G   0% /sys/fs/cgroup  
/dev/md126      446G   71G  376G  16% /  
/dev/md1        3.0T  4.5G  3.0T   1% /var/cache/fscache   
/dev/md0         99T   38M   99T   1% /scratch  
/dev/md127     1017M  157M  861M  16% /boot   
/dev/md125      201M   12M  190M   6% /boot/efi  
/dev/md2        148T  5.4T  143T   4% /data  
tmpfs           101G     0  101G   0% /run/user/1002   
[bulladm@CETIQT ~]$


[bulladm@CETIQT ~]$ ip a l  
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000  
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00  
    inet 127.0.0.1/8 scope host lo  
       valid_lft forever preferred_lft forever  
    inet6 ::1/128 scope host  
       valid_lft forever preferred_lft forever  
2: enp68s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000  
    link/ether 3c:ec:ef:fb:18:a0 brd ff:ff:ff:ff:ff:ff  
    inet 10.0.10.204/16 brd 10.0.255.255 scope global noprefixroute enp68s0f0  
       valid_lft forever preferred_lft forever  
    inet6 fe80::3eec:efff:fefb:18a0/64 scope link  
       valid_lft forever preferred_lft forever  
3: enp161s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000  
    link/ether 3c:ec:ef:b1:e9:38 brd ff:ff:ff:ff:ff:ff  
4: enp68s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000  
    link/ether 3c:ec:ef:fb:18:a1 brd ff:ff:ff:ff:ff:ff  
5: enp161s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000  
    link/ether 3c:ec:ef:b1:e9:39 brd ff:ff:ff:ff:ff:ff  

[bulladm@CETIQT ~]$ ip route  
default via 10.0.10.99 dev enp68s0f0 proto static metric 100  
10.0.0.0/16 dev enp68s0f0 proto kernel scope link src 10.0.10.204 metric 100  

```
[bulladm@CETIQT ~]$ cat /proc/mdstat
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4]
md125 : active raid1 sdw2[0] sdx2[1]
      205760 blocks super 1.0 [2/2] [UU]
      bitmap: 0/1 pages [0KB], 65536KB chunk

md2 : active raid6 sdh[7] sdl[11](S) sda[0] sdg[6] sdj[9] sdc[2] sde[4] sdb[1] sdf[5] sdk[10] sdi[8] sdd[3]
      158203763712 blocks super 1.2 level 6, 512k chunk, algorithm 2 [11/11] [UUUUUUUUUUU]
      bitmap: 3/131 pages [12KB], 65536KB chunk

md0 : active raid6 sdr[5] sdt[7] sdq[4] sds[6] sdp[3] sdo[2] sdn[1] sdm[0] sdu[8](S) sdv[9](S)
      105469175808 blocks super 1.2 level 6, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]
      bitmap: 0/131 pages [0KB], 65536KB chunk

md1 : active raid0 nvme1n1[1] nvme0n1[0]
      3125362688 blocks super 1.2 512k chunks

md126 : active raid1 sdx3[1] sdw3[0]
      467462144 blocks super 1.2 [2/2] [UU]
      bitmap: 2/4 pages [8KB], 65536KB chunk

md127 : active raid1 sdw1[0] sdx1[1]
      1047552 blocks super 1.2 [2/2] [UU]
      bitmap: 0/1 pages [0KB], 65536KB chunk

unused devices: <none>
```

