---
layout: page
subheadline:  "Onsite Interview from MathWork 2015 Fall"
title:  "Onsite Interview from MathWork 2015 Fall"
teaser: "Interview"
categories:
    - interview
tags:
    - interview
    - MathWork

comments: true
show_meta: true

---

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




## Matlab

She told me to choose another language for test. I thought my Matlab is good until I saw the questions.

### Scenario 1

The first scenario is the proccess data.

1. How to optimize the following code

		sensorData = [50, 30, 45, 36, 45];
		scalePara = [2, 6, 8, 32, 10, 32];
		for sensor = 1 : 5
			scaledData(sensor) = sensorData(sensor) / scalePara(sensor);
		end

2. How to optimize the code if (data still needed to be divided by the scaledPara, which means that you need to do it row by row). I used a loop over the rows, but there must be better ways to do this.
	
		sensorData = [50, 30, 45, 36, 45,
				52, 32, 74, 23, 68,
				20, 30, 48, 95, 30];

### Scenario 2

1. If you are writing a project in Matlab, would you use function or script.
2. If you have a function to do clean up, is it a good idea to name the function "end"?

### Scenario 3

1. If you have a 4 sensor with each sensor has 1000 data, how do you visualize the data.

2. How would you differentiate the different data from different sensors.

### Scenario 4

1. If you have lines of repeatation to calculate something, what would you do.

2. If you have a complicated calculation in one line and there are many lines like it, how do you optimize without write another function.


## Math

It's really simple the first one is a linear function with porperty 
	
	F(A+B) = F(A) + F(B)
	F(kA) = kF(A)

