# Shell Scripting II: Advanced Scripts (Session 7)

##  Overview

This session focuses on **advanced shell scripting techniques**.  
You will learn how to handle command-line arguments, use loops and functions, manage exit codes, and write scripts that behave like real command-line tools.

---

##  Learning Objectives

By the end of this session, you will be able to:

- Handle command-line arguments using positional parameters
- Use `shift` to process variable numbers of arguments
- Write reusable functions in shell scripts
- Use loops (`while`) for repeated tasks
- Manage exit codes with `exit`, `return`, and `$?`
- Debug shell scripts using built-in tools
- Write modular and maintainable scripts

---

##  Positional Parameters

Shell scripts receive arguments automatically.

| Variable | Description |
|--------:|-------------|
| `$0` | Script name |
| `$1`–`$9` | Positional arguments |
| `$#` | Number of arguments |
| `$@` | All arguments |

### Example

```bash
#!/bin/bash
echo "Script name: $0"
echo "Number of arguments: $#"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
```
Run:
```
./script.sh hello world
```
## While Loop

The while loop is useful when the number of iterations is unknown.

Structure
```
while [ condition ]; do
  commands
done
```

### Example
```
#!/bin/bash
count=1
while [ $count -le 5 ]; do
  echo "Count is $count"
  count=$((count + 1))
done
```

## shift Command

shift removes the first positional argument and shifts the rest left.

shift → shifts by 1

shift N → shifts by N

$# decreases after each shift

Example
```
#!/bin/bash
while [ "$#" -gt 0 ]; do
  echo "Argument: $1"
  shift
done
```

Run:
```
./shift_example.sh hello world 42 earth
```
## Functions

Functions allow code reuse and better structure.

Syntax
```
function_name() {
  commands
}
```
Example
```
hello_person() {
  echo "Hello, $1!"
}

hello_person "Thomas"
```
## exit, return, and $?

Used to indicate success or failure.

| Command  | Usage                        |
| -------- | ---------------------------- |
| `exit`   | Terminates script            |
| `return` | Returns status from function |
| `$?`     | Exit status of last command  |

Example (exit)
```
#!/bin/bash
if [ ! -f myfile.txt ]; then
  echo "File not found!"
  exit 1
fi
```
Example (return)
```
check_number() {
  if [ "$1" -gt 10 ]; then
    return 0
  else
    return 1
  fi
}
```
## Debugging Tools

Useful tools for debugging shell scripts:
```
set -x : Trace mode (prints commands before execution)

set +x : Disable trace mode

echo : Print variable values

$? : Check last command status

bash -n script.sh : Syntax check without execution

trap : Handle cleanup on script exit
```
Example
```
set -x
NAME="Thomas"
echo "Hello, $NAME"
set +x
```
