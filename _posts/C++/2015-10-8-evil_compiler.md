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
		cout<<"pos= " <<str - str_h <<endl;

		cout << endl<< "str = str_0" << endl << endl;
		str = str_h;
		// wirte the statement in one line
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


The second statement give a different result and it's obvious wrong.

	cout<< *str <<endl<< *str++ <<endl;

I believe this is the compilier doing. I guess the compiler try to optimize the increment(++) operation by execute the statement with ++ first. 
So the code execution sequence is 

	//cout<<*str<<endl<<*str++<<endl;
	*str 	// the last one, so the output is 'a'
	str++	// 
	*str 	// the first one

g++4.8.2
---

![alt text][g++_str++]

[g++_str++]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/g++_str++.png "g++_str++"

For g++ even the first statement is "wrong"
When execute
	
	cout << "*str++=" << *str++ << " 	pos= " << str - str_h << endl;

the output str - str_h should be executed after str++, so it's pos should be 1

But here str - str_h is obviously executed after str++, so it's pos is 0;

Then in the next line, the pos afterwards is 1






	

