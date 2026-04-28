```groovy
import groovy.util.logging.Slf4j

@Slf4j
class FileUtil3 {
 
    def run() {
         log.info "准备删除文件: {}"
		 log.warn "文件不存在，无需删除"
		 log.error "文件不存在，无需删除2"
    }
}
return new FileUtil3().run()
```