
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
		// 1st statement
		cout <<"*str=	"<< *str << "	pos= " << str - str_h<<endl;

		// 2nd statement
		cout << "*str++=	" << *str++ << " 	pos= " << str - str_h << endl;
		cout<<"pos= " <<str - str_h <<endl;

		cout << endl<< "str = str_0" << endl << endl;
		str = str_h;
		// 3rd statement
		cout << "*str=	" << *str << "	pos= " << str - str_h << endl
		<< "*str++=	" << *str++ << " 	pos= " << str - str_h << endl;

		cout<<"pos= " <<str - str_h <<endl;

		char t;
		cin >> t;
		return 1;
	}

Here is the result:

VS2013
---


![alt text][VS2013]

[VS2013]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/vc2013.png "VS2013"


The 3rd statement give an obvious wrong.

	cout<< *str <<endl<< *str++ <<endl;

I believe this is the compilier doing. I guess the compiler try to optimize the increment(++) operation by execute the statement with ++ first. 
So the code execution sequence is 

	//cout<<*str<<endl<<*str++<<endl;
	*str 	// the last one, so the output is 'a'
	str++	// 
	*str 	// the first one
