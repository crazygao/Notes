---
title: Thread Basics
tags: C#
grammar_cjkRuby: true
grammar_tableExtra: true
---

## Thread Overhead
* Thread Kernel object: thread context
* Thread environment block(TEB): 
	* exception-handling chain
	* TLS
	* GDI / OpenGL data structures
* User-mode stack.
* Kernel-mode stack.
* DLL thread-attach and thread-detach nofications

## Dedicate thread to perform async compute-based operation
* Create a thread when
	* Nice your Priority
	* thread behave as foreground thread.
	* LONG-RUNNING
	* start a thread and possibly abort it by Thread.Abort()
* Create Thread
	* System.Threading.Thread
	* delegate void ParameterizedThreadStart(Object obj)

## Reason to Use Threads
* responsiveness (client GUI apps)
* Performance (client - server applications)

## Thread Scheduling and Priorities
* Priority 0-31
* Process Priority Class: Idle, Lowest, Below Normal, Normal, Above Normal, Highest, Time-Critical
* Thread Priority Class: Idle, Below Normal, Normal, High, Realtime.
* Desktop apps: System.Diagnostics.{ Process, ProcessThread }

## Foreground Thread vs. Background Thread.
* When ALL foreground threads STOP running, CLR forcibly ends any background thread, no exception.
* Thread.IsBackground = true/false
* ThreadPool default is background threads, thread created by native code that enter the managed ececution environ are background.