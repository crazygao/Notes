---
title: 28 I/O Bound Async Operations
tags: 
grammar_cjkRuby: true
grammar_tableExtra: true
---

# I/O Bound Async Operations
* Allow devices to handle the task.

## How the compiler transfom a Async Function into a State Machine.
* suspend and resume: .GetAwaiter, extension method
* IsCompleted property:
	* if true, executing forward -> GetResult
	* if false, async, .AwaitUnsafeOnCompleted()
* TaskLogger* : debug scenarios when app hang.
* Task.Factory.FromAsync: change Old pattern Begin End, with new async functions.
* Use Task.Run to stop async function to run synchronously and block gui thread.

[Read Again, after this implementation]