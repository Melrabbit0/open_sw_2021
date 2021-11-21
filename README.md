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
