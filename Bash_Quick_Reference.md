# <center> Bash Quick Reference </center>

## Bash Variable Conditionals Inline

**1. Variable Assignment (:=):**

```bash
variable_name="value"   # Assign a value to a variable
```

**2. Default Value Assignment (:-):**

```bash
default_variable=${variable_name:-default_value}
#If variable_name is set, it will be used.
    If variable_name is not set or is empty, default_value will be used.
```

3. Default Value Assignment and Set (:=):
bash

default_variable=${variable_name:=default_value}

    If variable_name is set, it will be used.
    If variable_name is not set or is empty, default_value will be used, and variable_name will be set to default_value.

4. Use Default if Unset or Null (:+):

bash

result=${variable_name:+default_value}

    If variable_name is set and not null, default_value will be used.
    If variable_name is unset or null, nothing is assigned to result.

5. Check if Variable is Set (:?):

bash

if [ -z "$variable_name" ]; then
    echo "Variable is not set."
else
    echo "Variable is set."
fi

    -z checks if the length of the string is zero (empty).

6. Use Default if Unset or Null (:-):

bash

result=${variable_name:-default_value}

    If variable_name is unset or null, default_value will be used.
    If variable_name is set and not null, its value will be used.

7. Conditional Ternary Operator (?:) - Alternative:

bash

result=$([ "$condition" = "true" ] && echo "true_value" || echo "false_value")

    Depending on the condition, it assigns one of two values to the result variable.

8. Conditional Ternary Operator (?:) - Alternative using if:

bash

if [ "$condition" = "true" ]; then
    result="true_value"
else
    result="false_value"
fi

    A more readable way to achieve conditional assignment.

These are some common uses of colons and similar symbols in Bash scripting. They allow you to handle variable assignments and conditional checks more efficiently.

---

## Bash String Manipulation Cheatsheet

