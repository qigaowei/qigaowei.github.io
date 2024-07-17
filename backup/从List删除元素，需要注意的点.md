```java
     List<String> list=new ArrayList<String>();
        list.add("1");
        list.add("2");
        list.add("3");
        list.add("4");
        for(String str : list){
            if("3".equals(str)){
                list.remove(str);
            }
            System.out.println(str);//代表业务逻辑
        }
        System.out.println();
        for(String str : list){
            System.out.println(str);
        }
```
结果如下，第一个for循环，4没有打印出来需要注意
1
2
3

1
2
4
