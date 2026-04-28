```xml
<dependency>
            <groupId>commons-net</groupId>
            <artifactId>commons-net</artifactId>
            <version>3.6</version>
        </dependency>
```

```java
          private static List<String> cidrToIpList(String cidr){
        SubnetUtils utils = new SubnetUtils(cidr);
        String[] adress = utils.getInfo().getAllAddresses();
        return Arrays.asList(adress);
    }
```