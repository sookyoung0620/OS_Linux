## 1. Create a working directory named 'lab' in your home directory. Which command allows you to create a directory in your home folder?
홈 디렉토리에 lab이라는 작업 디렉토리를 생성하시오.
홈 폴더에 디렉토리를 생성하는 명령어는 무엇입니까?
```bash
mkdir ~/lab
```
## 2. Move into this newly created directory. What command do you use to navigate into a directory?
방금 생성한 디렉토리로 이동하시오.
디렉토리로 이동할 때 사용하는 명령어는 무엇입니까?
```bash
cd ~/lab
```
## 3. Create the following files: file1.txt, file2.txt, file3.txt, notes.md, data.csv. How would you create multiple empty files at once?
다음 파일들을 생성하시오: file1.txt, file2.txt, file3.txt, notes.md, data.csv.
여러 개의 빈 파일을 한 번에 생성하는 방법은 무엇입니까?
```bash
touch file1.txt file2.txt file3.txt notes.md data.csv
```
## 4. Copy all .txt files into a folder named 'backup'. How would you identify and copy only files with the .txt extension?
모든 .txt 파일을 backup이라는 폴더로 복사하시오. .txt 확장자를 가진 파일만 선택하여 복사하는 방법은 무엇입니까?
```bash
mkdir backup
cp *.txt ~/backup
```
## 5. Rename the file file3.txt to final.txt. Which command renames or moves a file?
file3.txt 파일의 이름을 final.txt로 변경하시오.
파일의 이름 변경 또는 이동에 사용하는 명령어는 무엇입니까?
```bash
mv file3.txt final.txt
```
## 6. Move notes.md into a new folder called docs/. What command moves a file and how do you create the folder first?
notes.md 파일을 docs/라는 새 폴더로 이동하시오.
폴더를 먼저 생성한 뒤 파일을 이동하는 명령어는 무엇입니까?
```bash
mkdir docs
mv notes.md docs/
```
## 7. Delete the docs/ folder and the file data.csv. What commands allow you to remove files and folders respectively?
docs/ 폴더와 data.csv 파일을 삭제하시오.
파일과 폴더를 각각 삭제하는 명령어는 무엇입니까?
```bash
rm data.csv
rm -r docs
```
## 8. Try each command and write down what it does. 
• Use rm -i to confirm deletion before proceeding. 
• Use cp -v, mv -i, or rm -v to observe detailed output.
• Use wildcards like .txt or file to match filenames.
• Use cp *.txt newlocation/ to copy multiple files at once.
• Use rm *.txt carefully to delete all .txt files.

각 명령어를 실행해 보고, 어떤 동작을 하는지 설명하시오.

```bash
rm -i : 파일 삭제 전에 사용자에게 확인을 요청한다.
cp -v : 복사 과정을 자세히 출력한다.
*.txt : .txt 확장자를 가진 모든 파일을 선택한다.
cp *.txt newlocation/ : 모든 .txt 파일을 한 번에 복사한다.
rm *.txt : 모든 .txt 파일을 삭제하므로 주의가 필요하다.
```
## 9. Create a file named test.txt.What command do you use to create a new file?
test.txt라는 파일을 생성하시오.
새 파일을 생성하는 명령어는 무엇입니까?
```bash
touch test.txt
```

## 10. Delete the file test.txt. How do you delete a file from the system?
test.txt 파일을 삭제하시오.
시스템에서 파일을 삭제하는 방법은 무엇입니까?
```bash
rm test.txt
```

## 11. Try to recover the deleted file. Was it possible? Explain what happens to a file when it's deleted using rm.
삭제된 파일을 복구해 보시오. 가능했습니까?
rm으로 파일을 삭제하면 어떤 일이 발생하는지 설명하시오.
```bash
파일은 일반적으로 복구할 수 없다.
rm 명령어는 파일을 휴지통으로 보내지 않고 즉시 시스템에서 제거한다.
```

## 12. What option can you use to avoid accidental deletions when using rm? Which option makes rm ask for confirmation before deleting?
rm 사용 시 실수로 삭제하는 것을 방지하기 위한 옵션은 무엇입니까?
삭제 전에 확인을 요청하는 옵션은 무엇입니까?
```bash
rm -i
```
## 13. Create the following files: test1.txt, test2.txt, test1.csv, report.md. What is the simplest way to create all these files in one command?
다음 파일들을 생성하시오.
한 줄의 명령어로 가장 간단하게 생성하는 방법은 무엇입니까?
```bash
touch test1.txt test2.txt test1.csv report.md
```
## 14. Use these commands and describe the difference in results:
ls test?.txt
ls .md
ls test.*
How do wildcards help you filter files in a directory?


다음 명령어들의 실행 결과 차이를 설명하시오.
와일드카드는 디렉토리 내 파일을 어떻게 필터링하는 데 도움을 줍니까?

```bash
test?.txt : test 다음에 한 글자가 오는 txt 파일
*.md : 모든 md 파일
test*.* : test로 시작하는 모든 파일
와일드카드는 특정 조건의 파일만 선택할 수 있게 해준다.
```

## 15. Open the manual for the cp command. Which option lets you copy directories? What is the command to view the manual and which flag is needed to copy folders?
cp 명령어의 매뉴얼을 여시오.
디렉토리를 복사할 때 사용하는 옵션은 무엇입니까?
```bash
man cp
cp -r source destination
```

## 16.Create a directory named 'lab'. Which command creates a new folder?
lab이라는 디렉토리를 생성하시오.
새 폴더를 생성하는 명령어는 무엇입니까?
```bash
mkdir lab
```
## 17. Move all the created files into the lab folder. How can you move multiple files at once into a folder?
생성한 모든 파일을 lab 폴더로 이동하시오.
여러 파일을 한 번에 이동하는 방법은 무엇입니까?
```bash
mv *.txt *.md *.csv ~/lab
```

## 18. Copy the entire 'lab' folder to a new folder named 'lab_final'. How do you copy directories with all their contents?
lab 폴더 전체를 lab_final이라는 새 폴더로 복사하시오.
디렉토리와 그 안의 모든 내용을 복사하는 방법은 무엇입니까?
```bash
cp -r lab lab_final
```
