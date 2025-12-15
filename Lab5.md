## 1. Create a working directory and navigate into it.
작업 디렉토리를 생성하고 해당 디렉토리로 이동하시오.
```bash
mkdir ~/cli_lab5
cd ~/cli_lab5
```
## 2. Copy or create the file fake_syslog.txt in that folder.
해당 폴더에 fake_syslog.txt 파일을 복사하거나 생성하시오.
```bash
cp ~/fake_syslog.txt 
touch fake_syslog.txt
```
```bash
2023-11-01 10:00:01 INFO System boot complete.
2023-11-01 10:01:03 ERROR Failed to load module 'xyz'.
2023-11-01 10:02:45 WARNING Disk space low.
2023-11-01 10:04:12 Info User login: alice
2023-11-01 10:05:07 error Unable to reach server.
2023-11-01 10:06:30 warning High CPU usage detected.
2023-11-01 10:07:55 ERROR Segmentation fault occurred.
2023-11-01 10:08:15 INFO Scheduled backup started.
2023-11-01 10:09:40 WARNING Memory leak suspected.
2023-11-01 10:10:22 error Disk read failure.
2023-11-01 10:11:33 info User logout: alice
2023-11-01 10:12:55 ERROR Network unreachable.
2023-11-01 10:13:17 warning Service response delay.
2023-11-01 10:14:42 Info System check passed.
2023-11-01 10:15:59 ERROR Unable to authenticate user.
```
## 3.Extract lines containing 'error' and redirect to errors.txt. Do the same for 'warn' into warnings.txt.
error가 포함된 줄을 추출해 errors.txt로 저장하고,
warn이 포함된 줄을 warnings.txt로 저장하시오.
```bash
grep error fake_syslog.txt > errors.txt
grep warn fake_syslog.txt > warnings.txt
```

## 4.Generate basic statistics for errors.txt: line count, word count, character count, longest line. Save all to summary.txt.
errors.txt에 대해 줄 수, 단어 수, 문자 수, 가장 긴 줄의 길이를 구하고
모든 결과를 summary.txt에 저장하시오.
```bash
wc -l errors.txt > summary.txt
wc -w errors.txt >> summary.txt
wc -c errors.txt >> summary.txt
wc -L errors.txt >> summary.txt
```
## 5.Preview and save the first 5 lines of errors.txt and warnings.txt to first_errors.txt and first_warnings.txt.
errors.txt와 warnings.txt의 처음 5줄을 확인하고
각각 first_errors.txt, first_warnings.txt로 저장하시오.
```bash
head -n 5 errors.txt > first_errors.txt
head -n 5 warnings.txt > first_warnings.txt
```
## 6.Extract timestamps (first 2 fields from each line) from errors.txt and warnings.txt. Save their frequencies to error_times.txt and warning_times.txt.
errors.txt와 warnings.txt에서
각 줄의 앞 2개 필드(타임스탬프)를 추출하고
빈도를 계산하여 각각 파일로 저장하시오.
```bash
cut -d' ' -f1,2 errors.txt | sort | uniq -c > error_times.txt
cut -d' ' -f1,2 warnings.txt | sort | uniq -c > warning_times.txt
```
## 7. Append the summary and timestamp statistics into a file named final_report.txt.
summary와 타임스탬프 통계를 final_report.txt에 추가하시오.
```bash
cat summary.txt > final_report.txt
cat error_times.txt >> final_report.txt
cat warning_times.txt >> final_report.txt
```

## 8.Try doing the timestamp count in a single pipeline (no intermediate files).
중간 파일 없이 하나의 파이프라인으로 타임스탬프 빈도를 계산하시오.
```bash
grep -i "error" fake_syslog.txt | cut -d' ' -f1,2 | sort | uniq -c | sort -nr
```

## 9.Identify the longest line in errors.txt using advanced CLI tools.
errors.txt에서 가장 긴 줄을 고급 CLI 도구로 찾으시오.
```bash
wc -L errors.txt
```
## 10. Create a final report file combining all previous results
(summary, error_times, warning_times).
모든 결과를 하나의 최종 보고서 파일로 결합하시오.
```bash
cat summary.txt error_times.txt warning_times.txt > final_report.txt
```
## Q1.How many lines contain 'error' and 'warn'?
error와 warn이 포함된 줄은 각각 몇 개인가요?
```bash
wc -l errors.txt warnings.txt
```
## Q2.What are the five most frequent timestamps associated with errors?
에러와 가장 자주 연관된 상위 5개의 타임스탬프는 무엇인가요?
```bash
sort -nr error_times.txt | head -n 5
```
## Q3.What is the longest line (in characters) found in errors.txt?
errors.txt에서 가장 긴 줄의 길이는 얼마인가요?
```bash
wc -L errors.txt
```
## Q4. What is the difference between using > and >> in your summary file?
summary 파일에서 >와 >>의 차이점은 무엇인가요?
```bash
> : overwrites the contents of a file(기존 내용을 덮어씀)
>> : appends the output to the end of the file without removing existing content(기존 내용 뒤에 추가함)
```
## Q5. Which options of grep and wc did you find most useful and why?
grep과 wc에서 가장 유용했던 옵션은 무엇이며, 그 이유는 무엇인가요?
```bash
grep -i : it allows case-insensitive searches(대소문자 구분 없이 검색 가능)
wc -l : it counts the number of lines in a file(로그에서 메시지 개수를 빠르게 파악 가능)
```
## Q6. What did using a pipeline help you do more efficiently?
파이프라인을 사용하면 어떤 작업을 더 효율적으로 할 수 있었나요?
```bash
Using a pipeline allowed multiple commands to be connected together, enabling fast and efficient text processing without intermediate files.
여러 명령어를 하나로 연결하여 중간 파일 없이 빠르고 효율적인 텍스트 분석이 가능했다.
```
