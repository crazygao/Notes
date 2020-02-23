---
title: Intro 
tags: Lisp
grammar_cjkRuby: true
grammar_tableExtra: true
---
| Table | 
| ---- |
| format |
| define a function |
| quit lisp |
| load file |
| compile file |
| make CLO list |
| get plist by property |
| get by index |


| Slime Functions |
| ---- |
| Close Parens |
| Load File |

%

| Name | Type | Usage |
| ---- | ---- | ---- |
| format | function | |
| defun | function | |
| ,quit / ,sayoonara | keyword | |
| load | function | (load "hello.lisp") |
| compile-file | function | (compile-file "hello.lisp") |
| list / ' | function | (list 1 2) / (list :a 1 :b 2) |
| getf | function | (getf (list 1) 1) |
| nth | function | (nth 2 '(1 2 3)) |


| Slime Command | Shortcut | Usage | 
| ---- | ---- | ---- |
| slime-close-parens-at-point | C-c C-q | match up Parens |
| slime-compile-defun | C-c C-c | Evaluate and compile |
| slime-load-file | C-c C-l | Load a file |
