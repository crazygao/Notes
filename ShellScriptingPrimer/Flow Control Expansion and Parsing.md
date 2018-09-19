---
title: Flow Control Expansion and Parsing
tags: shell
grammar_cjkRuby: true
grammar_tableExtra: true
---
## Basic control statement
* `if ; then else fi` statement:Distinctions with other `if`
	* the test performed is EXECUTION of a command, depend on result, it execute the statement that follows it. 
	* keywords like `true`, `false`, are programs. return of 0 is true, others are false.
* the test command and bracket notation `[]`
	* `[` is a command, see manual by using `man \\[`
	* `[ -d "filename" ]`: check file name etc.
* `while ; do done` statement:
	* same as if statement
	* terminate the loop with `break` or skip with `continue`
	* break or continue multiple enclosing loops.
* `for` statement: Iterate through items in list.
	* 