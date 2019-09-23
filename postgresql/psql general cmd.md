# 建立数据库连接
##  psql -h host地址 -p 端口 -d 数据库 -U 连接用户名
##  回车后会要求输入数据库密码
# 访问数据库
##  psql 的命令都是以斜杠 "\\" 开头的。
### \l
####  列出数据库
### \c[onnect] {[DBNAME|- USER|- HOST|- PORT|-] | conninfo}
####  连接到新数据库
### \dt
####  列出表
### \d 表名
####  查看某个库中某个表结构
### \d 索引名
####  显示某索引信息
### \d+
#### 将显示比 \d 更详细的信息，还会显示任何与表关系的注释
### \di
####  列出索引
### \ds
####  列出序列
### \dv
####  列出视图
### \df
####  列出函数
### \dn
####  列出模式schema
### \du或\dg
####  列出用户和角色
### \db
####  列出表空间
### \dx
####  列出已安装的扩展
### \dT
####  列出类型
### \dp或\z [模式]
####  列出表, 视图, 序列的访问权限
### \encoding
####  显示客户端字符集编码
### \encoding 字符集编码名
####  指定客户端字符集编码
### \timing on|off
####  显示SQL已执行的时间，默认是off
### \conninfo
#### 显示当前连接的相关信息
### \password
####  更改用户口令
### \x [on|off|auto]
####  切换扩展输出模式，默认是off
### \h [command]
####  SQL命令语法上的说明，用*显示全部命令的语法说明

### 更多的命令可以用 \? 来显示
####  一般性
####  \copyright            显示PostgreSQL的使用和发行许可条款
####  \crosstabview [COLUMNS] 执行查询并且以交叉表显示结果
####  \errverbose            以最冗长的形式显示最近的错误消息
####  \g [文件] or;     执行查询 (并把结果写入文件或 |管道)
####  \gexec                 执行策略，然后执行其结果中的每个值
####  \gset [PREFIX]     执行查询并把结果存到psql变量中
####  \gx [FILE]             as \g, but forces expanded output mode
####  \q             退出 psql
####  \watch [SEC]          每隔SEC秒执行一次查询

####  帮助
####  \? [commands]          显示反斜线命令的帮助
####  \? options             显示 psql 命令行选项的帮助
####  \? variables           显示特殊变量的帮助
####  \h [名称]          SQL命令语法上的说明，用*显示全部命令的语法说明

####  查询缓存区
####  \e [FILE] [LINE]        使用外部编辑器编辑查询缓存区(或文件)
####  \ef [FUNCNAME [LINE]]   使用外部编辑器编辑函数定义
####  \ev [VIEWNAME [LINE]]  用外部编辑器编辑视图定义
####  \p                    显示查询缓存区的内容
####  \r                    重置(清除)查询缓存区
####  \w 文件          将查询缓存区的内容写入文件

####  输入/输出
####  \copy ...             执行 SQL COPY，将数据流发送到客户端主机
####  \echo [字符串]       将字符串写到标准输出
####  \i 文件          从文件中执行命令
####  \ir FILE               与 \i类似, 但是相对于当前脚本的位置
####  \o [文件]        将全部查询结果写入文件或 |管道
####  \qecho [字符串]      将字符串写到查询输出串流(参考 \o)

####  Conditional
####  \if EXPR               begin conditional block
####  \elif EXPR             alternative within current conditional block
####  \else                  final alternative within current conditional block
####  \endif                 end conditional block

