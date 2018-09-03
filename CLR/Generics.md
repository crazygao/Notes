---
title: Generics
tags: C#
grammar_cjkRuby: true
grammar_tableExtra: true
---

* Generics: algorithm reuse.
	* Proper use of generics improve performance.

## Generics In FCL
* Sysem.Collections.{Generic, ObjectModel, Concurrent}
* Open and closed types:
	* open : generic type with un-materialized type parameter
		* cannot be initialized
	* Use inherit for Partial Defined Specification: with out type inference.
		* Dict<TValue> : Dictionary<String, TValue>
	* typeof(): return a Type object
	* Activator.createInstance(Type T): create object with default constructor()
* Generic Types and Inheritance: be clear about which part should be in generic
* Genric Type Identity:
	* using TypeB = some materialized Genrics

## Code Explosion

## Generic Interfaces

## Generic Delegates
* generic delegate pass value type without boxing -> pass by reference
* delegate: = 4 methods
	* constructor
	* Invoke
	* BeginInvoke
	* EndInvoke

## Delegate & Interface contra-variant and covariant generic type arguements
Generic variant
* Invariant: type params cannot be changed.
* contra-variant: _in_ can change from a class to a class derived from it.
* covariant: _out_ can change from a class to a class base.
* means same il code on inherited types.

```csharp
public delegate TResult Func<in T, out TResult>(T arg);
Func<Object, ArgumentExceptioln> fn1 = null;
Func<String, Exception> fn2 = fn1; // no cast required
Exception e = fn2("");
```

## Generic Methods

## Generics and Other Members
* properties, indexers, events, operators, constructors, finalizers __CANNOT__ have type parameters.

## Verifiability and Constraints

[To Be Continued]

