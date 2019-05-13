---
title: Vim programming
tags: Vim
grammar_cjkRuby: true
grammar_tableExtra: true
---
## Variables
* let
	* let &textwidth = 80
	* let &l:number = 1
	* let @a = "hello"

## Variable Scoping
* :help internal-variables

## Conditionals
* if
	* :if 1 :echom "ONE" :endif
* else, elseif
* "==" is depends on user's settings, such as ignorecase
	* ==?, case-insensitive no matter what the user has set.
	* ==#, case-sensitive no matter what the user has set.
	* :help expr4

## Coersion
* 10 + "20foo" = 10 + 20
* String start with number are coerced to that number. "20foo" = 20

## Function
* :function Meow() :endfunction
* function should start with Capital Letter if unscoped.
* call, execute function and drop the return value.
* function return 0 by default.

## Function Arguments
* use function scope , a:
* Vary arguments.
	* a:0 , number of arguments
	* a:000 , list of arguments
	* a:1, a:2 , 1st/2nd argument

## Numeric Types
* Decimal: 100
* Hexical: 0xff
* Octal: 010
* Float: 100.1
* Exponential: 5.34e+3

## Strings
* Concat: "Hello" + " World", not stable
* String Concat: "Hello" . " World"
* Special Chars: \\, \n
* Literal Strings: use single quote.

## String Functions
* strlen: when string =len
* split: split("one two three", " ")
* join: join(["foo", "bar"], "...")
* tolower, touppe

## Execute
execute evaluate a string as if it were a Vimscript command.
* `execute "echom 'Hello, world'"`
* something like javascript eval.

## Normal
* normal: execute user input command in normal mode.
* TAKE mapping into account.
* normal!: don't take mapping into account.

## Execute Normal!
* eg: `:execute "normal! mqA;\<esc>``q"`
