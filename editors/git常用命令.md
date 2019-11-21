

## 树形展示git log的相关方式

```
git log --stat=1000 --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative
```

## 所有的变更都以树形结构展示出来

```
git log -p --stat=1000 --graph
```

## git简易报表

```
git_stat generate
```


##  将在所有分支上输出最新标记的提交的标记
```
git describe --tags $(git rev-list --tags --max-count=1)
```

##  要获取最新tag
```
git describe --tags
```

##  要获取最新的带注释tag
```
git describe --abbrev=0
```
