---
title: Lambda Expression
tags: C++
grammar_cjkRuby: true
grammar_tableExtra: true
---
## Basic Lambda
![Basic Lambda](./images/1550478490833.png)
1. Capture Clause
	* (C++14) introduce new variables in body
	* capture by value, capture by reference(&)
	* default capture mode, capture-default
		* [], empty capture clause
		* [&], all variable referred are captured by reference.
		* [=], all variable referred are captured by value
		* 
2. (Optional) Parameter List
3. (Optional) mutable specification
	* Mutable specification: cancel const-by-value.
4. (Optional) exception specification
	* noexcept.There is static check for this case.
5. (Optional) trailing-return-type
	* auto deduced
6. Lambda body.
	* 

