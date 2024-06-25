##批量替换空行
^P^P  replace to ^P

##批量替换指定行
方法：在[替换]对话框的[高级]中：[正则表达式引擎]选UltraEdit。
指定字符 @
%*@*^p replace to 空

##大小写切换
alt+F5  大写
ctrl+F5 小写

##批量替换换行
^r^n replace to 空

## 删除以指定字符开头的行 运行替换src为指定字符
^(?!src).*\r\n