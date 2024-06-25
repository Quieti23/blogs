查找linux下中最大文件
 du -Sh / | sort -rh | head -n10 


查看当前运行发行版本
wsl -u root
wsl -l -v  

linux  开放指定端口 ： /sbin/iptables -I INPUT -p tcp --dport 10001 -j ACCEPT
在/etc/sysconfig/iptables文件中添加

#开放本服务器的232端口对所有访问者

-A INPUT -m state --state NEW -m tcp -p tcp --dport 232 -j ACCEPT
#发放本服务器的1521端口 对172.17.45/24网段的访问者

-A INPUT -s 172.17.45.0/24 -m state --state NEW -m tcp -p tcp --dport 1521 -j ACCEPT

最后一行的所有列:awk 'END{print}' messages.log
输出第一行 :ps -ef | awk 'NR==1'

find / | xargs grep function

BusiDemandMessageJob


find /home -iname "*.txt"
查找大于1G的文件
find / -type f -size +1G

批量杀进程:
ps -ef|grep moni|grep -v grep|awk  '{print "kill -9 " $2}' |sh

脚本中grep匹配中文  有问题  不可用   需使用awk命令
awk '{if(index($0, busname) !=0){print $0}}' busname=$BUSINAME

查看端口
netstat -ntlp

netstat -ano 3306|awk '{if($1=="tcp") print $0}'
-- 分组统计uniq -c
cat mysql.log|awk '{print $5}'|awk -F: '{print $1}'|sort|uniq -c

-- 根据端口状态分组统计各状态数量
netstat -an|awk '/tcp/ {print $6}'|sort|uniq -c

-- 查看Linux主机防火墙状态 
firewall-cmd --state

cat io.tmp | awk 'BEGIN{a="1"}{printf("%s\t",a);for(i=1;i<=NF;i++){printf($i);printf("\t")}printf("%s","\n")}'

tar -xzvf conf.tar.gz 解压

tar -czvf conf.tar.gz conf压缩

打包文件(排除文件及目录)
tar -zPcvf admp_155_20191202.tar.gz /home/aidmp/* 
	--exclude=/home/aidmp/admpTest/server/tomcat_develop/logs 
	--exclude=/home/aidmp/admpTest/logs  
	--exclude=/home/aidmp/logs 
	--exclude=/home/aidmp/admp.tar.gz 
	--exclude=/home/aidmp/server/tomcat_develop/logs 
	--exclude=/home/aidmp/patch/*.tar 
	--exclude=/home/aidmp/patch/*.zip 
	--exclude=/home/aidmp/suozz  &

sysm.checker.isSystemTime

mkdir fileName 新建文件

du -h /data/toptea/ --max-depth=1   磁盘占用最大

cat /dev/null > filename 清空文件

df -h  查看磁盘使用情况
du -sh * 查看当前目录各文件大小

删除文件后缀：sed 's/\.sh//'
删除空行：sed '/^$/d'

 netstat -an |grep 14337    查看端口被哪些IP占用
netstat -tunlp|grep port 根据端口查找进程号：


1、grep -r "查询内容"  文件目录    #这样查询出来的包括文件名+内容

        grep -r -l   "查询内容"  文件目录   #这样只显示包含内容的文件名

    2、find 文件目录  -type f |xargs grep "查询内容";   #也可以达到效果


chmod -R g+rx memdb/ 同一组的用户加rx权限：

active活动的ThreadPool:
echo status -l | nc -i 1 135.10.106.27 20881|grep threadpool |awk '{print $11}'|awk -F':' '{print $2}'|awk '{sub(/,/," ",$1);print}'

grep -E '123|abc' filename  // 找出文件（filename）中包含123或者包含abc的行



cat test|awk -F\; '{print $5}'|awk -F@ '{sum+=$1}'END'{print sum}'

