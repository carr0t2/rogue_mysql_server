# Rouge Mysql Server

基于 https://github.com/vitessio/vitess 实现的恶意 mysql 服务器, 支持 go, php, python, java, 原生命令行等多种语言的多种库下的恶意 mysql 客户端.  
远离恼人的兼容性问题, 可以定制需要读取的文件等, 测试过的客户端见下表  

language | library | pass |
---     | --- | --- | 
go | github.com/go-sql-driver/mysql | ✔️ | 
php | mysqli, pdo | ✔️ | 
python | pymysql | ✔️ | 
java | mysql-connector-java | ✔️ |
native | 10.4.13-MariaDB | ✔️ |

## 配置文件

示例:
```yaml
lhost: 127.0.0.1
lport: 3306
auth: false
username: root
password: root
filelist: ["/etc/passwd", "C:/boot.ini"]
```
lhost, lport 对应监听的端口和 ip.  
auth 对应是否开启验证, 如果为 false, 那么不管输什么密码或者不输入密码都可以登录.  
如果为 true, 则需要帐号密码匹配下面的 username 和 password.  
而 filelist 对应需要读取的文件, 会按照客户端执行语句的顺序读取列表中的文件, 并保存到 ./loot 中.  

## Ref

https://github.com/vitessio/vitess
https://github.com/src-d/go-mysql-server
http://scz.617.cn:8/network/202001101612.txt