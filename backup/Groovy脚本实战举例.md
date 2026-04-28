1. 解析cURL文本
2. 通过接口获取数据，提取数据
3. 获取jvminfo
```groovy
import cn.hutool.system.*

class AbcScript2 {

    def run() {
        // 获取JVM信息对象
        JvmInfo jvmInfo = new JvmInfo();
       println("JVM名称: " + jvmInfo.toString());
    }
}
return new AbcScript2().run()
```