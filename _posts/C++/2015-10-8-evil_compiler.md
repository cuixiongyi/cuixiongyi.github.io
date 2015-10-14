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

g++4.8.2
---

![alt text][g++_str++]

[g++_str++]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/g++_str++.png "g++_str++"

For g++ even the 2nd statement is "wrong"
When execute
	
	cout << "*str++=" << *str++ << " 	pos= " << str - str_h << endl;

the output str - str_h should be executed after str++, so it's pos should be 1

But here str - str_h is obviously executed after str++, so it's pos is 0;

Then in the next line, the pos afterwards is 1



Reference
---
* [Sequence point](https://en.wikipedia.org/wiki/Sequence_point)

But in this case, I guess sequence point doesn't matter, because the computation of `*str` and `*str++` individually are well defined. But it is the sequence of executing them make the difference.

* [This answer](http://stackoverflow.com/a/31083924) observes that
**just because the ```++``` comes after the variable does not mean that the increment happens late.** The increment can happen as early as the compiler likes as long as the compiler ensures that the original value is used.

Conclusion
===	

The reason of this strange behavior is that the statement is an Undefined Behavior(UB). So there is no standard to define the execution of this statement. Thus the compiler could do whatever to optimize the code and in both MSVC and GCC does optimization in a way we didn't expect.

Update
---

It turns out that C++ primer (5th edition) already covered this.

![alt text][order_of_evaluation1]

[order_of_evaluation1]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/order_of_evaluation1.png "order_of_evaluation1"


![alt text][order_of_evaluation2]

[order_of_evaluation2]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/order_of_evaluation2.png "order_of_evaluation2"

![alt text][order_of_evaluation3]

[order_of_evaluation3]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/order_of_evaluation3.png "order_of_evaluation3"

![alt text][order_of_evaluation4]

[order_of_evaluation4]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/order_of_evaluation4.png "order_of_evaluation4"


