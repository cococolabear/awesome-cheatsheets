

## 树形展示git log的相关方式

```
git log --stat=1000 --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative
```

## 所有的变更都以树形结构展示出来

```
git log -p --stat=1000 --graph
```
