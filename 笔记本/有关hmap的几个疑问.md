---
typora-root-url: ./images
---



### plugins相关流程

> CocoaPods Plugins 是一个Ruby gem，你需要安装Ruby和CocoaPods来为你的插件开发做准备。

#### 安装

```
gem install cocoapods-plugins
```

#### 创建一个插件

```shell
pod plugins create [plugin_name]
```

插件创建完成后, 打开.gemspec文件如下图所示

![image-20211209175221484](/image-20211209175221484.png)

> 默认情况下，spec.files是指向git仓库并引用其中的文件。但是如果在git仓库中没有文件(还未进行版本控制)时构建gem，您将得到一个空的.gem文件，同时会没有任何警告或错误。我的建议是现在就将spec.files的值设置为Dir[' lib/**/* ']，它将引用lib目录下的所有文件。

#### 本地测试插件, 暂时将spec.files进行修改

```
spec.files = Dir['lib/**/*']
```

关于/\*\* 和 /\*的关系 https://ruby-doc.org/core-1.9.3/Dir.html#method-c-glob 

- `*`

  Matches any file. Can be restricted by other values in the glob. `*` will match all files; `c*` will match all files beginning with `c`; `*c` will match all files ending with `c`; and `*c*` will match all files that have `c` in them (including at the beginning or end). Equivalent to `/ .* /x` in regexp. Note, this will not match Unix-like hidden files (dotfiles). In order to include those in the match results, you must use something like “{*,.*}”.

- `**`

  Matches directories recursively.

#### 根据spec文件 build 出一个gem

```shell
 Summary:
    Build a gem from a gemspec
 Arguments:
    GEMSPEC_FILE  gemspec file name to build a gem for
    
gem build [GEMSPEC_FILE]
```



#### 安装插件

```
GEMNAME ≈ xxx.gem
gem install [GEMNAME]
```

> `gem list --local` 会列出来本地已安装的gem, gem包括pod的插件. pod插件也是gem的一种
>
> `pod plugins installed` 会列出来pod已安装的插件. 可以看做是上面的子集.

