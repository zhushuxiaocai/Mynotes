# 云平台部署(最简单)

### 本篇来源于 51CTO , 原文链接 : `https://blog.51cto.com/u_16213596/10305651` , 作者: mob64ca13fb6939 

Centos7.5最小化安装后基础环境
```
配置 IP GTEWAY DNS ,配置 yum 源 上传软件包 Centos-7.repo 替换 CentOS-Base.repo 或 curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
```
> 1. 安装管理软件 此处选择 宝塔
>> - `yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh` 
>> - 保存登录地址 用户名 密码
> 2. 开放相关端口
>> - `firewall-cmd --zone=public --add-port=8888/tcp --permanent` 
>> - 查看开放端口 `firewall-cmd --list-ports`
> 3. 登录后绑定宝塔账号 , 自动跳出的窗口提示安装网站运行环境 , 选择 LNMP极速安装 , 等待...
> 4. 网站搭建程序选择 WordPress ,  [通过此链接跳转至WordPress官网](https://cn.wordpress.org/download/)。
> > - 点击网站->添加站点 , 域名: 192.168.100.10 , 数据库: MySQL , 数据库名与账号一致: 192_168_100_10 , 密码: Pj33W4ZtdG319BHD
```
可能会报 `/www/server/nginx/sbin/nginx: error while loading shared libraries: libluajit-5.1.so.2: cannot open shared object file: No such file or directory`
这个错误是因为Nginx需要的共享库文件 `libluajit-5.1.so.2` 丢失或未安装 , 安装 luajit 提供缺失的库文件 , yum install luajit -y , 但是安装后可能会报 符号查找 错误
出现 符号查找 错误不建议继续 , 重头再来
```
> > - 点击文件->192.168.100.10 , 上传 WordPress 压缩包内文件
> > - 访问 http://192.168.100.10 , 进入安装页面 ,  保存登录信息 zz gfn(Rb2Y!pepCOxph^ 
 

