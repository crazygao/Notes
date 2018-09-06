---
title: Compute-Bound Asynchronous Operations
tags: C#
grammar_cjkRuby: true
grammar_tableExtra: true
---

## CLR Thread Pool
* one thread pool per CLR, shared by all AppDomains.
* create and kill threads by thread pool.

## Performing a Simple Compute-Bound Operation.
* ThreadPool.QueueUserWorkItem(WaitCallback callback);

## Execution Contexts
* Security Settings
* Host settings
* Logical call context data
* ExecutionContext: SuppressFlow, RestoreFlow

## Cooperative Cancellation and Timeout
* Cooperative pattern: cancellation token.
* Register method: register a cancelled callback.
* useSynchronizationContext.
* Register and cancel:
	* cancel(true): call callbacks one by one. 1 fail will stop others.
	* cancel(false): call callbacks in a bunch.
* Linked CancellationTokenSource: ...
	* If any of linked is canceled, linked is cancelled
* CancelAfter

## Tasks
* new Task().Start() | Task.Run()
* TaskCreationOptions
	* None
	* PreferFairness
	* LongRunning
	* AttachedToParent
	* DenyChildAttach
	* HideScheduler
* Wait for Task Complete and Get Result.
	* Task.Start();
	* Task.Wait();
	* Task.Result,
	* If fail, store exception in collection, when Wait or Result, will be thrown
	* 