####  资讯性
####  (选项: S = 显示系统对象, += 其余的详细信息)
####  \d[S + ]          列出表, 视图和序列
####  \d[S + ]  名称      描述表，视图，序列，或索引
####  \da[S][模式]    列出聚合函数
####  \dA[+][PATTERN]      list access methods
####  \db[+][模式]     列出表空间
####  \dc[S + ][PATTERN]      列表转换
####  \dC[+][PATTERN]      列出类型强制转换
####  \dd[S][PATTERN]      显示没有在别处显示的对象描述
####  \dD[S + ][PATTERN]      列出共同值域
####  \ddp[模式]    列出默认权限
####  \dE[S + ][PATTERN]      列出引用表
####  \det[+][PATTERN]      列出引用表
####  \des[+][模式]    列出外部服务器
####  \deu[+][模式]     列出用户映射
####  \dew[+][模式]       列出外部数据封装器
####  \df[antw][S + ][模式]    列出[只包括 聚合 / 常规 / 触发器 / 窗口]函数
####  \dF[+][模式]   列出文本搜索配置
####  \dFd[+][模式]     列出文本搜索字典
####  \dFp[+][模式]     列出文本搜索解析器
####  \dFt[+][模式]   列出文本搜索模版
####  \dg[S + ][PATTERN]      列出角色
####  \di[S + ][模式]  列出索引
####  \dl                   列出大对象， 功能与\lo_list相同
####  \dL[S + ][PATTERN]      列出所有过程语言
####  \dm[S + ][PATTERN]      列出所有物化视图
####  \dn[S + ][PATTERN]     列出所有模式
####  \do[S][模式]   列出运算符
####  \dO[S + ][PATTERN]      列出所有校对规则
####  \dp[模式]     列出表，视图和序列的访问权限
####  \drds[模式1[模式2]] 列出每个数据库的角色设置
####  \dRp[+][PATTERN]      list replication publications
####  \dRs[+][PATTERN]      list replication subscriptions
####  \ds[S + ][模式]    列出序列
####  \dt[S + ][模式]     列出表
####  \dT[S + ][模式]  列出数据类型
####  \du[S + ][PATTERN]      列出角色
####  \dv[S + ][模式]   列出视图
####  \dx[+][PATTERN]      列出扩展
####  \dy[PATTERN]      列出所有事件触发器
####  \l[+][PATTERN]      列出所有数据库
####  \sf[+]  FUNCNAME       显示一个函数的定义
####  \sv[+]  VIEWNAME       显示一个视图的定义
####  \z[模式]    和\dp的功能相同
	  
####  格式化
####  \a                  在非对齐模式和对齐模式之间切换
####  \C[字符串]        设置表的标题，或如果没有的标题就取消
####  \f[字符串]         显示或设定非对齐模式查询输出的字段分隔符
####  \H                    切换HTML输出模式(目前是 关闭)
####  \pset[NAME[VALUE]]   set table output option
####  (NAME : = { border | columns | expanded | fieldsep | fieldsep_zero |
####  footer | format | linestyle | null | numericlocale | pager |
####  pager_min_lines | recordsep | recordsep_zero | tableattr | title |
####  tuples_only | unicode_border_linestyle |
####  unicode_column_linestyle | unicode_header_linestyle })
####  \t[开 | 关]       只显示记录(目前是 关闭)
####  \T[字符串]         设置HTML <表格>标签属性, 或者如果没有的话取消设置
####  \x[on | off | auto]       切换扩展输出模式(目前是 关闭)
	  
####  连接
####  \c[onnect]{ [DBNAME | -USER | -HOST | -PORT | -] | conninfo }
####  连接到新数据库（当前是"postgres"）
####  \conninfo              显示当前连接的相关信息
####  \encoding[编码名称] 显示或设定客户端编码
####  \password[USERNAME]  安全地为用户更改口令
	  
####  操作系统
####  \cd[目录]     更改目前的工作目录
####  \setenv NAME[VALUE]   设置或清空环境变量
####  \timing[开 | 关]       切换命令计时开关(目前是 关闭)
####  \![命令]      在 shell中执行命令或启动一个交互式shell
	  
####  变量
####  \prompt[文本] 名称 提示用户设定内部变量
####  \set[名称[值数]] 设定内部变量，若无参数则列出全部变量
####  \unset 名称    清空(删除)内部变量
	  
####  大对象
####  \lo_export LOBOID 文件
####  \lo_import 文件[注释]
####  \lo_list
####  \lo_unlink LOBOID   大对象运算