1. String length: ${#string}
   Example: string="Hello, World!"; echo ${#string} - Outputs 13
2. Substring: ${string:position:length}
   Example: string="Hello, World!"; echo ${string:7:5} - Outputs World
3. Replace first match: ${string/pattern/replacement}
   Example: string="Hello, World!"; echo ${string/o/a} - Outputs Hella, World!
4. Replace all matches: ${string//pattern/replacement}
   Example: string="Hello, World!"; echo ${string//o/a} - Outputs Hella, Warld!
5. Replace beginning: ${string/#pattern/replacement}
   Example: string="Hello, World!"; echo ${string/#Hello/Hi} - Outputs Hi, World!
6. Replace end: ${string/%pattern/replacement}
   Example: string="Hello, World!"; echo ${string/%World/Everyone} - Outputs Hello, Everyone!
7. Remove shortest match from beginning: ${string#pattern}
   Example: string="Hello, World!"; echo ${string#*,} - Outputs  World!
8. Remove longest match from beginning: ${string##pattern}
   Example: string="Hello, World!"; echo ${string##*,} - Outputs  World!
9. Remove shortest match from end: ${string%pattern}
   Example: string="Hello, World!"; echo ${string%World*} - Outputs Hello,
10. Remove longest match from end: ${string%%pattern}
    Example: string="Hello, World!"; echo ${string%%,*} - Outputs Hello

---

## Bash Redirection Cheatsheet

1. command > file: Redirects the standard output from command to file. Overwrites file.
   Example: echo "Hello, World!" > output.txt - Writes "Hello, World!" to output.txt.
2. command >> file: Redirects the standard output from command to file. Appends to file.
   Example: echo "Hello, again!" >> output.txt - Appends "Hello, again!" to output.txt.
3. command 2> file: Redirects the standard error from command to file. Overwrites file.
   Example: ls /nonexistent 2> error.txt - Redirects error message to error.txt.
4. command 2>> file: Redirects the standard error from command to file. Appends to file.
   Example: ls /nonexistent 2>> error.txt - Appends error message to error.txt.
5. command &> file: Redirects both the standard output and the standard error from command to file. Overwrites file.
   Example: ls /nonexistent &> output_and_error.txt - Redirects both output and error to output_and_error.txt.
6. command < file: Takes file as input to command.
   Example: sort < unsorted.txt - Sorts the contents of unsorted.txt.
7. command1 | command2: Pipes the standard output of command1 to the standard input of command2.
   Example: ls -l | grep ".txt" - Lists all .txt files in the current directory.

---

## Bash Parameter Expansion Cheatsheet

1. :- : Provide a default value for a variable. If the variable is unset or null, the expansion of word is substituted instead.
2. :+ : The opposite of :- . If the variable is set, it will return the value of word, otherwise it returns nothing.
3. := : Similar to :- but it also assigns the word to the variable if the variable was unset or null.
4. :? : Display an error message if the variable is unset or null.
5. : : Expand the variable and return its value. If the variable is unset or null, it returns null.

---

## Bash If Conditions

# Basic if statement structure

if [ condition ]; then
    # Commands to execute if the condition is true
fi

# Common test flags for string comparisons

[ -z "$string" ]         # True if the string is empty
[ -n "$string" ]         # True if the string is not empty
[ "$string1" = "$string2" ]   # True if the strings are equal
[ "$string1" != "$string2" ]  # True if the strings are not equal

# Common test flags for file attributes

[ -e "$file" ]           # True if the file exists
[ -f "$file" ]           # True if the file exists and is a regular file
[ -d "$dir" ]            # True if the directory exists
[ -r "$file" ]           # True if the file is readable
[ -w "$file" ]           # True if the file is writable
[ -x "$file" ]           # True if the file is executable

# Numeric comparisons

[ "$num1" -eq "$num2" ]  # True if num1 is equal to num2
[ "$num1" -ne "$num2" ]  # True if num1 is not equal to num2
[ "$num1" -lt "$num2" ]  # True if num1 is less than num2
[ "$num1" -le "$num2" ]  # True if num1 is less than or equal to num2
[ "$num1" -gt "$num2" ]  # True if num1 is greater than num2
[ "$num1" -ge "$num2" ]  # True if num1 is greater than or equal to num2

# Logical operators

[ condition1 ] && [ condition2 ]   # True if both conditions are true
[ condition1 ] || [ condition2 ]   # True if either condition1 or condition2 is true
! [ condition ]                     # True if the condition is false

# Combining multiple conditions

if [ condition1 ] && [ condition2 ]; then
    # Commands to execute if both conditions are true
elif [ condition3 ] || [ condition4 ]; then
    # Commands to execute if either condition3 or condition4 is true
else
    # Commands to execute if none of the conditions are true
fi

---

## Bash If Conditionals Cheatsheet

1. Basic if statement:
if [ condition ]
then

# commands

fi
2. If-else statement:
if [ condition ]
then

# commands

else

# commands

fi
3. If-elif-else statement:
if [ condition ]
then

# commands

elif [ condition ]
then

# commands

else

# commands

fi
4. Nested if statement:
if [ condition ]
then
  if [ condition ]
  then
    # commands
  fi
fi

---

## Bash Common Uses Cheatsheet

1. echo : Used to print data to the terminal.
2. read : Used to read input from the user.
3. if..else : Used for conditional statements.
4. for : Used for looping over a sequence of numbers or array elements.
5. while : Used for looping as long as a condition is true.
6. case : Used for pattern matching and choice selection.
7. function : Used to define a block of code that can be reused.
8. exit : Used to end the script with a status.
9. trap : Used to respond to signals and system events.

---

## Bash Command Substitution Cheatsheet

1. $(command) : This is the preferred method for command substitution in bash. It allows for nesting.
   Example: echo "Today is $(date)" - This will print "Today is " followed by the current date.
2. `command` : This is the old method for command substitution. It can be difficult to use with complex or nested commands.
   Example: echo "Today is `date`" - This will also print "Today is " followed by the current date.

---

## Bash Vi Mode Keymaps

# Bash VI Mode Keymaps

## Introduction

This document lists key mappings for Bash when VI mode is enabled. In VI mode, Bash allows you to navigate and edit your command line with VI-like controls.

To enable VI mode in Bash, run:
\`\`\`
set -o vi
\`\`\`

## Modes

In VI mode, you have two primary modes:

- **Normal Mode**: Navigate and manipulate text.
- **Insert Mode**: Insert text.

---

## Normal Mode

| Key       | Action                               |
|-----------|--------------------------------------|
| `Esc`     | Enter Normal Mode                    |
| `0`       | Move to the beginning of the line    |
| `$`       | Move to the end of the line          |
| `w`       | Move forward one word                |
| `b`       | Move backward one word               |
| `dd`      | Delete the entire line               |
| `D`       | Delete from cursor to end of line    |
| `u`       | Undo the last change                 |
| `Ctrl`+`r`| Redo the last undo                   |

---

## Insert Mode

| Key       | Action                     |
|-----------|----------------------------|
| `i`       | Enter Insert Mode          |
| `I`       | Insert at the beginning    |
| `a`       | Append after the cursor    |
| `A`       | Append at the end          |
| `o`       | Open a new line below      |
| `O`       | Open a new line above      |

---

To switch between modes, use `Esc` to go to Normal Mode and `i` to go back to Insert Mode.

---
