## 用Vscode的Remote-SSH插件连接远程服务器时出现chanel3：open failed...的解决方案

在学校做操作系统实验时，老师让我们试着用vscode连接服务器。但是一直连接不上，按照网上的教程配置了公钥、config文件后还是不能连上。后来发现需要修改服务器端的sshd_config文件才行。

### 解决方案


# 1.连接服务器
博主已经配置过SSH，可以直接用cmd登录。也可以使用puTTY或者服务器自带的vsc登录。
# 2.查看sshd_config代码
使用cat指令查看sshd_config代码:ssh etc/ssh/sshd_config

![图片](https://user-images.githubusercontent.com/80083843/118526289-a9ed7b80-b772-11eb-935a-5cfe5f28da52.png)

拉到最后看看下列几项是不是yes

![图片](https://user-images.githubusercontent.com/80083843/118526506-e325eb80-b772-11eb-9578-cd52bdb16d2d.png)

如果是no的话可以用vim指令进行修改：
vim etc/ssh/sshd_config
输入i进入insert模式
修改对应的代码
esc退出insert模式
输入：wq保存并退出
# 3.重启SSH服务
输入service sshd restart指令，重启服务
![图片](https://user-images.githubusercontent.com/80083843/118527669-161caf00-b774-11eb-8eaa-1204df647490.png)

重启完应该就可以用Vscode的Remote-SSH插件连上服务器了



