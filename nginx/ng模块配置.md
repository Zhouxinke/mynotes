指令合并

- 值指令（可合并）
- 动作类指令（不可合并）



值指令的继承规则：向上覆盖

子配置不存在，用父配置块

子配置存在，直接覆盖父配置块 

listen 监听端口三种方式

- listen address[:port]
- listen port
- listen unix:path



pcretest  测试正则表达式