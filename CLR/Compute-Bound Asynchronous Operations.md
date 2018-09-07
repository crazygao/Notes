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
	
### Inside a Task
* Fields
	* Task ID: int32: Task.CurrentId
	* Task State: int32, TaskStatus
		* Created, WaitingForActivation, WaitingToRun
		* Running, WaitingForChildrenToComplete,RanToCompletion, Canceled, 
		* Faulted: task.Exception to get Exceptions.
	* Ref to parent task
	* Ref to TaskScheduler
	* Ref to callback method
	* Ref to object to be passed to callback
	* Ref to ExecutionContext
	* Ref to ManualResetEventSlim
	* Supplimentary state:
		* CancelklationToken
		* ContinueWithTask
		* child tasks
* Dispose of task:
	* implement IDisposable.
	* Don't call it ,but called by GC.
* Task Factory: create a bunch of tasks with same configurations.
	* a lot of tasks could be inside one task factory

### Task Scheduler
* TaskScheduler: use Default
* TaskScheduler.FromCurrentSynchronizationContext(): get GUI thread.

## Parallels static for, foreach, invoke
* ParallelOptions: CancellationToken, MaxDegreeOfParallelism, TaskScheduler
* For and ForEach overloads:
	* localInit: delegate invoke once for each task participating in the work
	* body: invoke once for each item being processed by the various threads participating in the work
	* localFinally: invoke once for each task participating the work, After.
	* ParallelLoopState: 
	* ParallelLoopResult:

## Parallel language Integrated Query
* Change IEnumerable to ParallelQuery:  .AsParallel() extension method.
	* get back: .AsSequential() method
* query.ForAll(Action): perform calculation on each result.
* Preserve order: .AsOrder method
	* get back: .AsUnordered

## Periodic Compute-Bound Operation
* Timer:
	* TimerCallback
	* Object state:
	* duetime: milliseconds to wait before callback for first time
	* period: how long to wait before each successive call to the callback.
	* .Change: change duetime and period
	* .Dispose: cancel the timer.
* Differentiate timers:
	* System.Threading.Timer: perform periodic background tasks
	* System.Windows.Forms.Timer: WM_TIMER into the thread message queue. all works in one thread.
	* System.Windows.Threading.DispatcherTimer: for Silverlight and WPF apps.
	* Windows.UI.Xaml.DispatcherTimer: for WIndows Store apps.
	* System.Timers.Timer: DONT USE.

## How ThreadPool Manage Its Threads
* blackbox: trust it...

### Setting Thread Pool Limits.
* Concept is unlimited:
	* Truth is at most 1360 threads. -> OutOfMemoryException.
	* ThreadPool support static methods to set limits.

### How Worker Threads Are Managed
* 