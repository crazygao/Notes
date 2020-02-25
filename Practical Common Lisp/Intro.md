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
| define a variable |
| push into a list |
| force output |
| read line |
| supplied-p feature |
| change value |
| reverse a list |


| Slime Functions |
| ---- |
| Close Parens |
| Compile File |
| Load File |
| Close Parentheses |
| Go back to REPL |
| _Check documentation_ |

%

| Name | Type | Usage |
| ---- | ---- | ---- |
| format | function | (format t "hello world")  |
| defun | function | (defun hello () (hello)) |
| ,quit / ,sayoonara | keyword | |
| load | function | (load "hello.lisp") |
| compile-file | function | (compile-file "hello.lisp") |
| list / ' | function | (list 1 2) / (list :a 1 :b 2) |
| getf | function | (getf (list 1) 1) |
| nth | function | (nth 2 '(1 2 3)) |
| defvar | marcro | (defvar \*db\* nil) |
| push | macro | (push item \*db\*) | 
| force-output | macro | Ensure Lisp doesn’t wait for a newline before it prints the prompt.
(force-output \*query-io\*)|
| read-line | function | Read from stream (read-line \*query-io\*) |
|||Define a parameter is provided (a "default" a-p)|
|setf | macro | setf {pair}* |
| reverse | function | (reverse '(1 2 3)) |
| defmacro | keyword | (defmacro backwards (expr) (reverse expr)) |



| Slime Command | Shortcut | Usage | 
| ---- | ---- | ---- |
| slime-close-parens-at-point | C-c C-q | match up Parens |
| slime-compile-defun | C-c C-c | Evaluate and compile |
| slime-load-file | C-c C-l | Load a file |
| slime-close-parens-at-point | C-c C-] | Close Parentheses |
||C-c C-z| Go back to REPL |
||C-c C-d C-d / C-c C-d h | Check documentation / online docs |

