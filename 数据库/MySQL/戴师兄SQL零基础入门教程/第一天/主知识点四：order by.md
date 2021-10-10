# 主知识点四：order by

### 【知识点引入】  
-   我们再来认识第六个子句order by  
#### 【标准语法】  
-   select 字段名1  
-   from 表格名  
-   where 条件代码
-   group by 字段名1
-   having 条件代码
-   order by 字段名 asc|desc  

#### 【语法解释】  

-   order by 子句会对最后查询出的结果集进行排序  
-   order by 字段名，表明根据指定的字段进行排序  
-   asc指定该字段升序排序，desc为降序排序，不写则默认为升序排序  
-   order by 可以对多个字段按照主字段和次字段排序，每个字段都可以指定升序还是降序排序  


### 【例题讲解】  
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


### 【总结】  
-   【标准语法】  
	-   select 字段名1  
	-   from 表格名  
	-   where 条件代码
	-   group by 字段名1
	-   having 条件代码
	-   order by 字段名 asc|desc  


###【练习题】  
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