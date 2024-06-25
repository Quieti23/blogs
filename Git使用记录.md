代理使用：
git config --global http.proxy http://127.0.0.1:10809
取消代理：
git config --global --unset http.proxy
查看代理
git config --global https.proxy
删除代理
npm config delete proxy

取消当前拉取：
PS D:\project\dataexchange-center> git reflog
975b643 (HEAD -> develop) HEAD@{0}: commit: Revert "bug: http连接器ssl证书修改不生效"
4c0400e HEAD@{1}: reset: moving to HEAD~
3936f4f HEAD@{2}: commit: Revert "bug: http连接器ssl证书修改不生效"
4c0400e HEAD@{3}: reset: moving to HEAD~
f5b25bf HEAD@{4}: commit: Revert "bug: http连接器ssl证书修改不生效"
4c0400e HEAD@{5}: commit: 72807d9: 2fc0bb4: bug: 导出接口文档响应修改
72807d9 HEAD@{6}: commit: 2fc0bb4: bug: 导出接口文档响应修改
2fc0bb4 HEAD@{7}: commit: bug: 导出接口文档响应修改
140dfd2 HEAD@{8}: commit: bug【文件转换节点】base64转文件失败
69170e9 HEAD@{9}: commit: 11
0b14671 HEAD@{10}: commit: bug:【文件转换节点】生成api文档响应不应为空
28014a0 HEAD@{11}: revert: Revert "1"
a43a0e4 HEAD@{12}: pull --tags origin develop: Fast-forward
b02d5ef HEAD@{13}: reset: moving to HEAD~
a43a0e4 HEAD@{14}: commit: 1
b02d5ef HEAD@{15}: merge dev_固化材料需求2: Merge made by the 'recursive' strategy.
0592391 HEAD@{16}: checkout: moving from dev_固化材料需求2 to develop
333de3c (origin/dev_固化材料需求2, dev_固化材料需求2) HEAD@{17}: commit: bug:【文件转换节点】base64转文件失败
9a155c1 HEAD@{18}: checkout: moving from dev_增加是否带默认前缀开关 to dev_固化材料需求2
6e1a531 (dev_增加是否带默认前缀开关) HEAD@{19}: commit: 1
78d257c HEAD@{20}: pull --tags origin develop: Merge made by the 'recursive' strategy.
PS D:\project\dataexchange-center> git reset-hard 3936f4f

错误1：
remote: Counting objects: 100% (1/1), done.
error: RPC failed; result=18, HTTP code = 200 | 33.00 KiB/s
fatal: The remote end hung up unexpectedly
fatal: early EOF

解决1：
git config --global http.postBuffer 1024288000
git config --list

ssh-keygen  生成公私密钥

关键字 in:name readme 
关键字 stars:>=5000
关键字 forks:>=5000

学习资料：
awesome 关键字

#L13 高亮显示13行
#L13-23 高亮显示13-23行

项目内搜索 t

搜索某区域  活跃用户
location:beijing language:java