# Bash scripts basics
### Selecting interpreters using shebang
`#!/bin/bash` or `#!/bin/sh`

### Commenting
`# comments start with the hash sign`
```
: '
    This i multi line 
    comment
'
```

### Variables
***String vals***
`VARIABLE_NAME="Some text"`
***Using variables***
`$VARIABLE_NAME`
***Reading arguments passed to script while executing with ./program.sh***
* `$*` this reads every args in `./program.sh arg1 arg2 ...`
* `$<number>` access individual variables e.g.`$1` will access `arg1`

***Accessing commands exit status in terminal***
`$?`: exist status `0` is true, `1` is false. 

***View all variables in the bash envinronment***
type `declare -p` in terminal

#### Conditional statements
* `-eq`: equal 
* `-ne`: not equal
* `-lt`: less than
* `-le`: less then or equal
* `-gt`: greater than
* `-ge`: greater than or equal
* `( EXPRESSION )`: returns the value of the expression
* `! EXPRESSION`: negate operator
* `EXPRESSION_1 && EXPRESSION_2`: logic AND
* `EXPRESSION_1 || EXPRESSION_2`: logic OR
* `== and !=`: For string comparisons, string to the right is used as a pattern and patter matching is performed
* `=~`: String to the right is used as regex  

For file/string and other operators look details of `help test`

### If statements
***if then*** use help if in terminal for extra information
```
if [[ CONDITION ]]
then 
    STATEMENTS 
fi # every if statements finishes with fi (if backwards)
```
***if then elif then else***
```
if [[ CONDITION ]]
then
    STATEMENT
elif [[ CONDITION ]]
then
    STATEMENT
else
    STATEMENT
fi
```
***if then for numeric comparisons*** these comparisons can use operators as <, >, <=, >=, etc..
```
if (( CONDITION )) # in this way you can reference numeric variables directly with VARNAME instead of $VARNAME
then  
    STATEMENT
fi
```
### For loops
***for (( i = 0; i < n; i++ )) statements***
```
for (( expression1; expression2; expression3 ))
do 
    COMMANDS
done
```
### While loops
```
while [[ CONDITION ]]
do
    STATEMENTS
    (( VAR-- )) # or (( VAR++ ))
done
```
### Until loop
```
until [[ CONDITION ]]
do
    STATEMENT
done
```
until loop will execute the loop until a condition is met, very similar to while loop  
until will execute the statement inside the loop at least once
### Numeric operations
All operations should be encapsuled by `(( OPERATION ))` otherwise bash will treat it as a string.  
When assigning the result to a new varibale use `newVar=$(( OPERATION ))` 

### Arrays
Declaration: `ARRNAME=("firstItem" "secondItem")`
Accessing values: `${ARR[0]}`
Accessing all values: `${ARR[*]}` or `${ARR[@]}`

### Functions
Declaration
```
FUNCTION_NAME(){
    STATEMENTS
}
```
Calling a function
* without argument `FUNCTION_NAME`
* with argument `FUNCTION_NAME arg1`

***RANDOM***
Set random range with % operator `RANDOM % 70` will return random int in the range of 0-69
***Read user input***
`read VARNAME` reads userinput and assign it to VARNAME