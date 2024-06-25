根据端口查看进程id
netstat -aon|findstr "49297"

根据进程id查看进程
tasklist|findstr "36104"

根据进程id杀死进程
taskkill /F /PID 23824