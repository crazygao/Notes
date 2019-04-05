---
title: Introduction to Function Objects
tags: C++, Boost
grammar_cjkRuby: true
grammar_tableExtra: true
---

## About Command Design Pattern.
* Define `virtual void operator() () = 0`
* Compact other inputs into other functions.

## Predefined and User-defined functions
* set: eg: `set<long, less<long>> myset`
* transform: eg: `transform(vec.begin(), vec.end(), vec.begin(), MyExp<double>())`
* for_each: eg: `for_each(personSet1.begin(), personSet1.end(), &Print<Person>)`

### Function adapters for member functions and ordinary functions.
* binary_function, unary_function, bind1st, bind2nd are deprecated.
