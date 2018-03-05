## npm 私有库

### 说明

基于开源项目[sinopia](https://github.com/rlidwka/sinopia)搭建的公司内部使用的npm仓库

### 功能

sinopia以文件系统为基础，提供了简单的`npm publish`和`npm login`等基本命令的处理流程，但整体不是很完善，部分功能也存在逻辑问题，对其进行了完善和添加了以下功能，使其更能满足公司的规范和便捷实用。

* 完善了私有库的权限控制和每个模块的权限控制。 

 ![1.png](./img/1.png =800x100)

* 提供快捷的版本回退和模块删除操作。  

![2.png](./img/2.png =800x100)
![3.png](./img/3.png =300x150) ![4.png](./img/4.png =300x150)
 
* 搭配gitlab的CI持续集成，实现模块自动发布和更新到私有库中。 

![5.png](./img/5.png =300x300)

* 提供数据恢复功能。应对私有库服务器出现数据丢失问题，或者方便重新部署时同步数据。

### 其他

* 对内部模块的名字进行了约定，添加了命名空间前缀，npm配置中将命名空间指向到私有库服务器地址，从而只存储公司内部的私有模块，公用的第三方模块还是从淘宝源上安装。
* 构建了包含私有库运行的代码和整套环境的docker镜像（代码，pm2,npm,node,gitlab CI注册）,满足一键部署的要求
