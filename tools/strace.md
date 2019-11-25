## 查看系统调用了哪些文件

```
strace -tt -T -f -e trace=file -o /data/log/strace.log -s 1024 <COMMAND>
```
