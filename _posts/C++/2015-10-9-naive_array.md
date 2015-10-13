---
layout: page
subheadline:  ""
title:  "Naive Array"
teaser: "There are several strang things about naive array, although I don't use them no more"
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

C++ Primer 3.5.1

	int *ptrs[10]; 			// ptrs is an array of ten pointers to int
	int &refs[10] = /* ? */; 	// error: no arrays of references
	int (*Parray)[10] = &arr; 	// Parray points to an array of ten ints
	int (&arrRef)[10] = arr; 	// arrRef refers to an array of ten ints

By default, type modifiers bind right to left. Reading the definition of ptrs from right to left (§ 2.3.3, p. 58) is easy: We see that we’re defining an array of size 10, named ptrs, that holds pointers to int.

Reading the definition of Parray from right to left isn’t as helpful. Because the
array dimension follows the name being declared, it can be easier to read array
declarations from the inside out rather than from right to left. Reading from the inside out makes it much easier to understand the type of Parray. 

We start by observing
that the parentheses around *Parray mean that Parray is a pointer. Looking right,
we see that Parray points to an array of size 10. Looking left, we see that the
elements in that array are ints. Thus, Parray is a pointer to an array of ten ints.
Similarly, `(&arrRef)` says that arrRef is a reference. The type to which it refers is
an array of size 10. That array holds elements of type int.

Of course, there are no limits on how many type modifiers can be used:

	int *(&arry)[10] = ptrs; // arry is a reference to an array of ten pointers

Reading this declaration from the inside out, we see that arry is a reference. Looking
right, we see that the object to which arry refers is an array of size 10. Looking left,

we see that the element type is pointer to int. Thus, arry is a reference to an array
of ten pointers.

> Tip
> It can be easier to understand array declarations by starting with the array’s name and reading them from the inside out.

# Pointers and Arrays

C++ Primer 3.5.3

There are various implications of the fact that operations on arrays are often really
operations on pointers. One such implication is that when we use an array as an
initializer for a variable defined using auto (§ 2.5.2, p. 68), the deduced type is a
pointer, not an array:

	int ia[] = {0,1,2,3,4,5,6,7,8,9}; // ia is an array of ten ints
	auto ia2(ia); // ia2 is an int* that points to the first element in ia
	ia2 = 42; // error: ia2 is a pointer, and we can't assign an int to a pointer

Although ia is an array of ten ints, when we use ia as an initializer, the compiler
treats that initialization as if we had written

	auto ia2(&ia[0]); // now it's clear that ia2 has type int*

It is worth noting that this conversion does not happen when we use decltype (§
2.5.3, p. 70). The type returned by decltype(ia) is array of ten ints:

	// ia3 is an array of ten ints
	decltype(ia) ia3 = {0,1,2,3,4,5,6,7,8,9};
	ia3 = p; // error: can't assign an int* to an array
	ia3[4] = i; // ok: assigns the value of i to an element in ia3

# Reference

* [Difference between pointer and array in C](http://www.geeksforgeeks.org/difference-pointer-array-c/)
* [Pointer vs Array in C](http://www.geeksforgeeks.org/g-fact-5/)