###Git 使用方法
***

* #####本地生成SSH秘钥
> 查看本地已有ssh秘钥： `cd ~/.ssh` ,若没有则提示未找到文件，有则备份删除 或直接添加<br>
> 生成秘钥 `$ ssh-keygen -t rsa -C "example@gmail.com"`<br>
> 提示输入密码，可自行输入或按回车(密码为空)，最后得到两个文件：id_rsa 和 id_rsa.pub<br>
> 在github添加ssh key ， 将`id_rsa.pub`里的公钥添加到setting -> SSH and GPG keys -> SSH keys


* #####设置Git的User name 和 email
> `$ git config --global user.name "example"`<br>
> `$ git config --global user.email "example@gmail.com"`

* #####测试连通
> `ssh git@github.com`  会提示你是否保持连接 输入 `yes` 即可

* #####获取Git源码
> `$ git clone  SSH地址或HTTPS地址`

* #####提交流程
> 1. 初始化仓库： `git init`<br>
> 2. 添加文件： `git add .` 添加所有修改文件 / `git add 文件名` 添加指定文件<br>
> 3. 提交到本地仓库： `git commit -m "修改备注"` <br>
> 4. 推送更新到远程：`git push origin master` 
> 
> 提示：<br>
> **更新远程到本地**： `git pulll origin master`<br>
> **添加远端repo**： `$ git remote add origin 远程仓库地址`