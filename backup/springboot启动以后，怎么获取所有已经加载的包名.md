```java
  if(Package.getPackages().length>0){
            for (Package pkg : Package.getPackages()) {
                System.out.println(pkg.getName());
            }
        }
```