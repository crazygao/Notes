---
title: Type Fundamentals
tags: C#
grammar_cjkRuby: true
grammar_tableExtra: true
---

# Type Fundamentals

## Types <- System.Object

|Public Method|Description
----|----
|Equals|Same Value true
|GetHashCode|should be overrided when hash is used|
|ToString|return full name of type by default, this is expected to be aware of CultureInfo|
GetType|Instance of type-derived object. cannot be overrided
[System.Object Public Methods]

|Protected Method| Description
----|----
MemberwiseClone|new instance and identical to _this_
Finalize|called when GC.
[System.Object Protected Methods]

* __new__ operator:
	* calculate number and malloc.
	* initialize type object pointer and sync block index member
	* constructor called. from this level up to System.Object
	* __NO DELETE__ operator

## Type casting/safety
* Runtime type
	* CLR runtime check it.
	* InvalidCastException
* __is, as__
	* is: check
	* as: cast without raising exception.
* Namespaces and Assemblies