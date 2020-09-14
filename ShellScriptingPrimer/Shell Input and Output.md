---
title: 3_Shell Input and Output
tags: shell
grammar_cjkRuby: true
grammar_tableExtra: true
---
# Shell Input and Output
read and write files using _echo_, _printf_, _read_, _cat_, pipes and redirection.

## printf and read
* `printf` and `echo`
	* printf: NO '\n' at end of line
* `read`: take a line and separates into args
	* IFS: separators settings
	* read definite number of inputs
	* use `eval` for unknown number of params

```bash
IFS="q"
read NUMBER1 NUMBER2
```
* `cat`: bulk IO
	* cooperate with redirect operators.
	* don't need to echo on each line.

```bash
cat > file.c << EOF
```

## Pipes and Redirection
* Special file descriptor fd: stdin 0, stdout 1, stderr 2
* Operators against these fds
	* `>`: redirect operator, stdout create a file
	* `>>`: stdout append a file
	* `>&`: stdout + stderr merge redirect to create a file
		* use 2>&1 for a more compatible way.
* Pipes and fd redirection (Bash)
	* `|`: pipe operator, stdout to next stdin.