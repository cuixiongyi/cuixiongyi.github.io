---
layout: page
subheadline:  ""
title:  "The Evil Compiler"
teaser: "An invsiable hand is fcuking my code"
categories:
    - C++
tags:
    - C++
    - skills
comments: true
show_meta: true

---

The Evil Compiler
===

This code include 2 core statement
	
	cout<<*str<<endl;
	cout<<*str++<<endl;

But it will give a different result
	
	cout<<*str<<endl<<*str++<<endl;

Run this code in VS2013

	#include <iostream>

	using namespace std;

	int main()
	{

		char* str = "abcdefg";
		char* str_h = str;
		// wirte the statement saperate
		cout <<"*str=	"<< *str << "	pos= " << str - str_h<<endl;

		cout << "*str++=	" << *str++ << " 	pos= " << str - str_h << endl;
		
		cout << endl<< "str = str_0" << endl << endl;
		str = str_h;
		// wirte the statement in one line
		cout << "*str=	" << *str << "	pos= " << str - str_h << endl
		<< "*str++=	" << *str++ << " 	pos= " << str - str_h << endl;


		char t;
		cin >> t;
	}

Here is the result:

![alt text][VS2013]

[VS2013]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/vc2013.png "VS2013"



