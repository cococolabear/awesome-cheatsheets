## vagrant

[vagrant-awesome](https://github.com/iJackUA/awesome-vagrant)

### vagrant box初始化目录

When you box add it downloads box to `/home/user/.vagrant.d/boxes`. These box copies could be reused between different Vagrantfiles. When you launch Box - it makes a copy of downloaded box.
Real boxes with changes according to each project is stored in `/home/user/VirtualBox VMs`.
That's not a big deal, but good to understand that.


### vagrant box的加载方式

```
vagrant box add {title} {url}
vagrant init {title}
vagrant up
```

### 同步文件

** 默认方式 **

默认情况下，您可以发现在vagrant框中看到/ vagrant文​​件夹，并且它是主机上Vagrantfile所在的文件夹。该文件夹通过VirtualBox的“共享文件夹”功能在主机和Vagrant之间共享

您可以指定自己的共享文件夹集，例如：config.vm.synced_folder "./"，"/var/www" 该功能允许您将项目文件存储在主机上

** NFS **

安装nfs命令

```
sudo apt-get install nfs-kernel-server
```

配置文件
```
config.vm.synced_folder "./", "/var/www", type: "nfs"
```
> 不支持window

** rsync **

```
config.vm.synced_folder "./", "/var/www", type: "rsync"
```

同步文件
```
vagrant rsync-auto
```


## vagrant plugin

### vagrant-hostsupdater 

```
vagrant plugin install vagrant-hostsupdater
```

### vagrant-hostmanager

### vagrant-omnibus

通过特定于平台的Omnibus软件包安装了Vagrant插件，可确保安装所需的Chef版本。




