### gdb常用命令
```
# 打印所有线程调用栈：
thread apply all bt

# 设置日志打印
set logging on
set logging file <log_file_path>
set logging redirect on

# 完成后关闭日志记录
set logging off

# 不中断不打印信号
handle SIGTTIN nostop noprint

# 设置gdb打印变量不会因为过长而用...省略
set print elements unlimited 

# 手动发送SIGINT信号
signal SIGINT

```