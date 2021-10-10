# 主知识点二：where

### 【知识点引入】  
-   我们来认识第三个子句where，where子句写在from之后  
	-   【标准语法】  
		-   select 字段名  
		-   from 表格名  
		-   where 条件代码  
	-   【语法解释】  
		-   where 条件代码 表明从数据库表中选取满足条件的数据  
-   where子句主要用来进行数据的筛选，从表格中筛选出符合条件的行数据  
-   接下来让我们来快速应用where子句吧~  


### 【例题讲解】  
- 【运算符】  
	-   条件代码中最常用的是运算符。  
		-   运算符查询标准语法  
			-   `select` 字段名  
			-   `from` 表名称  
			-   `where` 字段名 运算符 值  
	-   先来看这个表格，比较运算符，用于判断表中的哪些数据符合条件，and、or和not为逻辑运算符，not一般和与其他连用例如not in等。![](https://api2.mubu.com/v3/document_image/f386d31c-876c-4fbd-aa07-16a0f36b006d-9404487.jpg)  
	-   and 和 or 可以把两个或多个条件结合起来。若and连接的两个条件对于该数据都成立，就显示该数据，若or连接的两个条件对于该数据只要有一个成立，就显示该数据，否则就筛除该数据。  


####  点击链接[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第三题  
-   【题目】  
	-   查询人口数至少2亿的国家名和人均GDP  
-   人均GDP如何查询我们已经在前面讲过了，这里就不再赘述了。这里着重看的是“人口数至少2亿”这个条件，说人话就是人口population大于等于两亿，写成代码语言就是population>=200000000,并写在where子句后，与select和from子句组合在一起得到正确代码  
-   【运行代码】  
	```mysql
		-   select name,GDP/population 人均gdp  
		-   from world  
		-   where population>=200000000  
	```
-   【运行结果】  
	-   ![](https://api2.mubu.com/v3/document_image/9066f852-4758-4c2a-b770-c1040fbbe203-9404487.jpg)![](https://api2.mubu.com/v3/document_image/2c4533b7-9c1e-42c1-820d-deb0ab3e900c-9404487.jpg)  
-   点击链接[https://sqlzoo.net/wiki/SELECT_basics](https://sqlzoo.net/wiki/SELECT_basics)  
	-   看第一题  
		-   【题目】  
			-   修改代码查询德国（Germany）人口数量  
		-   我们把题目给的代码中的France改成Germany  
		-   注意在France外的单引号不要删除，所有的字符串都要用单引号包裹，与不用单引号包裹的字段名、表名和语法作区分，如果字符串仅有数字可以省略单引号 
		-   同时也要注意单引号是在英文输入法下输入的和逗号一样，不然就会出现语法错误  
		-   运行代码  
		```mysql
		SELECT population  
		FROM world  
		WHERE name = 'Germany'!
		 ```
		-   [](https://api2.mubu.com/v3/document_image/150e16d6-8256-41ca-b038-810cafa13cc5-9404487.jpg)  
	-   看第二题，了解in的用法  
		-   ![](https://api2.mubu.com/v3/document_image/93a68d48-c6ce-4728-8d23-090db7e857f5-9404487.jpg)![](https://api2.mubu.com/v3/document_image/a1ac9be6-f75f-47be-a3f6-0e338af25269-9404487.jpg)  
		-   in会筛选出字段中所有与括号内数据相等的行  
		-   在这题中in筛选的是名为name的这列字段中值等于Brazil, Russia, India, China的行  
	-   看第三题，了解between...and...的用法  
		-   ![](https://api2.mubu.com/v3/document_image/ea088dc1-f3a1-49ae-ad67-cf25cbabb096-9404487.jpg)![](https://api2.mubu.com/v3/document_image/759d0c73-dcb0-4f1b-a04d-68ca45562bf6-9404487.jpg)  
		-   between and选取介于两个值之间且包含这两个值的数据范围，这些值可以是数值或者日期  
		-   在这题中between and筛选出面积area字段的值在25万和30万之间的行  
-   【模糊查询like】  
	-   条件代码中除了使用运算符来进行条件判断，还可以使用like操作符组合通配符进行模糊查询  
		-   模糊查询标准语法  
			-   select 字段名 
			-   from 表格名  
			-   where 字段名 like '通配符+字符'  
		-   通配符用来匹配值的一部分，跟在LIKE关键字后面进行数据过滤常用的通配符有%和_，%用来匹配多个字符可以是零个、一个也可以是多个字符，_仅能用来匹配单个字符  
			-   ![](https://api2.mubu.com/v3/document_image/5714f438-11a2-482c-8071-de8290bf562b-9404487.jpg)  
		-   点击链接[https://sqlzoo.net/wiki/SELECT_names](https://sqlzoo.net/wiki/SELECT_names)  
			-   看第五题  
				-   【题目】  
					-   查询国家名name字段中以C开头ia结尾的国家  
				-   由于C和ia之间没有限定字符数，所以我们使用%通配符  
				-   写成代码就是where name like 'C%ia'  
				-   运行正确代码  
					-   SELECT name 
					-   FROM world  
					-   WHERE name LIKE 'C%ia'![](https://api2.mubu.com/v3/document_image/4dab53c7-4422-4a41-a888-ae68d3342414-9404487.jpg)  
			-   看第八题  
				-   【题目】  
					-   查询国家名name中第二个字符为't'的国家  
				-   指定第二个字符为t，此时使用_通配符，但未指定字符t后的字符数因此用%  
				-   写成代码 where name like '_t%'  
				-   运行代码  
					-   SELECT name  
					-   FROM world  
					-   WHERE name LIKE '_t%'![](https://api2.mubu.com/v3/document_image/0904efdd-6203-4e15-8c8f-5f595ed5e6e6-9404487.jpg)  
			-   看第九题  
				-   【题目】  
					-   查询国家名name中含有两个o且被两个字符隔开的国家名  
				-   题目指定有两个o且被两个字符隔开，这两个字符用两个_进行匹配而不能用%，因为_仅指代一个字符，不能没有也不能是两个，而%匹配数量不定的字符，可能没有也可能有二三四五六个  
				-   这里题目只指明两个o之间有两个字符但没有指明两个o前或者后有多少个字符  
				-   因此写成代码where name like '%o__o%'  
				-   运行代码  
					-   SELECT name  
					-   FROM world  
					-   WHERE name like '%o__o%'![](https://api2.mubu.com/v3/document_image/444325fa-eedd-4fe1-a7c6-03e0c9a79f39-9404487.jpg)  
-   【多条件查询】  
	-   前面我们已经学会使用运算符和like加通配符进行查询啦，我们还可以使用and或者or逻辑运算符对多个条件进行组合筛选我们想要的数据  
	-   点击链接[https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)第八题  
		-   【题目】  
			-   从nobel表中查询1980年物理奖获得者和1984年化学奖获得者的年份（yr），学科（subject）和获奖者姓名（winner）  
		-   这一题是从一张名为nobel的数据库表中查询数据，输入代码select * from nobel可以查看一下这张表  
		-   这张表有三个字段，分别是年份yr，学科subject，获奖者姓名winner，记录的是获得诺贝尔奖的获奖相关信息  
		-   再看题目，查询1980年物理奖获得者和1984年化学奖获得者，翻译成可以写成代码的话就是同时满足年份yr是1980年且学科subject是物理physics或者同时满足年份yr是1984年且学科subject是化学chemistry的获奖者，"同时"满足用逻辑运算符and，"或者"用逻辑运算符or  
		-   写出代码where (subject = 'Physics' and yr = 1980) or (subject = 'Chemistry' and yr = 1984)  
		-   逻辑是同时满足两个条件或者同时满足另两个条件所以or前后两个条件部分需要加括号  
		-   运行代码，得到正确结果  
			-   select yr,subject,winner  
			-   from nobel  
			-   where (subject = 'Physics' and yr = 1980) or (subject = 'Chemistry' and yr = 1984)![](https://api2.mubu.com/v3/document_image/7ff349e2-d51d-4bfb-9a86-5b4182c6b2ae-9404487.jpg)  


-   【总结】  
	-   标准语法  
		-   `select` 字段名  
		-   `from` 表格名  
		-   `where` 条件代码  
	-   运算符查询语法  
		-   `select` 字段名  
		-   `from` 表名称  
		-   `where` 字段名 运算符 值  
	-   模糊查询语法  
		-   select 字段名  
		-   from 表名称  
		-   where 字段名 like '通配符+字符'  
	-   使用多条件查询  
		-   select 字段名  
		-   from 表名称  
		-   where 条件代码1 and|or 条件代码2  
	-   运算符  
		-   ![](https://api2.mubu.com/v3/document_image/f386d31c-876c-4fbd-aa07-16a0f36b006d-9404487.jpg)  
	-   通配符  
		-   ![](https://api2.mubu.com/v3/document_image/5714f438-11a2-482c-8071-de8290bf562b-9404487.jpg)  
### 【练习题】  
-   【1】[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第四题  
	-   【题目】  
		-   查询南美洲（south america）所有国家的名称以及它们以百万（1000000 ）为单位的人口数量  
		-   ![](https://api2.mubu.com/v3/document_image/03dc03d3-9c23-4e37-8859-c96c0217559f-9404487.jpg)  
	-   【正确答案】  
		-   select  
		-   name  
		-   , population/1000000 population_in_millions  
		-   from world  
		-   where continent = 'South America';  


-   【2】[https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)第九题  

	-   【题目】  

		-   查询1980年除诺贝尔化学奖和诺贝尔医学奖外其余奖项获奖者的所有信息。  


		-   ![](https://api2.mubu.com/v3/document_image/4c47fda4-cee1-4120-8e42-faa863e635f5-9404487.jpg)  


	-   【正确答案】  

		-   select *  


		-   from nobel  


		-   where yr = 1980  


		-   and subject not in ('Chemistry','Medicine')  


-   【3】[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第十三题  

	-   【题目】  

		-   查询既包含有所有元音字母（a,e,i,o,u），同时国家名中没有空格的国家，最后显示他们的名字  


		-   例如，赤道几内亚Equatorial Guinea 和 多米尼加共和国Dominican Republic ，都包括有五个元音字母（a,e,i,o,u)，但这些国家不会被记录，因为国家名中，由两个单词构成（有空格）  


		-   ![](https://api2.mubu.com/v3/document_image/b19f59f8-ce9a-4d97-85a7-9fc364981931-9404487.jpg)  


	-   【正确答案】  

		-   select name  


		-   from world  


		-   where name like '%a%'  


		-   and name like '%e%'  


		-   and name like '%i%'  


		-   and name like '%o%'  


		-   and name like '%u%'  


		-   and name not like '% %';  


-   【4】[https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)第十题  

	-   【题目】  

		-   查询1910年以前（不含1910）诺贝尔医学奖获得者和2004年及以后诺贝尔文学奖获得者的所有信息  


		-   ![](https://api2.mubu.com/v3/document_image/1eddcf7f-3b7b-4913-be5a-a23629bb4bd0-9404487.jpg)  


	-   【正确答案】  

		-   select *  


		-   from nobel  


		-   where (subject = 'Medicine' and yr < 1910)  


		-   or (subject = 'Literature' and yr >= 2004)