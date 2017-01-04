### 单机多git环境下用户名设置

> 用公司的电脑,公司使用的gitlab,自己又在github上提交代码,然后用户名默认是github的,提交公司的代码中git log查看用户名也是github的用户名和邮箱,然后提交被拒绝.


#### 解决方法

+ 1.修改默认git配置为公司的名称和邮箱,毕竟大部分项目都会是公司的项目
  > 下面的命令将修改/home/[username]/.gitconfig文件，也就是说下面的配置只对每一个ssh的用户可见
  
  `git config --global user.name [公司的username]`
  
  `git config --global user.email [公司的email]`

+ 2.达到对应的github项目目录,找到目录下的.git/config文件
   > 增加下面的配置
   
   ```   
   [user]
        name = github用户名
        email = github用户邮箱
    ```
    
##### 这么做达到的目的是默认的项目使用的都是公司的账号和邮箱,指定的github项目使用的github的账号和邮箱.

##### 如果需要配置全局的信息,可以修改/etc/gitconfig文件.