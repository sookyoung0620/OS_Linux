# Shell Scripting I: Basics & Automation (Session 6)

## Overview

This session introduces **basic shell scripting** in Unix/Linux environments.  
You will learn how to write, execute, and automate tasks using shell scripts, including variables, user input, conditions, and control structures.

---

## Learning Objectives

By the end of this session, you will be able to:

- Understand what a shell script is
- Write and execute a basic shell script
- Use the shebang (`#!`) correctly
- Declare and use variables
- Read user input
- Use conditional logic (`if`, `elif`, `else`)
- Use `case` statements for multiple conditions
- Prepare scripts for automation tasks

---

## What is a Shell Script?

- A **shell script** is a plain text file containing Linux commands
- Commands are executed sequentially by the shell
- Used for file manipulation, program execution, and automation
- Think of it as a *to-do list for the terminal*

### Example
## Shebang (#!)
Specifies which interpreter executes the script
Must be the first line of the file
```bash
#!/bin/bash   # Bash shell
#!/bin/zsh    # Z shell
```
Different shells may have different syntax, so always specify the interpreter.

## Comments
Lines starting with # are comments
Comments are ignored during execution
Useful for documentation and collaboration

# This is a comment

## Creating and Running a Script

Create a script file:
```
gedit hello.sh
```

Add content:
```
#!/bin/bash
echo "Hello, world!"
date
```

Make it executable:
```
chmod +x hello.sh
```

Run it:
```
./hello.sh
```

or
```
bash hello.sh
```
# Variables
## Syntax
```
NAME="Thomas"
echo "Welcome $NAME"
```

Rules:
No spaces around =
Use $ to access variables

## Command Substitution
```
echo "Number of lines: $(wc -l file.txt)"
```
## Reading User Input
```
echo "What is your name?"
read USER_NAME
echo "Hello $USER_NAME"
```
## Environment Variables & export
Scripts run in a new shell.
Use export to make variables available to child shells.
```
export MYVAR
```
## Curly Braces {}

Curly braces clarify variable boundaries.
```
touch "${USER_NAME}.txt"
```
## Conditional Statements (if / elif / else)
Structure
```
if [ condition ]; then
  # code
else
  # code
fi
```
Common Test Operators
File Tests
```
-f : file exists

-d : directory exists

-r : readable

-w : writable

-x : executable

Numeric Tests

-eq : equal

-ne : not equal

-gt : greater than

-lt : less than

-ge : greater or equal

-le : less or equal
```

## Case Structure

The case structure is cleaner than multiple if/elif statements when comparing one variable to many values.
```
case $choice in
  1) echo "You chose one";;
  2) echo "You chose two";;
  3) echo "You chose three";;
  *) echo "Invalid choice";;
esac
```

