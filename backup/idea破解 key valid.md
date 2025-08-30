https://blog.csdn.net/weixin_41879185/article/details/136156798

＃补丁的绝对路径（可根据你实际的位置进行修改）
javaagent:D:/ja-netfilter/ja-netfilter.jar
＃ 最新IDEA 版本需要添加下面两行，否则会报 key valid
--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED