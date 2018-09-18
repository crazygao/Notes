---
title: Shell Variables
tags: shell
grammar_cjkRuby: true
grammar_tableExtra: true
---
# Shell Variables[^1x]
[^1x]: 曾经在Yinxiang上有一篇，并不详细。

## Shell Variables and Printing
* reference and dereference a variable.
```bash
FIRST_ARGUMENT="$1"
echo "Hello, world $FIRST_ARGUMENT!"
```

* Special Chars
	* Use args that contain SPACES , SLASHes
		* use "" to quote the strings.
		* especiallly making Filenames
	* Use quotation marks in string
		* backslash

```bash
MYSTRING="The word of the day is \"sedentary\"."
```

## Export Shell Varibles
* _export_ buildin
    * Careful: Export once will take effect during the time!

## Override Env for Child Process
```bash
MYVAR=7 ./printmyvar.sh
```

## Delete Shell Variables
* unset:
    * eg: unset MYVAR

