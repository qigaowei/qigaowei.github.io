1. 空回滚
没用try成功，又需要cancel
解决：需要在业务中做好对空回滚的识别和处理
2. 悬挂
先接到cancel，再接收try，结果一直try
解决：表里有try记录，才能candel
