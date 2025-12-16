## 1. (2 pts)
Explain the architecture of a typical Linux operating system. Include the roles of each element.
일반적인 Linux 운영체제의 구조를 설명하고, 각 구성 요소의 역할을 포함하시오.


- A typical Linux operating system consists of hardware, the kernel, the shell, and user applications.
The kernel manages hardware resources such as CPU, memory, and devices.
The shell provides an interface between the user and the kernel.
User applications allow users to perform tasks on the system.


- 일반적인 Linux 운영체제는 하드웨어, 커널, 셸, 사용자 응용 프로그램으로 구성된다.
커널은 CPU, 메모리, 장치와 같은 하드웨어 자원을 관리한다.
셸은 사용자와 커널 사이의 인터페이스 역할을 한다.
사용자 응용 프로그램은 사용자가 작업을 수행할 수 있게 해준다.

## 2. (2 pts)
List and describe four essential Linux shell commands. Include what each one does.
First command:
Second command:
Third command:
Fourth command:

기본적인 Linux 셸 명령어 네 개를 나열하고 각 기능을 설명하시오.


- ls: Lists files and directories.
  cd: Changes the current directory.
  cp: Copies files or directories.
  rm: Removes files or directories.

- ls: 파일과 디렉토리 목록을 출력한다.
  cd: 현재 작업 디렉토리를 변경한다.
  cp: 파일이나 디렉토리를 복사한다.
  rm: 파일이나 디렉토리를 삭제한다.

## 3. (1 pt)
What the difference between prompt, terminal, shell, and command line?
Shell:
Prompt:
Terminal:
Command line:


prompt, terminal, shell, command line의 차이를 설명하시오.

- Shell: A program that interprets user commands.
  Prompt: The text that indicates the shell is ready to accept input.
  Terminal: A program that provides access to the shell.
  Command line: The line where commands are typed.


- Shell: 사용자의 명령을 해석하는 프로그램이다.
  Prompt: 명령 입력을 기다리는 상태를 나타내는 표시이다.
  Terminal: 셸에 접근할 수 있게 해주는 프로그램이다.
  Command line: 명령어를 입력하는 줄이다.

## 4. (1 pt)
How can 'stdout' and 'stderr' be redirected in Linux?
stdout:
stderr:


Linux에서 stdout과 stderr를 어떻게 리다이렉션할 수 있습니까?

- stdout: Redirected using >
  stderr: Redirected using 2>

- stdout: > 를 사용해 리다이렉션한다.
  stderr: 2> 를 사용해 리다이렉션한다.

## 5. (2 pts)
Explain what a pipe (|) does in a command. Give an example of a useful pipeline with at least two commands and explain your example.

파이프(|)의 역할을 설명하고, 두 개 이상의 명령어를 사용하는 예시를 설명하시오.


- A pipe sends the output of one command as input to another command.
  Example: ls | wc -l counts the number of files in the directory.


- 파이프는 한 명령어의 출력을 다른 명령어의 입력으로 전달한다.
  예를 들어 ls | wc -l 은 디렉토리 안의 파일 개수를 센다.

Section B – Command Analysis & Short Tasks (12 points)
## 6. (1 pt)
You are in a directory containing multiple .txt files. Write a command that:
Creates a subdirectory named texts
Moves all .txt files into that subdirectory.

모든 .txt 파일을 texts 디렉토리로 이동하는 명령어를 작성하시오.


- mkdir texts
  mv *.txt texts/

## 7. (1 pt)
What does the following command do?
ls /etc | grep conf | wc -l

다음 명령어의 동작을 설명하시오.


- It counts how many files in /etc contain the word "conf".
- /etc 디렉토리에서 이름에 conf가 포함된 파일의 개수를 센다.

## 8. (2 pts)
Write a command that lists the last 10 lines of a file called 'system.log' and counts how many of them contain the word 'ERROR'.

system.log 파일의 마지막 10줄 중 ERROR가 포함된 줄의 개수를 구하시오.

- tail -n 10 system.log | grep ERROR | wc -l

## 9. (1 pt)
Write a shell command to extract and sort (alphabetically) all usernames from /etc/passwd.
/etc/passwd에서 모든 사용자 이름을 추출해 알파벳 순으로 정렬하시오.


- cut -d: -f1 /etc/passwd | sort

## 10. (2 pts)
You have a file called logs.txt. Write a pipeline (|) that extracts all lines containing the word 'fail' (case-insensitive), shows only the first two words of each line, removes duplicates, and sorts the result in reverse order.

logs.txt에서 fail이 포함된 줄을 추출하고, 앞 두 단어만 남긴 후 중복 제거 및 역순 정렬하시오.


- grep -i fail logs.txt | cut -d' ' -f1,2 | sort | uniq | sort -r

## 11. (1 pt)
Create a script ‘hello.sh’ that:
- Ask the user for their name
- Reads the input
- Print “Hello your_name”
Write the full script below:

이름을 입력받아 인사하는 hello.sh 스크립트를 작성하시오.

```bash
#!/bin/bash
echo -n "Enter your name: "
read name
echo "Hello $name"
```
## 12. (4 pts)
Create a script that:
- Asks the user to enter three file names.
- Assuming that all the files exist:
- Find the number of lines in each file.
- Use if statements to determine which file has the highest line count.
- Display the name of the file with the most lines and how many lines it contains.
Write the full script below:

세 개의 파일 이름을 입력받아, 가장 많은 줄을 가진 파일과 그 줄 수를 출력하시오.

```bash
#!/bin/bash

echo "Enter first file:"
read f1
echo "Enter second file:"
read f2
echo "Enter third file:"
read f3

c1=$(wc -l < "$f1")
c2=$(wc -l < "$f2")
c3=$(wc -l < "$f3")

if [ $c1 -ge $c2 ] && [ $c1 -ge $c3 ]; then
  echo "$f1 has the most lines: $c1"
elif [ $c2 -ge $c1 ] && [ $c2 -ge $c3 ]; then
  echo "$f2 has the most lines: $c2"
else
  echo "$f3 has the most lines: $c3"
fi
```
