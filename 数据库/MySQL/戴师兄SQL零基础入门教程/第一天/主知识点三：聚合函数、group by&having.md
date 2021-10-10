# 主知识点三：聚合函数、group by&having

### 【知识点引入】  

-   我们先来认识最常见的聚合函数  
	-   ![](https://api2.mubu.com/v3/document_image/b177d83e-4777-4d7d-a8f5-18dbae636214-9404487.jpg)  
	-   有时候我们只是需要获取数据的汇总信息，比如说行数啊、平均值啊这种，并不需要吧所有数据都检索出来，只需要使用聚合函数即可  


#### 【函数说明】  
-   `AVG()` 返回某列的均值  
-   `COUNT()` 返回某列的行数  
-   `MAX()` 返回某列的最大值  
-   `MIN()` 返回某列的最小值  
-   `SUM()` 返回某列的和  

 
> **⚠注意聚合函数都会忽略列中的NULL值，但是COUNT(*)也就是统计全部数据的行数，
> 不会忽略NULL值  **

-   我们再来认识两个子句`group by` 和`having` 
	-   【标准语法】  
		```mysql
		select 字段名1  
		from 表格名  
		where 条件代码
		group by 字段名1  
		having 条件代码  
		```
	-   【语法解释】  
		-   之前学到的筛选操作都是基于整个表去进行的，那如果想要依据某列中的不同类别（比如说不同品牌/不同性别等等）进行分类统计时，就要用到数据分组，在SQL中数据分组是使用GROUP BY子句建立  
		-   GROUP BY子句可以包含任意数量的列，因而可以对分组进行多重嵌套，如按照班级和性别进行分组的话，结果中班级A包含男生组和女生组，班级B也包含男生组和女生组  
		-   having 子句和where 子句一样用于条件筛选，两者的操作符一致，但不同的是where是在指定分组前对数据进行筛选过滤，而having可以对分组后的数据进行筛选过滤  
		-   注意写的子句的顺序不可颠倒，需要严格按照语法的顺序！  


#### 【例题讲解】  
-   【聚合函数】  
	-   点击链接[https://sqlzoo.net/wiki/SUM_and_COUNT](https://sqlzoo.net/wiki/SUM_and_COUNT)  

		-   第三题  

			-   【题目】  
				-   从world表中查询非洲（Africa）的总GDP  
			-   要求查询的是所有大洲（continent）为非洲（Africa）的GDP总和  
			-   求和用聚合函数sum，对gdp求和就写select sum(GDP)，可以写上别名gdp总和  
			-   从world表中查询，写from world  
			-   筛选表中大洲（continent）为非洲（Africa）的数据，写where continent = 'Africa'  
			-   【运行代码】  
				-   select sum(GDP) gdp总和  
				-   from world  
				-   where continent = 'Africa'  
			-   【运行结果】  
				-   ![](https://api2.mubu.com/v3/document_image/b3a055f1-7659-47b9-9b41-f0ebf5482ae0-9404487.jpg)  
			-   注意只使用聚合函数不使用group by时是对整张表作聚合运算  
			-   此时select后只能写聚合函数不能添加其他字段名  
		-   第四题  
			-   【题目】  
				-   从world表中查询有多少国家（name）的面积（area）至少有100万  
			-   查询有多少个国家需要进行计数，这里使用count函数  
			-   【运行代码】  
				-   select count(name) 数量  
				-   from world  
				-   where area >= 1000000  
			-   【运行结果】  
				-   ![](https://api2.mubu.com/v3/document_image/adf565b8-733d-4028-989a-37437ef172fb-9404487.jpg)  


-   【group by数据分组】  
	-   点击链接[https://sqlzoo.net/wiki/SUM_and_COUNT](https://sqlzoo.net/wiki/SUM_and_COUNT)第六题  
		-   【题目】  
			-   查询每个大洲（continent）和大洲内的国家（name）数量  
		-   这题需要对数据按照大洲字段分组，我们写出代码group by continent  
		-   并对每组的数据进行计数聚合运算，最后显示每个大洲和大洲中的国家数量，写出代码select continent,count(name)  
		-   对代码进行组合  
		-   【运行代码】  
			-   select continent,count(name)  
			-   from world  
			-   group by continent  
		-   【运行结果】  
			-   ![](https://api2.mubu.com/v3/document_image/5f630bcd-cba0-46a4-9c75-45afa898ec75-9404487.jpg)  
		-   group by 数据分组类似于excel中的数据透视表功能  
			-   【excel数据透视表演示】  
				-   1.![](https://api2.mubu.com/v3/document_image/34629583-9456-45a2-b5ce-e34482bd22de-9404487.jpg)  
				-   2.插入数据透视表![](https://api2.mubu.com/v3/document_image/96a2c163-b863-4e10-adaf-45b22a7c7a4b-9404487.jpg)  
		-   需要注意的是使用group by时，select后的字段只能写group by中出现过的字段和聚合函数，否则就会出现错误  
			-   ![](https://api2.mubu.com/v3/document_image/2da982de-7810-4d09-899c-8447d7e68eda-9404487.jpg)  
-   【having基于聚合运算结果进行筛选】  
	-   点击链接[https://sqlzoo.net/wiki/SUM_and_COUNT](https://sqlzoo.net/wiki/SUM_and_COUNT)第八题  
		-   【题目】  
			-   查询总人口数量至少为1亿（100000000）的大洲  
		-   题目要求对大洲人口数量进行筛选  
		-   首先要对数据进行分组写出代码group by continent  
		-   然后对分组后的数据进行筛选此时使用having  
		-   要对组内的数据人口数量（population）求和进行筛选，写出代码 having sum(population) >100000000  
		-   对代码按正确顺序组合  
		-   【运行代码】  
			-   select continent  
			-   from world  
			-   group by continent 
			-   having sum(population) >100000000  
		-   【运行结果】  
			-   ![](https://api2.mubu.com/v3/document_image/6c29a459-cb3c-498f-a6a4-d106773a1833-9404487.jpg)  


### 【总结】  
-   常用聚合函数  
	-   ![](https://api2.mubu.com/v3/document_image/b177d83e-4777-4d7d-a8f5-18dbae636214-9404487.jpg)  
-   标准语法  
	-   select 字段名1  
	-   from 表格名  
	-   where 条件代码
	-   group by 字段名1  
	-   having 条件代码  
### 【练习题】  
-   【1】[https://sqlzoo.net/wiki/SUM_and_COUNT](https://sqlzoo.net/wiki/SUM_and_COUNT)第五题  
	-   【题目】  
		-   计算Estonia, Latvia, Lithuania这几个国家的总人口数  
		-   ![](https://api2.mubu.com/v3/document_image/7198bc3d-727d-429d-ab72-edbc56cf84e8-9404487.jpg)  
	-   【正确答案】  
		-   select sum(population)  
		-   from world  
		-   where name in ('Estonia', 'Latvia', 'Lithuania')  
-   【2】[https://sqlzoo.net/wiki/SUM_and_COUNT](https://sqlzoo.net/wiki/SUM_and_COUNT)第七题  
	-   【题目】  
		-   查询每个大洲和该大洲里人口数超过1千万的国家的数量  
		-   ![](https://api2.mubu.com/v3/document_image/0cb85c66-2e7e-449f-8867-f3f49d8daefa-9404487.jpg)  
	-   【正确答案】  
		-   select  
		-   continent  
		-   ,count(name) 'number of countries'  
		-   from world  
		-   where population >= 10000000  
		-   group by continent