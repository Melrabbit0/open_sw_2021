# open_sw_2021


getopt()
프로그램 실행시 입력 받은 인자를 받아 분석하여 옵션 처리를 가능하게 해주는 함수
extern char *
getopt 옵션 3가지
getopt -a
getopt -b optarg
getopt -b optarg nonopt

#include <unistd.h> 헤더에 들어있음
int getopt(int argc, char *const *argv, const char *shortopts) 형태
int argc 인수의 개수 char *const *argv 인수의 내용 const char *shortopts 검색하려는 옵션들의 문자열

getopts()
명령행 인수를 처리하고 유효한 옵션을 검사
매개변수 리스트에서 옵션 및 옵션 인수를 검색하는 쉘 내장 명령어.
OptionString의 문자 뒤에는 :(콜론)이 오면 옵션에 인수가 있는 것으로 간주. 옵션에 옵션-인수가 필요한 경우 getopts 명령은 이를 변수 OPTARG에 배치합니다.

매개변수 optionstring 이름 Argument

종료는 0 >0으로 종료됨

참고 : https://www.ibm.com/docs/ko/aix/7.2?topic=g-getopts-command




sed 명령어
스트림 편집기

sed [ -n ] [ -u ] Script  [ File ... ]
sed [ -n ] [ -u ] [ -e Script ] ... [ -f ScriptFile ] ...  [ File ... ]

편집 스크립트에 따라 지정된 file 매개변수에서 행을 수정하고 표준 출력에 작성.
즉 수정 치환 삭제 글씨기 등의 편집기 기능을 제공함.
옵션
-e 스크립트 해당 옵션은 생략될 수 있음
-f scriptfile scriptfile을 사용하여 편집함
-n 표준 출력 기록된 모둔 정보를 출력
-u 버퍼없음 모드에서 출력 

특정 행을 출력 - p (print)
특정 행 삭제 - d (delete)
단어 치환(Substitute) - s (substitute)
문자열 추가 - a, i (append, insert)
특정 행의 내용을 전부 교체 - c (change)
특정 행에 파일의 내용을 추가 - r (read)


awk 명령어
파일에서 패턴이 일치하는 행을 찾아 그 행에 지정한 조치를 취할 수 있음
awk [ -u ] [ -F Ere ] [ -v Assignment ] ... { -f ProgramFile | 'Program' } [ [ File ... | Assignment ... ] ]

awk 명령은 사용자가 제공하는 명령어 세트를 사용하여 사용자가 제공한 확장 정규식과 파일 세트를 한 번에 한 행씩 비교합니다. 그런 다음, 확장 정규식과 일치하는 모든 행에서 조치를 실행합니다.

열(Column)만 출력하기
awk '{ print $1 }' ./awk_test_file.txt

특정 pattern이 포함된 레코드 출력
 awk '/rea/' ./awk_test_file.txt

출력의 내용 첨가
awk '{ print ("name : " $1, ", "  "phone : " $2) }' ./awk_test_file.txt

특정 Record를 검색하기 - if 구문
awk '{ if ( $5 >= 80 ) print ($0) }' ./awk_test_file.txt

내장 함수
 awk '{ print ("name leng : " length($1), "substr(0,3) : " substr($1,0,3)) }' ./awk_test_file.txt

반복문
awk '{
for(i=0;i<2;i++)
 print( "for loop :" i "\t" $1, $2, $3)
}' ./awk_test_file.txt


변수 사용
 awk '
> BEGIN {
>  sum = 0
>  cnt = -1
> }
>
> {
>  sum += $5
>  cnt++
> }
>
> END {
>  avg = sum/cnt
>  print ("sum :" sum ", average :" avg)
> }' ./awk_test_file.txt

참고 : https://reakwon.tistory.com/163, https://www.ibm.com/docs/ko/aix/7.2?topic=awk-command
