---
title: 5_Result Codes, Chaining and Flags
tags: shell
grammar_cjkRuby: true
grammar_tableExtra: true
---

* Working with result Codes
	* if ...: use result code
	* $?: last result code.
	* and operator: ls myfile && echo "File Exist"
* Chaining Execution: and &&, or || , not !
	* && : if success, then run right (only one right)
	* || : if fail, run right.
	* !: run right
* Flags and Arguments
	* $#: number of args
	* $\*: expands the list of arguments, from $1
		* outside "",
		* inside "", IFS used
	* $@: expands to the list of args, from $1
		* outside "": arg split is not defined
		* within "", 
		* "Blah$@Blah", Blah is append to the first and last argument
	* shift: + num, remove arguments from the arg list.
	* getopts builtin, getopt command:
```bash
getopts optstring user_specific_vars [args]
```

