#Regular Expression
```
Character 	Description
. 			    Matches any single character except a newline.
* 			    Matches zero or more occurrences of the character immediately preceding it.
[chars] 	  Matches any one of the characters given in chars, where chars is a sequence of characters.
			      You can use the - character to indicate a range of characters. If the ^ character is the first
			      character in chars, one occurrence of any character that is not specified by chars is
			      matched.
^ 			    Matches the beginning of a line.
$ 			    Matches the end of a line.
\ 			    Treats the character that immediately follows the \ literally. This is used to specify patterns
			      that contain one of the preceding wildcards.
```
```
String Type 					      Expression
Blank lines 					      /^$/
An entire line 					    /^.*$/
One or more spaces 			    / */
HTML (or XML) Tags 			    /<[^>][^>]*>/
Valid URLs 						      /[a-zA-Z][a-zA-Z]*:\/\/[a-zA-Z0-9][a-zA-Z0-9\.]*.*/
Formatted dollar amounts 		/\$[0-9]*\.[0-9][0-9]/
```

#sed
```
	sed -n '/0\.[0-9][0-9]$/p' input_file    (-n avoid printing line, and "p" means print)
	sed '/^[Mm]ango/d' input_file 			 ("d" means delete)
	sed 's/eqal/equal/g' input_file 		 ("s" means substitute and "g" means global substitution)
	sed -e 's/Paech/Peach/' -e 's/ *[0-9][0-9]*\.[0-9][0-9]$/\$&/'   (-e multiple commands, "&" resue the string matched pattern1 in patter2)
```

#awk
#a. Normal usage
```
	awk '
		/ *\$[1-9][0-9]*\.[0-9][0-9] */ { print $0, $1, $2, "*"; }
		/ *\$0\.[0-9][0-9] */ { print ; }
	' input_file

	- $0 means whole line, $1, $2, ... means first field, second field, ...
	- print means print the line matching
	- /pattern/
```
#b. Conditions
```
	expression { actions; }
		Operator 				      Description
		< 						        Less than
		> 						        Greater than
		<= 						        Less than or equal to
		>= 						        Greater than or equal to
		== 						        Equal to
		!= 						        Not equal to
		value ~ / pattern/ 		True if value matches pattern
		value !~ / pattern/ 	True if value does not match pattern
```
#c. "next" action
```
	awk '
		($2 ~ /^\$[1-9][0-9]*\.[0-9][0-9]$/) && ($3 < 75) {
		printf "%s\t%s\t%s\n",$0,"*","REORDER" ; next; }
	' input_file

	- Use ";" to separte commands
	- && and ||
	- "next" tells awk to skip all the remaining patterns and expressions and instead read the next input line and start from the first 		     pattern or expression.
```
#d. Expressions
```
  awk ' /^ *$/ { x=x+1 ; print x ; }' $i   （if x is not defined, x will be 0 initially）
```
#e. BEGIN and END
```
	awk '
		BEGIN { actions }
		/pattern/ { actions }
		/pattern/ { actions }
		END { actions }
	' input_file
```
#f. Built-in Variables in awk
```
	Variables 		Description
	FILENAME 		  The name of the current input file. You should not change the value of this variable.
	NR 				    The number of the current input line or record in the input file. You should not change the
					      value of this variable.
	NF 				    The number of fields in the current line or record. You should not change the value of this
					      variable.
	OFS 			    The output field separator (default is space).
	FS 				    The input field separator (default is space and tab).
	ORS 			    The output record separator (default is newline).
	RS 				    The input record separator (default is newline).
```
#g. Delimiters
```
	MYFS=: ; export MYFS ; awk -F${MYFS} '{ ... }'
	awk 'BEGIN { FS=":" ; } { print $1 , $6 ; }' /etc/passwd

	awk 'script' awkvar1=value awkvar2=value ... files
```
#h. Flow Control
```
	if (expression1) {
		action1
	} else if (expression2) {
		action2
	} else {
		action3
	}

	awk 'BEGIN{ x=0 ; while (x < 5) { x+=1 ; print x ; } }'

	awk '{
		for (x=1;x<=NF;x+=1) {
			printf "%s ",$x ;
		}
		printf "\n" ;
	}' input_file
```
