shell note 20180816
===================
0. Where there is a shell, there is a way!

1. 以root身份执行上一条命令
```shell
    $ sudo !!
```

2. 回到上一次的目录
```shell
    $ cd -
```

3. 替换前一条命令里面的部分字符
```shell
    ^old^new
    ➜  golanglab git:(master) echo "wanderful"
    wanderful
    ➜  golanglab git:(master) ^a^o
    ➜  golanglab git:(master) echo "wonderful"
    wonderful
```

4. 显示 ascii 表
```shell
    $ man ascii
```

5. 列出本机进程监听的端口号
```shell
    $ netstat -tlnp
```

6. 当 file.log 里面出现 Finished:SUCCESS 时候就退出tail,这个命令用于实时监控并过滤 log 是否出现了某条记录
```shell
    $ tail -f /path/to/file.log | sed '/^Finished:SUCCESS$/ q'
```

7. 在远程服务器上运行一段脚本，这条命令最大的好处就是不用把脚本拷贝到远程服务器
```shell
    $ ssh user@server bash < /path/to/local/script.sh
```

8. 在后台运行一段不终止的程序，并可以随时查看他的状态
```shell
    $ screen -d -m -S some_name ping my_router
    # 更多参考 man screen
```

9. 下载整个 www.example.com 网站
```shell
    $ wget --random-wait -r -p -e robots=off -U mozilla http://www.example.com
```

10. 实时查看本机网络服务的活动状态
```shell
    $ lsof -i
```

11. 用 python 启动一个 HTTP server， 把当前目录设为 HTTP 服务目录，可以通过 http://localhost:8000 访问
```shell
    $ python -m SimpleHTTPServer
```

12. 最常用的十条命令
```shell
    $ history | awk '{CMD[$2]++;count++;} END{for (a in CMD)print CMD[a] "" CMD[a]/count*100 "% " a}' | grep -v "./" | column -c3 -s "" -t | sort -nr | nl | head -n 10
```