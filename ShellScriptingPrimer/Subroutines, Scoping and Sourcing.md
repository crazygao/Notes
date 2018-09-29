---
title: Subroutines, Scoping and Sourcing
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
echo "
```