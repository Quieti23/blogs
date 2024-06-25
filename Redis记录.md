sh-4.4# redis-cli
#查询redis密码
127.0.0.1:6379> config get requirepass
1) "requirepass"
2) ""
#设置redis密码
127.0.0.1:6379> config set requirepass 123456
OK
127.0.0.1:6379> config get requirepass
(error) NOAUTH Authentication required.
登录验证
127.0.0.1:6379> auth 123456
OK
