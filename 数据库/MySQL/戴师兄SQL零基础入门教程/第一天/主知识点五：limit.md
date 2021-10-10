# 主知识点五：limit

### 【知识点引入】  
-   select 字段名1  
-   from 表格名  
-   where 条件代码
-   group by 字段名1
-   having 条件代码
-   order by 字段名 asc|desc
-   limit n  


### 【例题讲解】  
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


### 【总结】  
 ####【查询结果返回前n行】  
-   select 字段名1  
-   from 表格名  
-   where 条件代码
-   group by 字段名1  
-   having 条件代码  
-   order by 字段名 asc|desc  
-   limit n  
#### 【查询结果返回x+1行到x+y行】  
-   select 字段名1  
-   from 表格名  
-   where 条件代码] 
-   group by 字段名1 
-   having 条件代码  
-   order by 字段名 asc|desc  
-   limit x,y