## 1.Swapping Two Variables (10 min)
Create a script swap.sh that:
- Asks the user to enter two values (A and B)
- Swaps the values
- Displays the new values

사용자에게 두 값(A와 B)을 입력받아
두 값을 서로 바꾸고, 변경된 값을 출력하는 swap.sh 스크립트를 작성하시오.
```bash
gedit swap.sh
```
```bash
#!/bin/bash

echo "Enter value A:"
read A
echo "Enter value B:"
read B

temp=$A
A=$B
B=$temp

echo "After swapping:"
echo "A = $A"
echo "B = $B"
```
```bash
bash swap.sh
```
## 2. Fahrenheit to Celsius (10 min)
Create a script degconv.sh that:
- Asks for a temperature in Fahrenheit
- Converts it to Celsius using the formula
- Displays the result
화씨 온도를 입력받아
섭씨로 변환한 뒤 결과를 출력하는 degconv.sh 스크립트를 작성하시오.
```bash
#!/bin/bash
echo "Enter temperature in Fahrenheit:"
read F
C=$(echo "scale=2; ($F - 32) * 5 / 9" | bc)
echo "Temperature in Celsius: $C"
``````` 
## 3. Mini Calculator (20 min)
Create a script calc.sh that:
- Asks for two numbers
- Shows a menu (add, subtract, multiply, divide)
- Uses case and arithmetic to display the result
두 숫자를 입력받고,
연산 메뉴를 보여준 뒤 case를 사용해 결과를 출력하시오.
```bash
#!/bin/bash
echo -n "Enter two numbers: "
read a b

echo "1. Addition"
echo "2. Subtraction"
echo "3. Multiplication"
echo "4. Division"
echo -n "Choose an option: "
read op

case $op in
1) echo "$a + $b = $((a + b))";;
2) echo "$a - $b = $((a - b))";;
3) echo "$a * $b = $((a * b))";;
4) echo "$a / $b = $((a / b))";;
*) echo "Invalid option";;
esac
```
## 4. Biggest of Three Numbers (15 min)
Create a script big3.sh that:
- Asks the user to enter three numbers
- Uses if statements to find and display the biggest number
세 개의 숫자를 입력받아
가장 큰 숫자를 출력하시오.
```bash
#!/bin/bash
echo -n "Enter values for A B and C: "
read a b c

if [ $a -gt $b ] && [ $a -gt $c ]; then
  echo "A is the biggest"
elif [ $b -gt $c ]; then
  echo "B is the biggest"
else
  echo "C is the biggest"
fi
```
## 5. Grade Determination (15 min)
Create a script grade.sh that:
- Asks the user to enter a mark (0–100)
- Displays a grade based on the mark using if/elif/else
점수를 입력받아
조건문을 사용해 학점을 출력하시오.
```bash
#!/bin/bash
echo -n "Enter your mark: "
read mark

if [ $mark -gt 90 ]; then
  echo "S Grade"
elif [ $mark -gt 80 ]; then
  echo "A Grade"
elif [ $mark -gt 70 ]; then
  echo "B Grade"
elif [ $mark -gt 60 ]; then
  echo "C Grade"
elif [ $mark -gt 55 ]; then
  echo "D Grade"
elif [ $mark -ge 50 ]; then
  echo "E Grade"
else
  echo "U Grade"
fi
```
## 6. Vowel or Consonant (10 min)
Create a script vowel.sh that:
- Asks the user to input one lowercase letter
- Uses a case structure to determine if it’s a vowel or a consonant
소문자 알파벳 하나를 입력받아
모음인지 자음인지 판단하시오.
```bash
#!/bin/bash
echo -n "Enter a lowercase character: "
read choice

case $choice in
a|e|i|o|u)
  echo "It's a vowel";;
*)
  echo "It's a consonant";;
esac
```
## 7. Check lines and words (20 min)
Create a script filecount.sh that:
- Asks for a file name
- Checks if it exists
- If yes, displays number of lines and words using wc
파일명을 입력받아
존재 여부를 확인하고, 줄 수와 단어 수를 출력하시오.
```bash
#!/bin/bash
echo "Enter the file name:"
read filename

if [ -f "$filename" ]; then
  echo "Counting lines and words in '$filename'..."
  echo "Number of lines: $(wc -l < "$filename")"
  echo "Number of words: $(wc -w < "$filename")"
else
  echo "File '$filename' not found."
fi
```

