取消暂存文件

```shell
git reset HEAD filename.md
```



取消commit提交

```sh
git reset --soft HEAD~1 //退回1个版本，HEAD~2 退回2个版本

```

本地代码推送到已创建的远程仓库

```shell
# 创建版本库
git init
# 连接远程仓库
git remote add origin  git@github.com:bob798/sign-service.git
# 拉取远程代码
git pull origin master
# 添加文件
git add .
# 提交更改
git commit -m "comment"
# 推送当前分支并建立远程上游跟踪
git push --set-upstream origin master
```

仓库帐号配置

```shell
# 查看当前配置
git config --list
# 全局配置
 git config --global user.name "github's Name"
 git config --global user.email "github@xx.com"
 # 单独仓库配置
 git config user.name "gitlab's Name"
 git config user.email "gitlab@xx.com"
```



# 参考

[https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%92%A4%E6%B6%88%E6%93%8D%E4%BD%9C](https://git-scm.com/book/zh/v2/Git-基础-撤消操作)

https://www.jianshu.com/p/952d83fc5bc8