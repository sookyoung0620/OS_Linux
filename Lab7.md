## 1. Read lines from a file (10 min)
Create a file with random text, call it “myfile.txt”.
Read the file line by line.
임의의 텍스트가 들어 있는 myfile.txt 파일을 생성하고, 파일을 한 줄씩 읽어 출력하시오.
```bash
#!/bin/bash

while read line
do
  echo "$line"
done < myfile.txt
```
## 2.Print Positional Parameters
Create script: args.sh
Print the following:
- $# (number of arguments)
- $0 (script name)
- $1, $2 (first and second arguments)
- $@ (all arguments)
- Run: ./args.sh A B C and ./args.sh "hello" "world"
args.sh 스크립트를 생성하여 전달된 위치 인자 정보를 출력하시오.
```bash
#!/bin/bash

echo "Number of arguments: $#"
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
```
## 3.Creating Users with a Function (20 min)
Create script: adduser.sh
Define a function add_a_user
Use positional parameters to:
- Assign $1 to USER
- Assign $2 to PASSWORD
- Use shift to remove the first two arguments
- Assign the rest ($@) to COMMENTS
  Simulate creating users with echo commands.
  Call the function twice with different arguments.
함수와 위치 인자를 사용해 사용자 생성 과정을 시뮬레이션하는 스크립트를 작성하시오.
```bash
#!/bin/bash

add_a_user() {
  USER=$1
  PASSWORD=$2
  shift 2
  COMMENTS=$@

  echo "Creating user: $USER"
  echo "Password: $PASSWORD"
  echo "Comments: $COMMENTS"
}

add_a_user alice pass123 Developer Team
add_a_user bob secret456 System Admin
```

## 4.Greeting Function with Validation
Create script: greet.sh
Define a function greet_user that takes a name.
If name is missing, show an error.
Otherwise, print:
"Hello, NAME. Today is DATE."

Example:
./greet.sh Thomas

Result:
Hello, Thomas. Today is <current date>

이름을 인자로 받아 인사하는 함수를 작성하시오. 이름이 없으면 오류를 출력하시오.

```bash
#!/bin/bash

greet_user() {
  if [ -z "$1" ]; then
    echo "Error: Name is missing."
  else
    echo "Hello, $1. Today is $(date)."
  fi
}

greet_user "$1"
```

