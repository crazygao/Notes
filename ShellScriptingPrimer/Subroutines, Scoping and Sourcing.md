---
title: 6_Subroutines, Scoping and Sourcing
tags: shell
grammar_cjkRuby: true
grammar_tableExtra: true
---

* Shell: subroutines, functions
	* no exceptions

## Subroutine Basics
```bash
mysub()
{
	echo "Arg1: $1"
	return 3
}
mysub "This is an arg"
echo "Subroutine returned $?"
```

## Anonymous Subroutines
```bash
tar -cf - file1 file2 file3 | \
	{ if cd "/destination"; then tar -xf -; fi; }
```

## Variable Scoping
* Declare a local variable
	* `local` keyword:
	* If subroutine call subroutine, the variable is inherited.
* Using global variables
	* You can freely use global vars
	* Cannot use variable shadowed by local vars
	* cannot change global variables during inline execution.

## Including One Script into Another1
* `.`, `source`
* Finding Absolute Path of Current Script

```bash
SCRIPT="$(which $0)"
if [ "x$(echo $SCRIPT | grep '^\/')" = "x" ] ; then
	SCRIPT = "$PWD/$SCRIPT"
fi
```