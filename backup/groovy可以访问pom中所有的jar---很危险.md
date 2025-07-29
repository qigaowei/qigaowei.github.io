示例
1. 读取文件,可以设置权限控制
```groovy
import cn.hutool.core.io.FileUtil

class FileUtil2 {

    def run() {
        def file=FileUtil.readUtf8String("/code/groovy.txt")
        println(file)
    }
}
return new FileUtil2().run()
```
2. 创建线程
```groovy
import cn.hutool.core.thread.ThreadUtil


class AbcScript5 {

    def run() {
        ThreadUtil.execute(() -> {
            println("线程执行的任务");
        });
    }
}
return new AbcScript5().run()
```