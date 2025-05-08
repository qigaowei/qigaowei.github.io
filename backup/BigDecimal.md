1. BigDecimal有个精度字段
   equals会比较精度，0.1和0.10不相等，compare是相等的
   new BigDecimal("0.1")不精准
2. toString是科学计算法