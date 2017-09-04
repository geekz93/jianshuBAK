crontab 在执行脚本的时候不带环境变量, 因此需要在脚本中自行添加, 才能保证脚本正确运行
例子: crontab 设置: 每周五早上 7 点 03 分导出 awr 报告
```
3 7 * * 5 echo `date`>>/home0/nmcuser/awr_report/crontab.log;/home0/nmcuser/export_awr.sh
```
运行后: crontab.log 可以生成, 但是报告没导出
一下是 export_awr.sh 的内容:
