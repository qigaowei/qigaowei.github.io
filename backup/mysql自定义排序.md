```
CREATE TABLE `partner_company` (
  `id` int unsigned NOT NULL AUTO_INCREMENT COMMENT '数据库主键',
  `model_credit_grade` varchar(32) DEFAULT NULL COMMENT '最近一次模型结果信用评级',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2669 DEFAULT CHARSET=utf8mb3;
```
```
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('1', 'AAA');
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('2', 'AA');
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('3', 'A');
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('4', 'BBB');
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('5', 'BB');
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('6', 'B');
INSERT INTO `partner_company` (`id`, `model_credit_grade`) VALUES ('7', NULL);
```
下面sql为null值排最后



```
SELECT
	model_credit_grade
FROM
	partner_company
ORDER BY
	ISNULL(model_credit_grade) || model_credit_grade = '',
	field(
		model_credit_grade,
		'AAA',
		'AA',
		'A',
		'BBB',
		'BB',
		'B',
		''
	)
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/70b4603a5d63459091cb27a51b29d470.png)


	下面sql为null值排最前

```
SELECT
	model_credit_grade
FROM
	partner_company
ORDER BY
	field(
		model_credit_grade,
		'',
		'B',
		'BB',
		'BBB',
		'A',
		'AA',
		'AAA'
	),
	ISNULL(model_credit_grade) || model_credit_grade = ''
```




![在这里插入图片描述](https://img-blog.csdnimg.cn/6be349d2deac436d87c5108608d30179.png)