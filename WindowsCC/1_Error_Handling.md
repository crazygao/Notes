---
title: 1_Error_Handling
tags: Windows
grammar_cjkRuby: true
grammar_tableExtra: true
---
## Basics

| Data Type| Value to indicate failure|
| ---------- | ---------------------------------------------------------------------------------------- |
| VOID       | This function cannot possibly fail.                                                      |
| BOOL       | if fails, return 0.                                                                      |
| HANDLE     | if fails, return `NULL` or `INVALID_HANDLE_VALUE`                                        |
| PVOID      | if fails, return `NULL`; otherwise, `PVOID` identifies the memory address of a data block |
| LONG/DWORD | CHECK DOCUMENTATION|

* GetLastError():
	* use `,hr` in debugger to check error message.
* FormatMessage():
* SetLastError(): set your own error codes.
* 