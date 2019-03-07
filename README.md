<알고리즘 개정4>의 소스 코드를 이클립스에서 빌드하는 방법과 실행 방법을 소개합니다.

원본 소스 코드: https://github.com/kevin-wayne/algs4

원본 소스 코드에서 Clone or download 녹색 버튼을 클릭해서
Download Zip으로 압축 파일을 받아서 원하는 곳에 압축을 풀어도 됩니다.
가능하면 C: 드라이브 루트에 압축을 해제해서 C:\algs4 디렉터리를
작업 디렉터리로 사용하는 것을 추천합니다.

git을 사용할 줄 알면

C:\repo 디렉터리를 만들고 다음 명령을 실행합니다.

```
cd c:\repo
git clone https://github.com/kevin-wayne/algs4.git
```

이제 다음 절차를 따릅니다. 이클립스에서 빌드하면 의존성 있는 라이브러리까지 자동으로 다운로드합니다.

1. 이클립스 실행
2. Help > Eclipse Marketplace 선택
3. Find에서 Maven으로 검색
4. Maven Integration for Eclipse를 설치(Install 버튼)
5. 이클립스에서 File > Import > Maven > Existing Maven Projects... 선택
6. github에서 받은 소스 코드 algs4 디렉터리를 선택
7. Finish 버튼 클릭해서 프로젝트를 임포트
8. 이클립스의 Package Explorer에서 algs4 우클릭 후에 
   Maven > Update Project...를 선택하면 빌드 진행

데이터 파일은

https://algs4.cs.princeton.edu/code/

홈페이지에 algs4-data.zip으로 제공하지만,
없는 경우에는 직접 만들어야 합니다.

가능하면 누락된 데이터를 찾아서

https://github.com/gilbutITbook/006782/data

에 정리해뒀습니다. 원서 사이트보다 데이터 파일이 많습니다.
github에서 단일 파일 크기가 100MB를 초과하면 업로드가 불가능합니다.

데이터가 포함된 소스 코드를 받으려면 길벗 홈페이지를 이용하세요.
https://www.gilbut.co.kr/book/view?bookcode=BN002341#bookData


tinyEWDAG.txt 데이터 파일은 제공되지 않으므로 그림 4-74의 내용을 토대로 데이터 파일을 작성.
(https://github.com/gilbutITbook/006782/data/tinyEWDAG.txt 파일 다운로드해도 됩니다. 원서 사이트에는 없음)

tinyEWDAG.txt 파일을 algs4 프로젝트에서 컴파일된 파일이 생성되는

algs4\target\classes\edu\princeton\cs\algs4\tinyEWDAG.txt

로 복사


## 명령 프롬프트로 실행하기
명령 프롬프트에서 algs4\target\classes에서 다음과 같이 실행

```
X:\repo\algs4\target\classes>java edu.princeton.cs.algs4.AcyclicSP tinyEWDAG.txt 5
5 to 0 (0.73)  5->4  0.35   4->0  0.38
5 to 1 (0.32)  5->1  0.32
5 to 2 (0.62)  5->7  0.28   7->2  0.34
5 to 3 (0.61)  5->1  0.32   1->3  0.29
5 to 4 (0.35)  5->4  0.35
5 to 5 (0.00)
5 to 6 (1.13)  5->1  0.32   1->3  0.29   3->6  0.52
5 to 7 (0.28)  5->7  0.28

X:\repo\algs4\target\classes>
```

명령 프롬프트에서 실행할 때는 target\classes 디렉터리에서 실행해야 하고,
클래스명은 항상 "패키지명.클래스명"으로 지정해야 합니다.


## 이클립스에서 실행하기

이클립스 메뉴에서

Run > Run as > Java Application 선택

다양한 클래스 중에 AcyclicSP 선택해서 실행

실행하면 다음 에러가 발생

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0
	at edu.princeton.cs.algs4.AcyclicSP.main(AcyclicSP.java:138)

```

이제 이클립스에 AcyclicSP configuration이 생성되어 있으므로 이 설정을 수정합니다.

메뉴에서 Run > Run Configurations 선택
Java Application > AcyclicSP 선택
Arguments 탭에 Program Arguments 항목에 다음을 입

tinyEWDAG.txt 5

Run 클릭

하단 Console 탭에 실행 결과가 다음과 같이 표시

```
5 to 0 (0.73)  5->4  0.35   4->0  0.38   
5 to 1 (0.32)  5->1  0.32   
5 to 2 (0.62)  5->7  0.28   7->2  0.34   
5 to 3 (0.61)  5->1  0.32   1->3  0.29   
5 to 4 (0.35)  5->4  0.35   
5 to 5 (0.00)  
5 to 6 (1.13)  5->1  0.32   1->3  0.29   3->6  0.52   
5 to 7 (0.28)  5->7  0.28   
```


## 책의 2페이지 하단에

북사이트, 예제 소스, 동영상 강의(한국어 자막)를 볼 수 있는 링크가 안내되어 있습니다.


## 추가 설명
프린스턴, MIT 등의 대학에서는 입문 교재에서 입출력 라이브러리를 직접 만들어서 사용하는 경우가 종종 있습니다. <알고리즘 개정4판>에서는 StdIn, StdOut 클래스 등을 직접 만들어 사용합니다. 사용하는 프로그래밍 언어가 자바이거나 파이썬이거나 관계 없이 StdIn, StdOut 같은 공통 라이브러리를 사용하고 공통 사용법을 제공함으로써 언어에 대한 종속성을 제거하고 프로그래밍이나 알고리즘 문제 자체에 집중하기 위한 것입니다.


## 면책사항
이 저장소는 한국어 번역판 사용자가 예제 코드를 빌드하는 방법과 사용하는 방법을 안내하기 위해 제작한 것입니다. 소스 코드의 수정, 개정 사항 등은 항상 원서 북사이트와 github 소스 코드를 참고하시기 바랍니다.

## 리소스

코드와 라이브러리: https://algs4.cs.princeton.edu/code/

예제 소스 https://algs4.cs.princeton.edu/code/

Github 저장소 https://github.com/kevin-wayne/algs4

    저장소 README-MAVEN.txt에는 Maven으로 직접 빌드하는 방법, 리눅스와 macOS에서 빌드하는 방법이 안내되어 있습니다.

저자가 인정한 Scala fork https://github.com/garyaiki/Scala-Algorithms

저자가 인정한 .NET fork  https://github.com/nguyenqthai/Algs4Net

알고리즘 1부 동영상 강의(한국어 자막) https://www.coursera.org/learn/algorithms-part1

알고리즘 2부 동영상 강의(한국어 자막) https://www.coursera.org/learn/algorithms-part2