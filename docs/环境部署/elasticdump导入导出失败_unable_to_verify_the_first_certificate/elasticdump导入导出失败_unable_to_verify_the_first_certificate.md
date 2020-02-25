##问题现象
执行elasticdump时导入失败。详细报错如下：
elasticdump --input=https://x.x.x.x:9200/xxxx(indices) --output=xxxx(indices).json --type=data --httpAuthFile=pwd.ini
Fri, 21 Feb 2020 09:14:43 GMT | starting dump
Fri, 21 Feb 2020 09:14:43 GMT | Error Emitted => unable to verify the first certificate
Fri, 21 Feb 2020 09:14:43 GMT | Error Emitted => unable to verify the first certificate
Fri, 21 Feb 2020 09:14:43 GMT | Total Writes: 0
Fri, 21 Feb 2020 09:14:43 GMT | dump ended with error (get phase) => Error: unable to verify the first certificate

##命令解释
xxxx(indices) 表示索引名字
xxxx(indices).json 表示导出的文件名，可以加绝对路径
--httpAuthFile=pwd.ini 表示使用pwd.ini文件进行验证，文件的格式为：
user=用户名
password=密码

##问题原因
查资料后发现时因为拒绝了未认证的证书。

##解决方案
export NODE_TLS_REJECT_UNAUTHORIZED=0
设置环境变量NODE_TLS_REJECT_UNAUTHORIZED=0，即"不拒绝未认证的证书"

<font color="#dd0000">注：直接修改系统环境变量比较危险，因为会影响到所有的程序，建议把这个操作放到脚本中执行</font>
<font color="#dd0000">注：直接修改系统环境变量比较危险，因为会影响到所有的程序，建议把这个操作放到脚本中执行</font>
<font color="#dd0000">注：直接修改系统环境变量比较危险，因为会影响到所有的程序，建议把这个操作放到脚本中执行</font>
