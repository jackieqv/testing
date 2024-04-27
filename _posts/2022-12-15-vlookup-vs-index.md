---
title: "VLOOKUP() vs. INDEX()"
published: true
categories:
  - Excel
  - Vlookup
  - Index

tags:
  - Excel skills
  - Vlookup
  - Index
  - Vlookup vs. Index
date: 2022-12-27 00:02 +0100
---
Hi all,
today's blog post is a guest post by my husband Sven, who compares the vlookup() and the index() function in Excel. They are both very useful functions for finding things in a table range. It's quite a long post to read but a very useful one. Kudos to him for being so dedicated and writing such a long article!:clap: Most of you working an office job and using Excel to analyze data, can probably relate.:computer: I am using the vlookup() function a lot but the function has its limitations. The lookup_value must be always the very left column of the table_array of the function. Therefore, I always find myself inserting columns to get the right order for the vlookup() to function. Understanding the index() function can help you out directly finding your lookup_value without paying attention to the order of the table_array.

And over to Sven's part:
---
I am happy be given the chance to write a guest post on Jackie’s Blog. In this post I will write a comparison between two Excel functions that can be used to access data from a different table via comparing a lookup value. The vlookup() vs. index() function.
To explain the differences, I will use an example of made-up HR-data. Imagine you are given the following task: You are granted access to a table with several information on employee data, but one column is missing. The missing values can be found in a separate table as shown below. In this example we are going to fill in the salary column of the Employee data table.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_1.png"/>

If you want a fast solution without further explanation for the first entry, here you go:
```yaml
Vlookup: =VLOOKUP(A4;$G$4:$H$6;2;FALSE)
Index: 	 =INDEX($G$4:$H$6;MATCH(A4;$G$4:$G$6;0);2)
```

Using vlookup()
---
Let us first use the vlookup() function to fill in the column of Salary. Generally, the vlookup() function is used to look up a value in the leftmost column of a table and then returns a value in the same row from a different table that can be specified. The v in vlookup() stands for vertical.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_2.png"/>

After typing in the vlookup() function into the first salary cell of the example, Excel already shows us the required parameters to set up this function.

**lookup_value**: This is the value that we are using as a reference to lookup in the other table. Normally that could be an ID as we also have here. Therefore, we are selecting the Cell A4 as a lookup_value.

**table_array**: This argument wants us to select the whole table where we would expect the answer column to be in. The table_array must have the lookup_value in the very left column, otherwise the vlookup() function will return an error. In our example that would be the Employee salary table ($G$4:$H$6).

**col_index_num**: This argument wants us to define the column of our previously defined table_array where we want to get our answer from. Since we want to gain the information on the Annual Salary which is the second column of the table_array, we must take the value 2.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_3.png"/>

**(range_lookup)**: This argument is optional and wants the user to define the accuracy of the lookup_value.:
TRUE &rarr; the function will work with an approximate match.
FALSE &rarr; the function will only work with an exact match. This is normally what the user wants to set.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_4.png"/>

In the example above, the vlookup() function returns different results depending on the setting of the parameter (range_lookup). The ID EMP002 is not existent in the Employee salary table. Therefore, setting the parameter on the value true returns a result with an approximately correct ID. In this case for the ID EMP001.

Note that the parameter (range_lookup) is automatically set on TRUE per default if it has not been declared all. This might lead to results that the user is not expecting.
The final result using the vlookup() function should look like this:
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_5.png"/>


Using index()
---
We will solve the same problem with the index function now. The index function is used to return a value or a reference of a cell at the intersection of a particular row and column in a given range. Let’s first look at the parameters of the function again.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_6.png"/>

**array**: is used to define the table, where we want to get our answer from. In our example that would be the Employee salary table ($G$4:$H$6).

**row_num**: is used to define the row, from which we want to get the result. In the given example that would be row number 1. But if we would set the parameter to 1, we would always get the same result returned to us, since we hardcoded 1 into the function and therefore it is not automatically adjusted if we apply it to all the other rows.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_7.png"/>

Therefore, we must come up with a different solution that helps us to automatically find the correct row number for every row we are looking at. To get the correct row number, we will use the match() function, since it returns the relative position of an item in an array that matches a specific value in a specified order. It helps us to always find the correct row number for the index() function.

match() needs three parameters to be filled:
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_8.png"/>

**lookup_value**: This is the value that we are using as a reference to lookup in the other table. Normally that could be an ID as we also have here. Therefore, we are selecting the Cell A4 as a lookup_value.

**lookup_array**: This parameter wants us to select the column, where we want to find the lookup_value in. Since we want to find our lookup_value from the data table in the salary table, we must select the column ID in the salary table ($G$4:$G$6).

**(match_type)**: Similarly, to the (range_lookup) parameter from the vlookup() function, this is an optional parameter that we can use to specify the type of match that we want to receive. Select the value 0 for exact matches.

Note that the parameter (match_type) is automatically set on 1 per default if it has not been declared all. This might lead to results that the user is not expecting.

**col_num**: is used to define the column, from which we want to get the result. In the given example that would be column number 2. Since our result will always be in column number two, we can safely hardcode the number 2 to all the other rows.

And here you go using index() and match().
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_9.png"/>

Since using vlookup() is way easier to handle than using index(), I would recommend solving this request with the vlookup() function. But there are some problems with the vlookup function. Imagine the Employee salary table would have its columns in reverse order.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_10.png"/>

In that case, the vlookup() function does not work anymore, because its lookup_value must always be in the very left column of the table_array. The index() function has no problem with this request at all. Only the col_num parameter must be adjusted to 1. 
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_11.png"/>

A different problem may occur, if the result of our table is depending on a second parameter. Let us consider the second parameter to salary type, we want to look at.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_12.png"/>

We could adjust our vlookup() function with a match() function, to gain the wanted result. 
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_13.png"/>

The same applies to the index() function. We can adjust it by using a second match() function for the col_num.
<img src="{{site.baseurl | prepend: site.url}}assets/images/vlookup%20vs%20index_14.png"/>

To sum this topic up, I would recommend using the vlookup() function whenever it is possible since it is much easier to handle.