### SQL是什么？  

#### SQL是一种能指挥数据库自动&批量处理大量Excel表格的超级简单的语言  

-   语法标准由ANSI美国国家标准化组织统一制定，主流数据库的关键语法都是相同的  
	-   如`select`、`update`、`delete`、`insert`、`where`等  


#### 只针对结构化数据进行处理，不处理乱糟糟非结构化数据  

-   非结构化数据  
		-   ![](https://api2.mubu.com/v3/document_image/5ea2a225-3db6-4e71-aafc-403cab76acc3-1105051.jpg)  


	-   结构化数据  
		-   ![](https://api2.mubu.com/v3/document_image/8afa06fb-962c-4435-8d3e-78965d89fe49-1105051.jpg)  

#### 有严格的语法结构和运行顺序（所以学起来非常简单）  

-   语法结构：
	-   `select`--`from`--`where`--`group by`--`having`--`order by`--`limit`

-   运行顺序：
	-   `from`--`where`--`group by`--`having`--`order by`--`limit`--`select`





-   主知识点一：select&from  

	-   【知识点引入】  

		-   首先我们先认识两句子句，select和from  

			-   【标准语法】  

				-   select 字段名  


				-   from 表名称  


			-   【语法解释】  

				-   select 字段名 表明选择查询表格中的哪几列进行查看  


				-   from 表格名 表明你查询的数据来自哪一个数据库表  


		-   但凡大家要从数据库中查询数据，必不可少的就是select和from语句  


		-   现在给大家5秒的时间记忆这两个单词，5，4，3，2，1  


		-   好啦，大家现在已经学会最基础的sql查询语句啦  


		-   接下来让我们一起来学习如何应用select和from语句进行查询吧  


	-   【例题讲解】  

		-   【基础查询select单列&多列&所有列&别名应用】  
			-   我们点开链接[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第一题  

				-   【题目】  
					-   阅读关于表格的信息，观察SQL代码并运行  


				-   我们先观察我们要查询的表格中的表头，知道每个列名称，再查看表格前几行数据知道每一行和每一列数据的大致内容  
					-   ![](https://api2.mubu.com/v3/document_image/2a62d212-b6ea-43fb-8b93-185a6d25301d-9404487.jpg)  


				-   观察题目给我们的代码  

					-   ![](https://api2.mubu.com/v3/document_image/236ad1d4-5b1d-4bb5-99be-ae9bf96a8615-9404487.jpg)  


					-   由刚才我们所学的select 和from组成，select后有多个字段名，表明这段代码查询的是多列数据，字段顺序按照select后所写的字段顺序依次展现，注意逗号是在英文输入法下输入的  


					-   select name, continent, population from world表明要查询名为 "name" 、 "continent" 和"population"的列的内容从名为world的数据库表中，同时记住SQL对大小写不敏感SELECT和select完全等效，但是为了书写效率，成熟的分析师一般都用小写  


					-   点击运行代码  
						-   得到结果![](https://api2.mubu.com/v3/document_image/4d15ee45-db8c-4da6-9cd0-8ffdad1484fd-9404487.jpg)  


				-   将所有列名称变更为单一的*：SELECT * FROM world  
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


	-   【总结】  

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


	-   【练习题】  
		-   自己完整敲一遍知识点中出现的代码吧~  


-   主知识点二：where  

	-   【知识点引入】  

		-   我们来认识第三个子句where，where子句写在from之后  

			-   【标准语法】  

				-   select 字段名  


				-   from 表格名  


				-   where 条件代码  


			-   【语法解释】  
				-   where 条件代码 表明从数据库表中选取满足条件的数据  


		-   where子句主要用来进行数据的筛选，从表格中筛选出符合条件的行数据  


		-   接下来让我们来快速应用where子句吧~  


	-   【例题讲解】  

		-   【运算符】  

			-   条件代码中最常用的是运算符。  
				-   运算符查询标准语法  

					-   select 字段名  


					-   from 表名称  


					-   where 字段名 运算符 值  


			-   先来看这个表格，比较运算符，用于判断表中的哪些数据符合条件，and、or和not为逻辑运算符，not一般和与其他连用例如not in等。![](https://api2.mubu.com/v3/document_image/f386d31c-876c-4fbd-aa07-16a0f36b006d-9404487.jpg)  


			-   and 和 or 可以把两个或多个条件结合起来。若and连接的两个条件对于该数据都成立，就显示该数据，若or连接的两个条件对于该数据只要有一个成立，就显示该数据，否则就筛除该数据。  


			-   点击链接[https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)第三题  

				-   【题目】  
					-   查询人口数至少2亿的国家名和人均GDP  


				-   人均GDP如何查询我们已经在前面讲过了，这里就不再赘述了。这里着重看的是“人口数至少2亿”这个条件，说人话就是人口population大于等于两亿，写成代码语言就是population>=200000000,并写在where子句后，与select和from子句组合在一起得到正确代码  


				-   【运行代码】  

					-   select name,GDP/population 人均gdp  


					-   from world  


					-   where population>=200000000  


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

						-   SELECT population  


						-   FROM world  


						-   WHERE name = 'Germany'![](https://api2.mubu.com/v3/document_image/150e16d6-8256-41ca-b038-810cafa13cc5-9404487.jpg)  


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

			-   select 字段名  


			-   from 表格名  


			-   where 条件代码  


		-   运算符查询语法  

			-   select 字段名  


			-   from 表名称  


			-   where 字段名 运算符 值  


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


	-   【练习题】  

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


-   主知识点三：聚合函数、group by&having  

	-   【知识点引入】  

		-   我们先来认识最常见的聚合函数  

			-   ![](https://api2.mubu.com/v3/document_image/b177d83e-4777-4d7d-a8f5-18dbae636214-9404487.jpg)  


			-   有时候我们只是需要获取数据的汇总信息，比如说行数啊、平均值啊这种，并不需要吧所有数据都检索出来，只需要使用聚合函数即可  


			-   【函数说明】  

				-   AVG() 返回某列的均值  


				-   COUNT() 返回某列的行数  


				-   MAX() 返回某列的最大值  


				-   MIN() 返回某列的最小值  


				-   SUM() 返回某列的和  


			-   注意聚合函数都会忽略列中的NULL值，但是COUNT(*)也就是统计全部数据的行数时，不会忽略NULL值  


		-   我们再来认识两个子句group by 和having  

			-   【标准语法】  

				-   select 字段名1  


				-   from 表格名  


				-   [where 条件代码]  


				-   group by 字段名1  


				-   having 条件代码  


			-   【语法解释】  

				-   之前学到的筛选操作都是基于整个表去进行的，那如果想要依据某列中的不同类别（比如说不同品牌/不同性别等等）进行分类统计时，就要用到数据分组，在SQL中数据分组是使用GROUP BY子句建立  


				-   GROUP BY子句可以包含任意数量的列，因而可以对分组进行多重嵌套，如按照班级和性别进行分组的话，结果中班级A包含男生组和女生组，班级B也包含男生组和女生组  


				-   having 子句和where 子句一样用于条件筛选，两者的操作符一致，但不同的是where是在指定分组前对数据进行筛选过滤，而having可以对分组后的数据进行筛选过滤  


				-   注意写的子句的顺序不可颠倒，需要严格按照语法的顺序！  


	-   【例题讲解】  

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


	-   【总结】  

		-   常用聚合函数  
			-   ![](https://api2.mubu.com/v3/document_image/b177d83e-4777-4d7d-a8f5-18dbae636214-9404487.jpg)  


		-   标准语法  

			-   select 字段名1  


			-   from 表格名  


			-   [where 条件代码]  


			-   group by 字段名1  


			-   having 条件代码  


	-   【练习题】  

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


-   主知识点四：order by  

	-   【知识点引入】  
		-   我们再来认识第六个子句order by  

			-   【标准语法】  

				-   select 字段名1  


				-   from 表格名  


				-   [where 条件代码]  


				-   [group by 字段名1]  


				-   [having 条件代码]  


				-   order by 字段名 asc|desc  


			-   【语法解释】  

				-   order by 子句会对最后查询出的结果集进行排序  


				-   order by 字段名，表明根据指定的字段进行排序  


				-   asc指定该字段升序排序，desc为降序排序，不写则默认为升序排序  


				-   order by 可以对多个字段按照主字段和次字段排序，每个字段都可以指定升序还是降序排序  


	-   【例题讲解】  
		-   点击链接[https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)第十三题  

			-   【题目】  

				-   查询姓名以Sir开头的获奖者的姓名，获奖年份和奖项  


				-   查询结果按照年份从近到远排序，再按照姓名字母顺序升序排序  


			-   查询获奖者的姓名，获奖年份和奖项，写出代码select winner, yr, subject  


			-   从数据库表nobel中查询，写出代码from nobel  


			-   姓名以Sir开头的获奖者，写出代码where winner like 'Sir%'  


			-   按年份降序排序，姓名字母顺序升序排序，写出代码order by yr desc,winner  


			-   【运行代码】  

				-   select winner, yr, subject  


				-   from nobel  


				-   where winner like 'Sir%'  


				-   order by yr desc,winner  


			-   【运行结果】  
				-   ![](https://api2.mubu.com/v3/document_image/ca65def3-d642-4194-bd40-4e0c4bbbe18c-9404487.jpg)  


	-   【总结】  
		-   【标准语法】  

			-   select 字段名1  


			-   from 表格名  


			-   [where 条件代码]  


			-   [group by 字段名1]  


			-   [having 条件代码]  


			-   order by 字段名 asc|desc  


	-   【练习题】  
		-   【1】点击链接[https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)第十四题  

			-   【题目】  

				-   查询1984年所有获奖者的姓名和奖项。结果将诺贝尔化学奖和物理学奖排在最后，然后按照奖项排序，再按照获奖者姓名排序  


				-   ![](https://api2.mubu.com/v3/document_image/60d0bd29-780d-434c-add3-4f8b943d5990-9404487.jpg)  


			-   【正确答案】  

				-   select  


				-   winner  


				-   ,subject  


				-   from nobel  


				-   where yr = 1984  


				-   order by subject in ('chemistry','physics') , subject, winner  


-   主知识点五：limit  

	-   【知识点引入】  

		-   select 字段名1  


		-   from 表格名  


		-   [where 条件代码]  


		-   [group by 字段名1]  


		-   [having 条件代码]  


		-   [order by 字段名 asc|desc]  


		-   limit n  


	-   【例题讲解】  
		-   【查询结果返回某几行】  
			-   点击链接[https://www.nowcoder.com/practice/f24966e0cb8a49c192b5e65339bc8c03?tpId=82&&tqId=29823&rp=1&ru=/ta/sql&qru=/ta/sql/question-ranking](https://www.nowcoder.com/practice/f24966e0cb8a49c192b5e65339bc8c03?tpId=82&&tqId=29823&rp=1&ru=/ta/sql&qru=/ta/sql/question-ranking)  

				-   【题目】  
					-   分页查询employees表，每5行一页，返回第2页的数据  


				-   翻译成人话就是查询第6行到第10行的数据，共5行  


				-   写出代码limit 5,5  


				-   【运行代码】  

					-   select *  


					-   from employees  


					-   limit 5,5  


	-   【总结】  

		-   【查询结果返回前n行】  

			-   select 字段名1  


			-   from 表格名  


			-   [where 条件代码]  


			-   [group by 字段名1]  


			-   [having 条件代码]  


			-   [order by 字段名 asc|desc]  


			-   limit n  


		-   【查询结果返回x+1行到x+y行】  

			-   select 字段名1  


			-   from 表格名  


			-   [where 条件代码]  


			-   [group by 字段名1]  


			-   [having 条件代码]  


			-   [order by 字段名 asc|desc]  


			-   limit x,y  


-   主知识点六：子查询  

	-   【知识点引入】  

		-   到这里我们已经把sql的主要子句学完啦，接下来就是sql语法的进阶学习  


		-   首先是造就了sql语句千变万化的子查询  


		-   子查询本身就是一个完整的查询语句，然后用括号（）包裹嵌套在主查询语句中，子查询可以多层嵌套  


		-   之前所涉及到的都是从数据库中检索数据的单条语句，但当我们想要检索的数据并不能直接从数据库表中获取，而是需要从筛选后的表格中再度去查询时，就要用到子查询，相当于我们无法直达时，需要进行换乘  


		-   子查询的执行优先于主查询执行，因为主查询的条件用到了子查询的结果  


		-   子查询主要分为三类  

			-   标量子查询  
				-   查询结果只有一行一列  


			-   行子查询  
				-   查询结果只有一行  


			-   列子查询  
				-   查询结果只有一列  


			-   表子查询  
				-   查询结果有多行多列  


	-   【例题讲解】  
		-   【where基于子查询条件筛选】  

			-   点击链接[https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)第六题  

				-   【题目】  
					-   查询出gdp高于欧洲每个国家的所有国家名称，有一些国家gdp值可能为NULL，请排除这些国家  


				-   将题目翻译成人话就是查询国家名称，这些国家的gdp大于欧洲国家中最大的gdp，其中国家的gdp不为空值  


				-   由于欧洲国家中最大的gdp未知，我们先需要写子查询语句  

					-   select max(gdp)  


					-   from world  


					-   where continent='europe'  


					-   and gdp is not null  
						-   ![](https://api2.mubu.com/v3/document_image/95a8b5cb-942a-42b0-b0a8-1b6377db3649-9404487.jpg)  


				-   这样我们就得到欧洲国家中最大的GDP了  


				-   接着我们查询gdp大于这个值的国家名  


				-   写出代码where gdp>子查询  


				-   将代码进行组合  


				-   【运行代码】  

					-   select name  


					-   from world  


					-   where gdp>(  

						-   select max(gdp)  


						-   from world  


						-   where continent='europe'  


						-   and gdp is not null  


						-   )  


				-   【运行结果】  
					-   ![](https://api2.mubu.com/v3/document_image/e57b4b64-eb21-40af-a48f-5d8c1d091a98-9404487.jpg)  


				-   这题代码中的子查询结果是单行单列的标量子查询  


				-   等同于where gdp > 3425956000000  


				-   只是欧洲国家中最大的GDP数值我们并不知道，因此需要先构建子查询作为中转，具体的数值3425956000000就由子查询来代替了  


			-   点击链接[https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)第三题  

				-   【题目】  
					-   查询跟阿尔及尼亚（Argentina）和澳大利亚（Australia）在同一大洲的所有国家名称， 并按照国家名称进行排序展示  


				-   由于阿尔及尼亚（Argentina）和澳大利亚（Australia）所属大洲未知，所以我们先写子查询得到这两个国家所属的大洲  

					-   【运行代码】  

						-   select continent  


						-   from world  


						-   where name='Argentina'  


						-   or name='Australia'  


					-   【运行结果】  
						-   ![](https://api2.mubu.com/v3/document_image/9a435c06-eb56-4288-bdb2-f35e1f9cb41d-9404487.jpg)  


				-   接下来查询属于这两个大洲的国家名称，并按照名字排序，这里没有指定排序降序还是升序，所以使用默认的升序  


				-   由于子查询是列子查询，有多个值，所以条件筛选中使用in操作符  

					-   【运行代码】  

						-   select name,continent  


						-   from world  


						-   where continent in (  

							-   select continent  


							-   from world  


							-   where name='Argentina'  


							-   or name='Australia'  


							-   )  


						-   order by name  


					-   【运行结果】  
						-   ![](https://api2.mubu.com/v3/document_image/d23dfb87-df22-4b38-9589-74711ba7eefd-9404487.jpg)  


	-   【总结】  

		-   子查询本身是一个完整的查询，由括号包裹嵌套在主查询中  


		-   子查询最后返回查询出的结果给主查询  


		-   子查询可以在select，from，where，having子句中使用，但要注意不同子句能接受的子查询种类有差别  


		-   子查询可以多重嵌套  


	-   【练习题】  

		-   【1】[https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)第一题  

			-   【题目】  

				-   查询 人口（population）比俄罗斯Russia更多的国家名（name）  


				-   ![](https://api2.mubu.com/v3/document_image/dd159e8c-6881-4466-8cf9-4a10ad46f308-9404487.jpg)  


			-   【正确答案】  

				-   select  


				-   name  


				-   from world  


				-   where population > (  

					-   select population  


					-   from world  


					-   where name = 'Russia'  


					-   )  


		-   【2】[https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)第七题  

			-   【题目】  

				-   查找每个大陆（continent）中最大的国家（按区域area），显示该大陆（continent），名称（name）和区域（area）  


				-   ![](https://api2.mubu.com/v3/document_image/17c28813-90c0-42da-976a-abfd2689d96f-9404487.jpg)  


			-   【正确答案】  

				-   select  


				-   continent  


				-   ,name  


				-   ,area  


				-   from world  


				-   where (continent,area) in (  

					-   select  


					-   continent  


					-   ,max(area)  


					-   from world  


					-   group by continent  


					-   )  


		-   【3】[https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)第二题  

			-   【题目】  

				-   查询在欧洲Europe中人均gdp大于 英国 'United Kingdom' 的国家名  


				-   ![](https://api2.mubu.com/v3/document_image/d17bc604-4439-47c1-a28e-0ba40bb4b5b5-9404487.jpg)  


			-   【正确答案】  

				-   select  


				-   name  


				-   from world  


				-   where continent = 'Europe'  


				-   and gdp / population > (  

					-   select  


					-   gdp / population  


					-   from world  


					-   where name = 'United Kingdom'  


					-   )  


		-   【4】[https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)第四题  

			-   【题目】  

				-   查询国家的人口数（population）超过加拿大（Canada）但少于波兰（Poland）的国家的名称（name）和人口数（population）  


				-   ![](https://api2.mubu.com/v3/document_image/df95c910-086c-415a-8ba2-29ac9e0374d1-9404487.jpg)  


			-   【正确答案】  

				-   select  


				-   name  


				-   , population  


				-   from world  


				-   where population > (  

					-   select  


					-   population  


					-   from world  


					-   where name = 'Canada'  


					-   )  


				-   and population < (  

					-   select  


					-   population  


					-   from world  


					-   where name = 'Poland'  


					-   )