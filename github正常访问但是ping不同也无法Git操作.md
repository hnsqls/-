## Github 正常访问但是ping不同也无法进行git操作

原因：在git push 的时候 发现一直push不上去。

```shell
$ git push interview master
ssh: connect to host github.com port 22: Connection timed out
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

```

网站可以正常访问，但是主机ping却ping不通

```shell
C:\Users\26611>ping github.com

正在 Ping github.com [20.205.243.166] 具有 32 字节的数据:
请求超时。
请求超时。
请求超时。
请求超时。

20.205.243.166 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 0，丢失 = 4 (100% 丢失)，
```

经过查询资料可以修改将github ip 添加到hosts 文件中

github动态ip[www.github.com - GitHub · Build and ship software on a single, collaborative platform · GitHub](https://www.ipaddress.com/website/www.github.com/)

win10 hosts 文件位置 如下图

![image-20241231100147150](images/github正常访问但是ping不同也无法Git操作.assets/image-20241231100147150.png)

可以ping通

```shell
C:\Users\26611>ping github.com

正在 Ping github.com [140.82.112.4] 具有 32 字节的数据:
来自 140.82.112.4 的回复: 字节=32 时间=291ms TTL=45
来自 140.82.112.4 的回复: 字节=32 时间=430ms TTL=45
来自 140.82.112.4 的回复: 字节=32 时间=299ms TTL=45
来自 140.82.112.4 的回复: 字节=32 时间=318ms TTL=45

140.82.112.4 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 291ms，最长 = 430ms，平均 = 334ms
```

git操作可以正常操作了

```shell
$ git push interview master
Enumerating objects: 25, done.
Counting objects: 100% (25/25), done.
Delta compression using up to 12 threads
Compressing objects: 100% (22/22), done.
Writing objects: 100% (22/22), 386.20 KiB | 1.69 MiB/s, done.
Total 22 (delta 10), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (10/10), completed with 3 local objects.
To github.com:hnsqls/interview.git
   afbfadb..a5d5746  master -> master
```

