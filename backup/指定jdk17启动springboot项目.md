创建一个如下的shell脚本
```
#!/bin/bash

export JAVA_HOME=/usr/local/jdk-17.0.8/
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=.:${JAVA_HOME}/bin:$PATH

nohup java -jar chatgpt-0.0.1-SNAPSHOT.jar > /dev/null 2>&1 &
```
