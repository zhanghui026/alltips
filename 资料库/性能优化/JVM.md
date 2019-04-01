# JVM 最佳参数设置



JVM 启动脚本

```
nohup java -jar build/libs/hallo-hyper-0.0.1-SNAPSHOT.war -Xmx2048m -Xms512m -XX:+UseG1GC -server -d64 -Dfile.encoding=UTF8 -Djava.net.preferIPv4Stack=true -Djava.net.preferIPv6Addresses=false > nohup.out 2>&1 &
```

