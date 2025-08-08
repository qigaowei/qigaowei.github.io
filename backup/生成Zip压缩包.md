- 如果是文件夹，只需要传文件夹这一个文件到sourceFiles就行
```java
  /**
     *
     * 生成Zip压缩包 (注意是对hutool的二次封装,所以必须要有hutool依赖)
     *
     * @param targetZipFile 要生成的目标zip压缩包
     * @param sourceFiles   压缩包中包含的文件集合
     * @param dirWithFlag   是否将文件目录一同打包进去 (true:压缩包中包含文件目录,false:压缩包中不包含目录)
     */
    public static void generateZip(File targetZipFile, List<File> sourceFiles, boolean dirWithFlag) {
        if (CollUtil.isNotEmpty(sourceFiles)) {
            File[] fileArr = sourceFiles.toArray(new File[]{});
            ZipUtil.zip(targetZipFile, dirWithFlag, fileArr);
        }
    }
```