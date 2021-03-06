# c에서의 파일 관련 함수
>  stdio.h 헤더에 포함

## 1. 파일 오픈

    fopen("[열고싶은_파일명]", "[모드]")

<li> 리턴값 : 파일 포인터
<li> 모드의 종류 : r, w, r+, w+</li>

## 2. 문자 가져오기

    int fgetc(FILE *stream);

<li> 파일 포인터가 가리키는 다음 문자를 읽어들인다.

<li> stream : 파일 포인터
<li> 리턴값 :  읽어들인 문자열을 int형으로 캐스트해 반환한다.
<li> stream : 파일 포인터 </li>

## 3. 문자열 가져오기

    fgets(char * str, int num, FILE *stream);

<li> 1개 이상, num보다 작은 문자열을 파일 포인터가 가리키는 파일에서 읽어와 str에 저장한다.
읽기가 멈추는 때는 EOF이나 개행문자일 때이다.

<li>str : 읽어들인 문자열을 저장할 char 배열
<li>num : 읽어들일 최대 문자수
<li>stream : 파일 포인터
<li>리턴값 : 성공 - str, 실패 - null</li>

## 4. 파일 닫기

    fclose(FILE *stream);
<li> 파일포인터를 제거한다. (더이상 파일을 참조하지 않게 한다)


## 5. 파일 포인터 초기화

    rewind(FILE *stream);
<li> 파일 포인터의 위치를 초기화한다.
<li> 현재 파일 포인터의 위치는 `ftell(FILE *stream)`함수를 이용하면 알 수 있다.

## 6. 파일 포인터 위치 이동

    fseek(fp, 0, SEEK_END);
<li>파일포인터의 위치를 이동시킨다.

#### 3번째 인자 - 파일오프셋을 어떻게 이동할 지 결정
 <li> SEEK_SET(0) : 파일의 처음 위치를 기준으로 이동
 <li> SEEK_CUR(1) : 현재 파일의 위치를 기준으로 이동
 <li> SEEK_END(2) : 파일의 마지막 위치를 기준으로 이동

## 7. 현재 파일포인터의 위치 알아내기

    ftell(fp);
<li> 파일을 읽거나 쓰면서 이동하는 현재 위치의 위치 값을 반환한다.
 <li> 리턴값 : 현재 위치 반환(현재 위치의 앞에 있는 글자들의 개수), 1글자를 1으로 함.
