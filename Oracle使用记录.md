 sqlplus BORS/BORS_123@"(DESCRIPTION = (LOAD_BALANCE = OFF) (FAILOVER = ON) (ADDRESS_LIST = (ADDRESS = (PROTOCOL = TCP)(HOST = 135.10.55.58)(PORT = 1521)) (ADDRESS = (PROTOCOL = TCP)(HOST = 135.10.55.57)(PORT = 1521)) ) (CONNECT_DATA = (SERVER = DEDICATED) (SERVICE_NAME = JYCBOSS) (FAILOVER_MODE=(TYPE=SESSION)(METHOD=BASIC)(RETRIES = 4)(DELAY = 1)) ) ) " 
sqlplus 'ADMP/"Admp_@123!"'@//135.10.118.52:1521/pdbbomc1

2. 代码大小：USER_OBJECT_SIZE

可以从USER_OBJECT_SIZE 数据字典视图中查询过程对象在SYSTEM表空间中所使用的空间量。如下列程序清单所示，可以将4 个不同大小的区域累加起来，确定在SYSTEM 数据字典表中存储对象所用的总空间。这4 个Size 列与Name 列和Type 列一起构成了该视图的所有列。

select Source_Size+Code_Size+Parsed_Size+Error_Size Total  
from USER_OBJECT_SIZE  
where Name = '&procedure_name' 
and Type = 'PROCEDURE'; 
该视图还有一个可用的“DBA”版本，DBA_OBJECT_SIZE 视图列出了数据库中所有对象的大小。

总的CPU花费在执行及解析上的比率

l         Parse CPU to total CPU ratio：该项显示总的CPU花费在执行及解析上的比率。如果这项比率较低，说明系统执行了太多的解析。

公式：1 - (parse time cpu / CPU used by this session)

执行：

select 1-(a.value/b.value)

 from v$sysstat a,v$sysstat b

 where a.name='parse time cpu' and

         b.name='CPU used by this session';

表记录更新：

SELECT ID,NAME,VERSIONS_STARTTIME,VERSIONS_ENDTIME,VERSIONS_OPERATION FROM TEST a VERSIONS BETWEEN TIMESTAMP MINVALUE AND MAXVALUE WHERE VERSIONS_STARTTIME IS NOT NULL ORDER BY VERSIONS_STARTTIME DESC;


表空间:

        代码改动DBCollectorTaskRunne.java  relatedKpi 行数335 337 370