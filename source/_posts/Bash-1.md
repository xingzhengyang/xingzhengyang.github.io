---
title: Bash Notes
---
# Bash

## Bash Commands

#### curl

Transfer to/from URL

> Curl ${URL} -O //to download it

#### date

Show the date

#### echo

Print the following string(notice a format string in c)

`echo` is a type of write ,which will take place of the previous content of a file with new content.

#### pwd

Print working directory

#### cd

change directory

**.. means the last directory**

-(dash) means the previous working directory (back)

Use cd ../../ to back to the third last directory

#### ls

List 

#### help

Command -help

#### mv

Use mv to rename or move a file

#### cp

copy file

`copy source target`

```bash
copy source target
```

#### rm

```bash
rm -R directory
```

Use -R to fully delete the directory (password needed)

#### rmdir

```bash
rmdir directory
```

Remove an empty directory

#### mkdir

Make a directory, followed by one string

```bash
mkdir hello\ world
mkdir "hello world"
echo instead\ of\ hello world
```

#### man

Manual to a command

**q to quit**



#### cat

`cat` to view the file

```bash
cat < hello.txt > bash.txt
```



#### tail

```bash
tail -n1
```

Use this to view the last one line of the list



#### grep

```bash
grep -i content-length curl-content
```



#### sudo 

do as a super user

Password acquired

```bash
sudo su
```

use this command to have a `root` permission



#### chmod

`chmod` can change file mode. 

Mode number can be added.

```bash
chmod 0777 file
```

The command above gives the rwx permission to three groups of users.



#### grep

`grep` can find certain content in the file.

```bash
grep last-modified file
```

get the line.

```bash
grep -R content .
```

search the content in the directory `.`





#### diff

`diff` can show the difference between two strings.



#### find

use `find` to make batch operation possible. 

```bash
find foo?.py -exec rm {} \;
```





## Bash stream

Rewire the I/O stream

```bash
> file //to the file
< file //from file
```

`<` stands for output from the file

`>` stands for input to the file

```bash
echo hello > bash.txt
```

`>>` stands for append

` a | b ` is pipe, which is like a real pipe which will transcend content between a and b. 

Here is an example of pipe:

```bash
ls -l / | tail -n1 > ls.txt 
```

Firstly, `ls -l / `gives an output to `tail` as an input, then `tail` use it to show the last line ,then the last line is written into the `ls.txt` file.

```bash
echo 1050 | sudo tee brightness
```

# File mode

`ls -l` can give you the long format of the file information which includes the `file mode`.

File mode in linux (or unix-like system like macos) is like below:

```bash
-rwxr--r--
```

The file mode can be interepted into 4 groups:

the first one letter,`d` or '-' ,shows that whether it is a directory or not.

The following three groups are respectively permissions hold by owner, users and other.

`r` for read, `w` for write, and `x` for execute.

use `chmod` to change file mode.



# Bash Script

### Notations

`$` for variable. For example, 

```bash
foo=bar	#there should be without any space
echo $foo
# bar
```

`""` For string but with format.

```bash
echo "this is foo : $foo"
```

However, `''`is quite different in this point.

```bash
echo 'this is foo : $foo'
#this will give a simple string
```

`.sh` is a type of shell script used by bash.

use `source` command to make it a source shell command instead of being a text file

some variable names are reserved for functions.

`$0` is the name of the command, `$?` is the last command's error bool, `$_` is the last variable of the function.

`$#` is number of arguments(argc), `$$` is the pid of the process, `$@` will expand to all the arguments.

`||` is quite different from which we have learned in c. It is a choose sentence.

```bash
grep what file || echo 'can not find the line'
```

`||` means if the previous one is false, then do the latter one.

`&&` is opposite to `||`

`;` will separate two sentences

Use `()` to make format string in bash, which is like `{}` in python.

```bash 
echo "this is pwd: $(pwd)"
```

```bash
#!/bin/bash

echo "date: $(date)"

echo "running program $0 with $# argvs with pid $$"

for file in "$@"; do
	grep foobar "$file" > /dev/null 2> /dev/null
	if [[ "$?" -ne 0 ]]; then
		echo "File $file does not have any foobar"
		echo "# foobar" >> "$file"
	fi
done
```

this is an example of a loop and condition in bash script.

`-ne` is short for `not equal` , and `if` `;` `then` `fi` gives a conditional sentence part.

`*` for any , `?` For not finished line(only stands for one character)

`#!` notation is a special command to let the file be runned in certain way, like in python.

```bash
#!/usr/bin/python
```

`\` is similar to C, which can be `\;` or something else to be a special character.
