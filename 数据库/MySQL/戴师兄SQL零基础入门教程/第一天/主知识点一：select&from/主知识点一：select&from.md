# 主知识点一：select&from

## [[【标准语法】]]

-   `select`
	-    字段名  
-   `from`
	-    表名称  

## [[【语法解释】]]
-   `select` 
	-   字段名
		-    表明选择查询表格中的哪几列进行查看  
-   `from`
	-    表格名 
		-    表明你查询的数据来自哪一个数据库表  

## [[【例题讲解】]]
-   【基础查询select单列&多列&所有列&别名应用】  
	-   我们点开链接[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第一题  

### 【题目】  
-   阅读关于表格的信息，观察SQL代码并运行  
-   我们先观察我们要查询的表格中的表头，知道每个列名称，再查看表格前几行数据知道每一行和每一列数据的大致内容  
	-   ![](https://api2.mubu.com/v3/document_image/2a62d212-b6ea-43fb-8b93-185a6d25301d-9404487.jpg)  
-   观察题目给我们的代码  
	-   ![](https://api2.mubu.com/v3/document_image/236ad1d4-5b1d-4bb5-99be-ae9bf96a8615-9404487.jpg) 
	-   由刚才我们所学的select 和from组成，select后有多个字段名，表明这段代码查询的是多列数据，字段顺序按照select后所写的字段顺序依次展现，注意逗号是在英文输入法下输入的  
	-   select name, continent, population from world表明要查询名为 "name" 、 "continent" 和"population"的列的内容从名为world的数据库表中，同时记住SQL对大小写不敏感SELECT和select完全等效，但是为了书写效率，成熟的分析师一般都用小写  
	-   点击运行代码  
		-   得到结果![](https://api2.mubu.com/v3/document_image/4d15ee45-db8c-4da6-9cd0-8ffdad1484fd-9404487.jpg)  
-   将所有列名称变更为单一的*：`SELECT * FROM world `` 
	-   运行代码，得到表格的所有列，所以通配符*是选取所有列的快捷方式![](https://api2.mubu.com/v3/document_image/20b312be-f9b7-42a5-af1c-b8e8b080bda6-9404487.jpg)  
-   在select中还可以为字段名指定别名  
	-   在select的字段名或者from的表格名后加 [as 别名]，即可为字段名起个别名，也可以省略as，但是记得字段名和表格名后的别名要用空格隔开  
	-   select name as 国家名, continent 大洲, population 人口 from world![](https://api2.mubu.com/v3/document_image/c41dd9e4-9b21-4126-b968-ea3952b4ab29-9404487.jpg)  
-   【select中distinct去重】  
	-   select中还可以加distinct对重复的行数据进行去重，我们点开链接（distinct去重）[https://sqlzoo.net/wiki/SUM_and_COUNT](https://sqlzoo.net/wiki/SUM_and_COUNT)第二题  
		-   【阅读题目】  
			-   列出所有大洲（continent），且仅出现一次  
		-   如果运行代码select continent from world，就会发现大洲多次出现在查询结果里，这不是我们所要的答案  
			-   ![](https://api2.mubu.com/v3/document_image/3a9cac3d-734c-4138-9128-3e06271c9990-9404487.jpg)  
		-   在select后加入distinct对重复的数据去重  
			-   运行代码select distinct continent from world得到去重后的数据![](https://api2.mubu.com/v3/document_image/8c82ff25-cd4c-4107-9602-b927bcfe826f-9404487.jpg)  
			-   如果select distinct后有多个字段名时，是对重复的行数据进行去重  
				-   运行select distinct continent,name from world![](https://api2.mubu.com/v3/document_image/93a0f906-d491-4668-90d4-abff7faa976f-9404487.jpg)  
			-   注意distinct在select中使用时，只能加在select后而不是字段名前  
				-   所以大家如果这样写：select continent,distinct name from world，就会出现语法错误![](https://api2.mubu.com/v3/document_image/d1e6c53f-2204-4690-bfb0-66f336a3bc04-9404487.jpg)  
-   【select中计算字段的运用】  
	-   select中还可以直接进行计算，我们点击链接[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第三题  
		-   【题目】  
			-   查询人口数至少2亿的国家名和人均GDP  
		-   人均GDP该如何计算呢？这里有给出公式：人均GDP = GDP/population  
		-   可见人均GDP无法从数据库表world中直接得到，需要进行计算，而这个新的字段人均GDP由数据库表中的两个字段GDP和population计算得到，因此我们在select后写算式GDP/population构建计算字段  
		-   运行代码  
			-   select name,GDP/population 人均gdp from world![](https://api2.mubu.com/v3/document_image/b2719241-e292-4080-a7be-4b450271d837-9404487.jpg)  
			-   此时每行数据的GDP和population相除，生成我们所需的新字段人均gdp，我们还可以对计算字段添加别名人均gdp  


## [[【总结】]]
-   基础语法  
	-   select 字段名 from 表名称  
-   别名语法  
	-   select 字段名 as 别名 from 表名称  
	-   注意：as可以省略  
-   查询多列  
	-   select 字段名1, 字段名2, 字段名3 from 表名称  
-   查询所有列  
	-   select * from 表名称  
-   数据去重  
	-   select distinct 字段名 from 表名称  
-   select中的计算字段  
	-   select 字段名,计算字段 from 表名称  
	-   注意：计算字段中的算式所涉及的 字段名必须是表格中包含的，或者算式本身可以独立运算