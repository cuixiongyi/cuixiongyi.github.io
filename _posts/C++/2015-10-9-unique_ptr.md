---
layout: page
subheadline:  ""
title:  "Pointer performance test"
teaser: "How unique_ptr, shared_ptr compare to raw ptr"
categories:
    - C++
tags:
    - C++
    - skills
    - array
comments: true
show_meta: true

---


# Read Array Type

Test the performance of unique_ptr, shared_ptr and raw ptr

	#include <iostream>
	#include <stdio.h>
	#include <ctime>
	#include <unistd.h>
	#include <memory>
	#include <vector>
	#include <chrono>
	typedef std::chrono::high_resolution_clock Clock;


	using namespace std;

	class foo
	{
	public:
		foo(){};
		~foo(){};
		
		std::vector<int> v;
		double data;
	};

	int main()
	{
		constexpr int count = 1000000; 
		auto t1 = Clock::now();
		for (int i = 0; i < count; ++i)
		{
			unique_ptr<foo> ptrFoo = make_unique<foo>();
		}
	    auto t2 = Clock::now();
	    std::cout << "make_unique "<< count<< " times "
	              << std::chrono::duration_cast<std::chrono::microseconds>(t2 - t1).count()
	              << " microseconds" << std::endl<<endl;

		t1 = Clock::now();
		for (int i = 0; i < count; ++i)
		{
			shared_ptr<foo> ptrFoo = make_shared<foo>();
		}
	    t2 = Clock::now();
	    std::cout << "make_shared "<< count<< " times "
	              << std::chrono::duration_cast<std::chrono::microseconds>(t2 - t1).count()
	              << " microseconds" << std::endl<<endl;


		t1 = Clock::now();
		for (int i = 0; i < count; ++i)
		{
			foo* ptrFoo = new foo;
			delete ptrFoo;
		}
	    t2 = Clock::now();
	    std::cout << "raw point "<< count<< " times "
	              << std::chrono::duration_cast<std::chrono::microseconds>(t2 - t1).count()
	              << " microseconds" << std::endl<<endl;

		char t;
		cin >> t;


		char ca[] = {'C', '+', '+'};
		cout<< ca<<endl;
		return 1;
	}

compile with

	g++-5 -std=c++1y unique_ptr.cpp -o uniq

Result
---

## g++

![alt text][unique_ptr]

[unique_ptr]: https://raw.githubusercontent.com/cuixiongyi/cuixiongyi.github.io/master/images/unique_ptr.png "unique_ptr"

Conculsion
---

Although raw pointer is twice as fast as unique_ptr, I guess compare to the whole program, the pointer overhead is trivial, while the benefit of using unique_ptr is enormous. 

**So, I would still use unique_ptr as default.**
