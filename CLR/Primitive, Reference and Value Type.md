---
title: Primitive, Reference and Value Type
tags: C#
grammar_cjkRuby: true
grammar_tableExtra: true
---
## Primitives
* FCL primitive types
	* sbyte, byte
	* short, ushort
	* int, uint
	* long, ulong
	* char: 16bit Unicode char.
	* float, double: 32bit , 64bit
	* bool
	* decimal: 128bit high-precision float, no rounding errors
		* 1bit sign, 96bit value, 8bit power10, unused
	* string
	* object
	* dynamic
* Primitive castings: 
	* int32->int64 (safe), int64->int32 (unsafe)
	* Conversions.
* Checked and unchecked Primitive Type Operations
* NO OVERFLOW EXCEPTION by default
	* overflow and wrap
	* VB: overflow is error.
	* C# an VB generate different IL instructions.
	* compile with /checked+ will enable overflow exception
	* or using code:  __checked/unchecked__ operator , statement.

## Reference Types and Value Types
* System.ValueType