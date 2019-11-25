[vagrant plugins](https://github.com/hashicorp/vagrant/wiki/Available-Vagrant-Plugins)

## Plugin Expunge
格式：

```
vagrant plugin expunge [-h]
```
这将删除所有用户安装的插件信息。所有插件gems、它们的依赖关系和plugins.json文件都会被删除。这个命令提供了一个简单的机制来完全删除所有用户安装的自定义插件。

```
test-Pro:~ user$ vagrant plugin expunge -h
Usage: vagrant plugin expunge [-h]
        --force                      Do not prompt for confirmation  强制执行
        --local                      Include plugins from local project for expunge  删除包括本地项目中的插件
        --local-only                 Only expunge local project plugins  只删除本地项目中的插件
        --global-only                Only expunge global plugins 只删除全局插件
        --reinstall                  Reinstall current plugins after expunge 在删除后重新安装当前的插件
    -h, --help                       Print this help 打印帮助信息
```

当升级vagrant时，可能由于内部不兼容的问题需要重新安装插件。expunge命令可以通过尝试自动重新安装当前配置的插件来帮助简化这个过程，即使用--reinstall标签:

```
# Delete all plugins and reinstall
$ vagrant plugin expunge --reinstall
```

## Plugin Install

格式：
```
vagrant plugin install <name>... [-h]
```
这将安装具有给定名称或文件路径的插件。如果名称不是文件的路径，那么插件将从远程存储库安装，通常是RubyGems。如果已经安装了插件，这个命令还会更新插件，但是你也可以使用vagrant plugin update来更新插件。

如果插件已经安装，这个命令将用最新版本重新安装它。

```
test-Pro:~ user$ vagrant plugin install -h
Usage: vagrant plugin install <name>... [-h]

        --entry-point NAME                The name of the entry point file for loading the plugin. 加载插件的入口点文件的名称
        --plugin-clean-sources            Remove all plugin sources defined so far (including defaults) 删除到目前为止定义的所有插件源(包括默认插件)
        --plugin-source PLUGIN_SOURCE     Add a RubyGems repository source 添加RubyGems库资源
        --plugin-version PLUGIN_VERSION   Install a specific version of the plugin  安装指定版本的插件
        --local                           Install plugin for local project only   只为本地项目安装插件
        --verbose                         Enable verbose output for plugin installation   为插件安装启用详细输出信息
    -h, --help                            Print this help  打印帮助信息
```
例子
```
# Installing a plugin from a known gem source
$ vagrant plugin install my-plugin //指定插件名称

# Installing a plugin from a local file source
$ vagrant plugin install /path/to/my-plugin.gem //指定插件路径
```
如果指定了多个名称，将安装多个插件，给出的标志将应用于当前命令调用所安装的所有插件

 

## Plugin List
格式：
```
vagrant plugin list [-h]
```
列出所有已安装的插件及其各自的已安装版本。如果插件在安装时指定了版本约束，那么约束也会列出。可能还会显示其他插件指定的信息。
```
test-Pro:~ user$ vagrant plugin list -h
Usage: vagrant plugin list [-h]
        --local                      Include local project plugins 包括本地项目的插件
    -h, --help                       Print this help 打印帮助信息
```

 

## Plugin Repair
格式：
```
vagrant plugin repair [-h]
```

vagrant可能无法正确初始化用户安装的自定义插件。这可能是由于我不正确的插件安装/删除，或手动操作像plugins.json的插件相关文件。vagrant可以尝试自动修复问题。
```
test-Pro:~ user$ vagrant plugin repair -h
Usage: vagrant plugin repair [-h]
        --local                      Repair plugins in local project 修复在本地项目的插件
    -h, --help                       Print this help 打印帮助信息
 ```

## Plugin Uninstall
格式：
```
vagrant plugin uninstall <name> [<name2> <name3> ...] [-h]
```
这将卸载具有给定名称的插件。如果没有其他插件需要，插件的任何依赖项也将被卸载。

如果给定多个插件，则将卸载多个插件。
```
test-Pro:~ user$ vagrant plugin uninstall -h
Usage: vagrant plugin uninstall <name> [<name2> <name3> ...] [-h]
        --local                      Remove plugin from local project 移除本地项目的插件
    -h, --help                       Print this help  打印帮助信息
 ```

## Plugin Update
格式：
```
plugin update [names...] [-h]
```
这将更新安装在vagrant中的插件。如果在安装插件时指定了版本约束，则此命令将尊重这些约束。如果你希望更改版本约束，请使用vagrant plugin install重新安装插件。

```
test-Pro:~ user$ vagrant plugin update -h
Usage: vagrant plugin update [names...] [-h]

        --local                      Update plugin in local project 更新在本地项目的插件
    -h, --help                       Print this help 打印帮助信息
```

如果指定了名称，则只更新该插件。如果指定了未安装插件的名称，则此命令不会安装该插件。
