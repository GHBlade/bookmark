###Git 使用方法

* #####本地生成SSH秘钥
> 查看本地已有ssh秘钥： cd ~/.ssh ,若没有则提示未找到文件，有则备份删除 或直接添加<br>
> 生成秘钥 $ ssh-keygen -t rsa -C "example@gmail.com"


* #####设置Git的User name 和 email
> `$ git config --global user.name "example"`<br>
> `$ git config --global user.email "example@gmail.com"`