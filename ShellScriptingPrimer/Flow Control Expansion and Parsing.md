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
	* `for in ; do done`
		* for i in \*.jpg: for and shell globbing.
		* for i in a b c\ d: Careful for IFS
	* `for (( i = 1 ; i <= $1 ; i++ )) ; do done`
		* not portable, use while instead
* `case` statement: 
	* \* is equivalent to default in C

```bash
case expression in
    [(] value | value | value | ... ) command; command; ... ;;
    [(] value | value | value | ... ) command; command; ... ;;
    ...
esac
```
* `expr` Command: String and Integer Math
	* expr accept EXPRESSION or COMMANDS surrounded by quotes.
	* support string compare, logic or, logic and.
	* support basic regular ezxpressions.

```bash
expr "This is a cat" '<' "I am a person"
NAME=`expr "$1" '|' "Untitled"`
expr "$STRING" : '.*\(....])est'
```

## Parsing, Variable Expansion and Quoting

* Passes in processing
	1. Parsing pass: extract code
	2. Expansion pass: variable expanded and inline exection performed
	3. Execution pass.
* Variable expansion and field separator
	* IFS
* Special Char Quoting
	* Shell Expansion happens in double quoting.
* Inline Execution: place its output in the middle of another command, not return value.
	* $(): can be safely nested
	* \`\`: cannot be nested.
	* evaluation of inline commands, occurs after the statement is parsed. it is safe to return quotations or others into outputs

```bash
FOO=1; BAR=3
echo "Try this command: `echo $FOO`"
echo "Try this command: `echo $FOO + "$(expr $BAR + 1)"`"
```