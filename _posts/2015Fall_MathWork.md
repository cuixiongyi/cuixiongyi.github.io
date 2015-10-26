


I had a onsite interview at MathWork today. Sadly I didn't make it.

A Indin girl took gave me the interview.
The tech interview has 4 parts

## algorithm test

Write down any sorting algorithm

## C++

There are 4 pages of C++ code and you need to find out the output

1. The first one is about shallow and deep copy 
1. The behavior of virtual destructor

	#include <iostream>
	Class A
	{
	public:
		~A()
		{
			std::cout<<"A"<<std::endl;
		}
	}
	Class B
	{
	public:
		~B()
		{
			std::cout<<"B"<<std::endl;
		}
	}
	
	void main()
	{
		A* ptr = new B;
		delete ptr;
		return;
	}
	
	
1. Static class member 
1. Behavior of array pointer

	#include <iostream>
	void main()
	{
		int arr[] = {0,1,2,3,4};
		//int* ptr = arr;
		std::cout<<*(arr+1)<<std::endl;
		std::cout<<*(arr++)<<std::endl;
		return;
	}

1. 


## Matlab

She told me to choose another language for test. I thought my Matlab is good until I saw the questions.


