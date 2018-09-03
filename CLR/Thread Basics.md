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