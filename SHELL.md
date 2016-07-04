```
Ctrl + a
	- move cursor to begining
Ctrl + e
	- move cursor to end
$
	- vi command move cursor to end
0
	- vi command move cursor to begining
cp -r
	- copy directory to destination
ln -s source destination
chown -R
chmod -R
chgrp
Crtl + Z
	- suspend process
bg
	- resume suspended process
bg %#
	- resume suspended process to background
fg %1
	- bring background process to foreground
wait %1
	- wait for background process to finish
jobs
	- suspended and background jobs
exec
	- overlaying current process
array
	- name[index]=value
	- set -A name value1 value2 ... valuen
	- name=(value1 ... valuen)
access array variable
	- ${name[index]}
	- ${name[*]}
	- ${name[@]}
unset name
	- unset variable
substitution
	Wildcard 				Description
	* 						Matches zero or more occurrences of any character
	? 						Matches one occurrence of any character
	[characters] 			Matches one occurrence of any of the given characters
	[!characters]			Matches one occurrence except any of the given characters
	${parameter:-word} 		If parameter is null or unset, word is substituted for parameter. The
							value of parameter does not change.
	${parameter:=word} 		If parameter is null or unset, parameter is set to the value of word.
	${parameter:?message}	If parameter is null or unset, message is printed to standard error. This
							checks that variables are set correctly.
	${parameter:+word} 		If parameter is set, word is substituted for parameter. The value of
							parameter does not change.

if list1
then
	list2
elif list3
then
	list4
else
	list5
fi
[ ! option file ]
-d file
-f file
Option 					Description
-z string 				True if string has zero length.
-n string 				True if string has nonzero length.
string1 = string2 		True if the strings are equal.
string1 != string2 		True if the strings are not equal.
int1 -eq int2 			True if int1 equals int2.
int1 -ne int2 			True if int1 is not equal to int2.
int1 -lt int2 			True if int1 is less than int2.
int1 -le int2 			True if int1 is less than or equal to int2.
int1 -gt int2 			True if int1 is greater than int2.
int1 -ge int2 			True if int1 is greater than or equal to int2.

case word in
	pattern1)
		list1
		;;
	pattern2)
		list2
		;;
	esac

while command
do
	list
done

for name in word1 word2 ... wordN ("$@")
do
	list
done

$0  - The name of the command being executed. For shell scripts, this is the path with which it was invoked.
$n  - These variables correspond to the arguments with which a script was invoked. Here n is a positive decimal number corresponding to the 	  position of an argument (the first argument is $1, the second argument is $2, and so on).
$# 	- The number of arguments supplied to a script.
$*  - All the arguments are double quoted. If a script receives two arguments, $* is equivalent to $1 $2.
$@  - All the arguments are individually double quoted. If a script receives two arguments, $@ is equivalent to $1 $2.
$? 	- The exit status of the last command executed.
$$ 	- The process number of the current shell. For shell scripts, this is the process ID under which they are executing.
$!  - The process number of the last background command.

command | tee file
	- output to standard output and to a file

Standard Input (STDIN), 0
Standard Output (STDOUT), 1
Standard Error (STDERR), 2
command 1> file1 2> file2
/dev/null
command > file 2>&1

functions
	- name () { list ; }

eval any-UNIX-command
	- reprocess command

:
	- shell command, does nothing but return 0

type commmand
	- fully path name of command
which command

sort -rn (reverse & number)
sort -k start,end files (sort specific column)
uniq -c (count)

find <path> -name <name> -type <d or f> -print -mtime +n|n|-n -size +n|n|-n -exec <command> {} \;

xargs
	- is a command that accepts a list of words from standard input and provides those words as arguments to a given command:
	- cat filelist | xargs rm

/bin/bash
	-n Reads all commands, but does not execute them.
	-v Displays all lines as they are read.
	-x -Displays all commands and their arguments as they execute. This option is often referred to as the shell tracing option.
```
