---
layout: single
title:  "logistic_regression_study"
categories: coding
tag: [python, blog, machine_learning]
toc: true
author_profile: false
---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {
      vertical-align: middle;
  }

  .dataframe tbody tr th {
      vertical-align: top;
  }

  .dataframe thead th {
      text-align: center !important;
      padding: 8px;
  }

  .page__content p {
      margin: 0 0 0px !important;
  }

  .page__content p > strong {
    font-size: 0.8rem !important;
  }

  </style>
</head>


<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
0
"
>
<
/
a
>


#
 
*
*
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
 
C
l
a
s
s
i
f
i
e
r
 
T
u
t
o
r
i
a
l
 
w
i
t
h
 
P
y
t
h
o
n
*
*






*
*
A
s
 
a
l
w
a
y
s
,
 
I
 
h
o
p
e
 
y
o
u
 
f
i
n
d
 
t
h
i
s
 
k
e
r
n
e
l
 
u
s
e
f
u
l
 
a
n
d
 
y
o
u
r
 
<
f
o
n
t
 
c
o
l
o
r
=
"
r
e
d
"
>
<
b
>
U
P
V
O
T
E
S
<
/
b
>
<
/
f
o
n
t
>
 
w
o
u
l
d
 
b
e
 
h
i
g
h
l
y
 
a
p
p
r
e
c
i
a
t
e
d
*
*
.




<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
0
.
1
"
>
<
/
a
>


#
 
*
*
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
*
*






1
.
	
[
I
n
t
r
o
d
u
c
t
i
o
n
 
t
o
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
]
(
#
1
)


2
.
	
[
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
 
i
n
t
u
i
t
i
o
n
]
(
#
2
)


3
.
	
[
A
s
s
u
m
p
t
i
o
n
s
 
o
f
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
]
(
#
3
)


4
.
	
[
T
y
p
e
s
 
o
f
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
]
(
#
4
)


5
.
	
[
I
m
p
o
r
t
 
l
i
b
r
a
r
i
e
s
]
(
#
5
)


6
.
	
[
I
m
p
o
r
t
 
d
a
t
a
s
e
t
]
(
#
6
)


7
.
	
[
E
x
p
l
o
r
a
t
o
r
y
 
d
a
t
a
 
a
n
a
l
y
s
i
s
]
(
#
7
)


8
.
	
[
D
e
c
l
a
r
e
 
f
e
a
t
u
r
e
 
v
e
c
t
o
r
 
a
n
d
 
t
a
r
g
e
t
 
v
a
r
i
a
b
l
e
]
(
#
8
)


9
.
	
[
S
p
l
i
t
 
d
a
t
a
 
i
n
t
o
 
s
e
p
a
r
a
t
e
 
t
r
a
i
n
i
n
g
 
a
n
d
 
t
e
s
t
 
s
e
t
]
(
#
9
)


1
0
.
	
[
F
e
a
t
u
r
e
 
e
n
g
i
n
e
e
r
i
n
g
]
(
#
1
0
)


1
1
.
	
[
F
e
a
t
u
r
e
 
s
c
a
l
i
n
g
]
(
#
1
1
)


1
2
.
	
[
M
o
d
e
l
 
t
r
a
i
n
i
n
g
]
(
#
1
2
)


1
3
.
	
[
P
r
e
d
i
c
t
 
r
e
s
u
l
t
s
]
(
#
1
3
)


1
4
.
	
[
C
h
e
c
k
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
]
(
#
1
4
)


1
5
.
	
[
C
o
n
f
u
s
i
o
n
 
m
a
t
r
i
x
]
(
#
1
5
)


1
6
.
	
[
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
m
e
t
r
i
c
e
s
]
(
#
1
6
)


1
7
.
	
[
A
d
j
u
s
t
i
n
g
 
t
h
e
 
t
h
r
e
s
h
o
l
d
 
l
e
v
e
l
]
(
#
1
7
)


1
8
.
	
[
R
O
C
 
-
 
A
U
C
]
(
#
1
8
)


1
9
.
	
[
k
-
F
o
l
d
 
C
r
o
s
s
 
V
a
l
i
d
a
t
i
o
n
]
(
#
1
9
)


2
0
.
	
[
H
y
p
e
r
p
a
r
a
m
e
t
e
r
 
o
p
t
i
m
i
z
a
t
i
o
n
 
u
s
i
n
g
 
G
r
i
d
S
e
a
r
c
h
 
C
V
]
(
#
2
0
)


2
1
.
	
[
R
e
s
u
l
t
s
 
a
n
d
 
c
o
n
c
l
u
s
i
o
n
]
(
#
2
1
)


2
2
.
 
[
R
e
f
e
r
e
n
c
e
s
]
(
#
2
2
)




#
 
*
*
1
.
 
I
n
t
r
o
d
u
c
t
i
o
n
 
t
o
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






데
이
터
 
과
학
자
들
이
 
새
로
운
 
분
류
 
문
제
를
 
마
주
할
 
때
,
 
먼
저
 
떠
오
르
는
 
알
고
리
즘
 
중
 
하
나
는
 
로
지
스
틱
 
회
귀
일
 
수
 
있
다
.
 
로
지
스
틱
 
회
귀
는
 
관
측
치
를
 
이
산
적
인
 
클
래
스
 
집
합
에
 
예
측
하
는
 
데
 
사
용
되
는
 
지
도
 
학
습
 
분
류
 
알
고
리
즘
이
다
.
 
실
제
로
 
관
측
치
를
 
서
로
 
다
른
 
범
주
로
 
분
류
하
는
 
데
 
사
용
된
다
.
 
따
라
서
 
출
력
은
 
이
산
적
인
 
형
태
이
다
.
 
로
지
스
틱
 
회
귀
는
 
로
짓
 
회
귀
(
L
o
g
i
t
 
R
e
g
r
e
s
s
i
o
n
)
로
도
 
불
린
다
.
 
이
는
 
분
류
 
문
제
를
 
해
결
하
는
 
데
 
사
용
되
는
 
가
장
 
간
단
하
고
 
직
관
적
이
며
 
유
연
한
 
분
류
 
알
고
리
즘
 
중
 
하
나
이
다
.


#
 
*
*
2
.
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
 
i
n
t
u
i
t
i
o
n
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
2
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






통
계
학
에
서
 
로
지
스
틱
 
회
귀
 
모
델
은
 
주
로
 
분
류
 
목
적
으
로
 
사
용
되
는
 
통
계
 
모
델
로
 
널
리
 
사
용
된
다
.
.
 
즉
,
 
주
어
진
 
일
련
의
 
관
측
치
를
 
기
반
으
로
 
로
지
스
틱
 
회
귀
 
알
고
리
즘
은
 
이
러
한
 
관
측
치
를
 
두
 
개
 
이
상
의
 
이
산
 
클
래
스
로
 
분
류
하
는
 
데
 
도
움
을
 
준
다
.
 
따
라
서
 
대
상
 
변
수
는
 
이
산
적
이
다
.




로
지
스
틱
 
회
귀
 
알
고
리
즘
은
 
다
음
과
 
같
이
 
작
동
한
다
.
 
-


#
#
 
*
*
I
m
p
l
e
m
e
n
t
 
l
i
n
e
a
r
 
e
q
u
a
t
i
o
n
*
*






로
지
스
틱
 
회
귀
 
알
고
리
즘
은
 
독
립
 
변
수
 
또
는
 
설
명
 
변
수
를
 
사
용
하
여
 
종
속
 
변
수
를
 
예
측
하
는
 
선
형
 
방
정
식
을
 
구
현
하
여
 
작
동
합
니
다
.
 
예
를
 
들
어
,
 
우
리
는
 
공
부
한
 
시
간
의
 
양
과
 
시
험
 
합
격
 
확
률
의
 
예
를
 
고
려
할
 
수
 
있
습
니
다
.
 
여
기
서
,
 
공
부
한
 
시
간
은
 
설
명
 
변
수
이
며
 
x
1
로
 
나
타
내
며
,
 
시
험
 
합
격
 
확
률
은
 
반
응
 
또
는
 
대
상
 
변
수
이
며
 
z
로
 
표
시
됩
니
다
.




설
명
 
변
수
가
 
하
나
(
x
1
)
이
고
 
반
응
 
변
수
가
 
하
나
(
z
)
인
 
경
우
,
 
선
형
 
방
정
식
은
 
다
음
과
 
같
은
 
수
식
으
로
 
표
시
됩
니
다
.




z
 
=
 
β
0
 
+
 
β
1
x
1


여
기
서
 
β
0
와
 
β
1
은
 
모
델
의
 
매
개
 
변
수
입
니
다
.




설
명
 
변
수
가
 
여
러
 
개
인
 
경
우
,
 
위
의
 
방
정
식
은
 
다
음
과
 
같
이
 
확
장
될
 
수
 
있
습
니
다
.




z
 
=
 
β
0
 
+
 
β
1
x
1
+
 
β
2
x
2
+
…
…
.
.
+
 
β
n
x
n


여
기
서
 
β
0
,
 
β
1
,
 
β
2
 
및
 
β
n
은
 
모
델
의
 
매
개
 
변
수
입
니
다
.




따
라
서
 
예
측
된
 
반
응
 
값
은
 
위
의
 
방
정
식
으
로
 
주
어
지
며
 
z
로
 
표
시
됩
니
다
.


#
#
 
*
*
S
i
g
m
o
i
d
 
F
u
n
c
t
i
o
n
*
*




이
러
한
 
예
측
된
 
응
답
값
 
z
는
 
0
과
 
1
 
사
이
의
 
확
률
 
값
으
로
 
변
환
됩
니
다
.
 
예
측
된
 
값
에
서
 
확
률
 
값
으
로
 
변
환
하
기
 
위
해
 
시
그
모
이
드
 
함
수
를
 
사
용
합
니
다
.
 
이
 
시
그
모
이
드
 
함
수
는
 
임
의
의
 
실
수
 
값
을
 
0
과
 
1
 
사
이
의
 
확
률
 
값
으
로
 
매
핑
합
니
다
.




기
계
학
습
에
서
는
 
시
그
모
이
드
 
함
수
를
 
사
용
하
여
 
예
측
 
값
을
 
확
률
 
값
으
로
 
매
핑
합
니
다
.
 
시
그
모
이
드
 
함
수
는
 
S
자
 
모
양
의
 
곡
선
을
 
가
지
고
 
있
으
며
,
 
s
i
g
m
o
i
d
 
c
u
r
v
e
라
고
도
 
불
립
니
다
.




시
그
모
이
드
 
함
수
는
 
로
지
스
틱
 
함
수
의
 
특
수
한
 
경
우
입
니
다
.
 
다
음
과
 
같
은
 
수
식
으
로
 
표
현
됩
니
다
.




그
래
프
로
는
 
다
음
과
 
같
이
 
시
그
모
이
드
 
함
수
를
 
나
타
낼
 
수
 
있
습
니
다
.


#
#
#
 
S
i
g
m
o
i
d
 
F
u
n
c
t
i
o
n




!
[
S
i
g
m
o
i
d
 
F
u
n
c
t
i
o
n
]
(
h
t
t
p
s
:
/
/
m
i
r
o
.
m
e
d
i
u
m
.
c
o
m
/
m
a
x
/
9
7
0
/
1
*
X
u
7
B
5
y
9
g
p
0
i
L
5
o
o
B
j
7
L
t
W
w
.
p
n
g
)


#
#
 
*
*
D
e
c
i
s
i
o
n
 
b
o
u
n
d
a
r
y
*
*




s
i
g
m
o
i
d
 
함
수
는
 
0
과
 
1
 
사
이
의
 
확
률
 
값
을
 
반
환
합
니
다
.
 
이
 
확
률
 
값
은
 
"
0
"
 
또
는
 
"
1
"
인
 
이
산
 
클
래
스
로
 
매
핑
됩
니
다
.
 
이
 
확
률
 
값
을
 
이
산
 
클
래
스
로
 
매
핑
하
기
 
위
해
서
는
 
임
계
값
을
 
선
택
해
야
 
합
니
다
.
 
이
 
임
계
값
은
 
결
정
 
경
계
(
d
e
c
i
s
i
o
n
 
b
o
u
n
d
a
r
y
)
라
고
 
합
니
다
.
 
이
 
결
정
 
경
계
 
값
 
이
상
의
 
값
은
 
클
래
스
 
1
로
 
매
핑
하
고
,
 
이
하
의
 
값
은
 
클
래
스
 
0
으
로
 
매
핑
합
니
다
.




수
학
적
으
로
는
 
다
음
과
 
같
이
 
표
현
될
 
수
 
있
습
니
다
.




p
 
≥
 
0
.
5
 
=
>
 
클
래
스
 
=
 
1




p
 
<
 
0
.
5
 
=
>
 
클
래
스
 
=
 
0




일
반
적
으
로
 
결
정
 
경
계
는
 
0
.
5
로
 
설
정
됩
니
다
.
 
따
라
서
 
확
률
 
값
이
 
0
.
8
(
>
 
0
.
5
)
인
 
경
우
 
이
 
관
측
치
는
 
클
래
스
 
1
로
 
매
핑
됩
니
다
.
 
마
찬
가
지
로
,
 
확
률
 
값
이
 
0
.
2
(
<
 
0
.
5
)
인
 
경
우
 
이
 
관
측
치
는
 
클
래
스
 
0
으
로
 
매
핑
됩
니
다
.
 
이
것
은
 
아
래
 
그
래
프
에
서
 
나
타
납
니
다
.


!
[
D
e
c
i
s
i
o
n
 
b
o
u
n
d
a
r
y
 
i
n
 
s
i
g
m
o
i
d
 
f
u
n
c
t
i
o
n
]
(
h
t
t
p
s
:
/
/
m
l
-
c
h
e
a
t
s
h
e
e
t
.
r
e
a
d
t
h
e
d
o
c
s
.
i
o
/
e
n
/
l
a
t
e
s
t
/
_
i
m
a
g
e
s
/
l
o
g
i
s
t
i
c
_
r
e
g
r
e
s
s
i
o
n
_
s
i
g
m
o
i
d
_
w
_
t
h
r
e
s
h
o
l
d
.
p
n
g
)


#
#
 
*
*
M
a
k
i
n
g
 
p
r
e
d
i
c
t
i
o
n
s
*
*




이
제
 
로
지
스
틱
 
회
귀
에
서
 
시
그
모
이
드
 
함
수
와
 
결
정
 
경
계
에
 
대
해
 
알
았
습
니
다
.
 
우
리
는
 
시
그
모
이
드
 
함
수
와
 
결
정
 
경
계
에
 
대
한
 
지
식
을
 
활
용
하
여
 
예
측
 
함
수
를
 
작
성
할
 
수
 
있
습
니
다
.
 
로
지
스
틱
 
회
귀
의
 
예
측
 
함
수
는
 
관
측
값
이
 
양
성
인
(
Y
e
s
 
또
는
 
T
r
u
e
)
 
클
래
스
 
1
에
 
속
할
 
확
률
을
 
반
환
합
니
다
.
 
이
는
 
P
(
c
l
a
s
s
 
=
 
1
)
로
 
표
시
되
며
,
 
이
 
확
률
이
 
1
에
 
가
까
워
질
수
록
 
모
델
이
 
관
측
값
이
 
클
래
스
 
1
에
 
속
한
다
고
 
더
 
자
신
 
있
게
 
판
단
할
 
수
 
있
으
며
,
 
그
렇
지
 
않
으
면
 
클
래
스
 
0
에
 
속
한
다
고
 
판
단
할
 
수
 
있
습
니
다
.




#
 
*
*
3
.
 
A
s
s
u
m
p
t
i
o
n
s
 
o
f
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
3
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






로
지
스
틱
 
회
귀
 
모
델
은
 
몇
 
가
지
 
주
요
 
가
정
이
 
필
요
합
니
다
.
 
이
는
 
다
음
과
 
같
습
니
다
:




1
.
 
로
지
스
틱
 
회
귀
 
모
델
은
 
종
속
 
변
수
가
 
이
항
,
 
다
항
 
또
는
 
순
서
형
인
 
것
을
 
요
구
합
니
다
.




2
.
 
반
복
 
측
정
에
서
 
나
온
 
것
이
 
아
닌
 
독
립
적
인
 
관
측
치
가
 
필
요
합
니
다
.




3
.
 
로
지
스
틱
 
회
귀
 
알
고
리
즘
은
 
독
립
 
변
수
 
간
 
다
중
공
선
성
이
 
적
거
나
 
없
어
야
 
합
니
다
.
 
즉
,
 
독
립
 
변
수
들
은
 
서
로
 
너
무
 
높
게
 
상
관
되
어
 
있
어
서
는
 
안
 
됩
니
다
.




4
.
 
로
지
스
틱
 
회
귀
 
모
델
은
 
독
립
 
변
수
와
 
로
그
 
오
즈
의
 
선
형
성
을
 
가
정
합
니
다
.




5
.
 
로
지
스
틱
 
회
귀
 
모
델
의
 
성
공
은
 
샘
플
 
크
기
에
 
따
라
 
달
라
집
니
다
.
 
일
반
적
으
로
 
높
은
 
정
확
도
를
 
달
성
하
려
면
 
큰
 
샘
플
 
크
기
가
 
필
요
합
니
다
.


#
 
*
*
4
.
 
T
y
p
e
s
 
o
f
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
4
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






로
지
스
틱
 
회
귀
 
모
델
은
 
대
상
 
변
수
 
카
테
고
리
에
 
따
라
 
세
 
가
지
 
그
룹
으
로
 
분
류
될
 
수
 
있
습
니
다
.
 
이
 
세
 
가
지
 
그
룹
은
 
아
래
와
 
같
이
 
설
명
됩
니
다
.




#
#
#
 
1
.
 
이
항
 
로
지
스
틱
 
회
귀
(
B
i
n
a
r
y
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
)


이
항
 
로
지
스
틱
 
회
귀
에
서
 
대
상
 
변
수
는
 
두
 
가
지
 
가
능
한
 
범
주
를
 
가
지
고
 
있
습
니
다
.
 
대
표
적
인
 
예
시
로
는
 
y
e
s
 
o
r
 
n
o
,
 
g
o
o
d
 
o
r
 
b
a
d
,
 
t
r
u
e
 
o
r
 
f
a
l
s
e
,
 
s
p
a
m
 
o
r
 
n
o
 
s
p
a
m
,
 
p
a
s
s
 
o
r
 
f
a
i
l
 
등
이
 
있
습
니
다
.




#
#
#
 
2
.
 
다
항
 
로
지
스
틱
 
회
귀
(
M
u
l
t
i
n
o
m
i
a
l
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
)


다
항
 
로
지
스
틱
 
회
귀
에
서
 
대
상
 
변
수
는
 
정
해
진
 
순
서
가
 
없
는
 
세
 
개
 
이
상
의
 
범
주
를
 
가
지
고
 
있
습
니
다
.
 
즉
,
 
세
 
개
 
이
상
의
 
명
목
 
범
주
가
 
있
습
니
다
.
 
예
시
로
는
 
과
일
의
 
종
류
 
-
 
사
과
,
 
망
고
,
 
오
렌
지
,
 
바
나
나
 
등
이
 
있
습
니
다
.




#
#
#
 
3
.
 
순
서
형
 
로
지
스
틱
 
회
귀
(
O
r
d
i
n
a
l
 
L
o
g
i
s
t
i
c
 
R
e
g
r
e
s
s
i
o
n
)


순
서
형
 
로
지
스
틱
 
회
귀
에
서
 
대
상
 
변
수
는
 
세
 
개
 
이
상
의
 
순
서
형
 
범
주
를
 
가
지
고
 
있
습
니
다
.
 
즉
,
 
범
주
 
사
이
에
 
내
재
적
인
 
순
서
가
 
있
습
니
다
.
 
예
를
 
들
어
,
 
학
생
 
성
적
은
 
p
o
o
r
,
 
a
v
e
r
a
g
e
,
 
g
o
o
d
,
 
e
x
c
e
l
l
e
n
t
와
 
같
이
 
분
류
할
 
수
 
있
습
니
다
.


#
 
*
*
5
.
 
I
m
p
o
r
t
 
l
i
b
r
a
r
i
e
s
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
5
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
#
 
T
h
i
s
 
P
y
t
h
o
n
 
3
 
e
n
v
i
r
o
n
m
e
n
t
 
c
o
m
e
s
 
w
i
t
h
 
m
a
n
y
 
h
e
l
p
f
u
l
 
a
n
a
l
y
t
i
c
s
 
l
i
b
r
a
r
i
e
s
 
i
n
s
t
a
l
l
e
d

#
 
I
t
 
i
s
 
d
e
f
i
n
e
d
 
b
y
 
t
h
e
 
k
a
g
g
l
e
/
p
y
t
h
o
n
 
d
o
c
k
e
r
 
i
m
a
g
e
:
 
h
t
t
p
s
:
/
/
g
i
t
h
u
b
.
c
o
m
/
k
a
g
g
l
e
/
d
o
c
k
e
r
-
p
y
t
h
o
n

#
 
F
o
r
 
e
x
a
m
p
l
e
,
 
h
e
r
e
'
s
 
s
e
v
e
r
a
l
 
h
e
l
p
f
u
l
 
p
a
c
k
a
g
e
s
 
t
o
 
l
o
a
d
 
i
n
 


i
m
p
o
r
t
 
n
u
m
p
y
 
a
s
 
n
p
 
#
 
l
i
n
e
a
r
 
a
l
g
e
b
r
a

i
m
p
o
r
t
 
p
a
n
d
a
s
 
a
s
 
p
d
 
#
 
d
a
t
a
 
p
r
o
c
e
s
s
i
n
g
,
 
C
S
V
 
f
i
l
e
 
I
/
O
 
(
e
.
g
.
 
p
d
.
r
e
a
d
_
c
s
v
)

i
m
p
o
r
t
 
m
a
t
p
l
o
t
l
i
b
.
p
y
p
l
o
t
 
a
s
 
p
l
t
 
#
 
d
a
t
a
 
v
i
s
u
a
l
i
z
a
t
i
o
n

i
m
p
o
r
t
 
s
e
a
b
o
r
n
 
a
s
 
s
n
s
 
#
 
s
t
a
t
i
s
t
i
c
a
l
 
d
a
t
a
 
v
i
s
u
a
l
i
z
a
t
i
o
n

%
m
a
t
p
l
o
t
l
i
b
 
i
n
l
i
n
e


#
 
I
n
p
u
t
 
d
a
t
a
 
f
i
l
e
s
 
a
r
e
 
a
v
a
i
l
a
b
l
e
 
i
n
 
t
h
e
 
"
.
.
/
i
n
p
u
t
/
"
 
d
i
r
e
c
t
o
r
y
.

#
 
F
o
r
 
e
x
a
m
p
l
e
,
 
r
u
n
n
i
n
g
 
t
h
i
s
 
(
b
y
 
c
l
i
c
k
i
n
g
 
r
u
n
 
o
r
 
p
r
e
s
s
i
n
g
 
S
h
i
f
t
+
E
n
t
e
r
)
 
w
i
l
l
 
l
i
s
t
 
a
l
l
 
f
i
l
e
s
 
u
n
d
e
r
 
t
h
e
 
i
n
p
u
t
 
d
i
r
e
c
t
o
r
y


i
m
p
o
r
t
 
o
s

f
o
r
 
d
i
r
n
a
m
e
,
 
_
,
 
f
i
l
e
n
a
m
e
s
 
i
n
 
o
s
.
w
a
l
k
(
'
/
k
a
g
g
l
e
/
i
n
p
u
t
'
)
:

 
 
 
 
f
o
r
 
f
i
l
e
n
a
m
e
 
i
n
 
f
i
l
e
n
a
m
e
s
:

 
 
 
 
 
 
 
 
p
r
i
n
t
(
o
s
.
p
a
t
h
.
j
o
i
n
(
d
i
r
n
a
m
e
,
 
f
i
l
e
n
a
m
e
)
)


#
 
A
n
y
 
r
e
s
u
l
t
s
 
y
o
u
 
w
r
i
t
e
 
t
o
 
t
h
e
 
c
u
r
r
e
n
t
 
d
i
r
e
c
t
o
r
y
 
a
r
e
 
s
a
v
e
d
 
a
s
 
o
u
t
p
u
t
.

```

<pre>
/
k
a
g
g
l
e
/
i
n
p
u
t
/
w
e
a
t
h
e
r
-
d
a
t
a
s
e
t
-
r
a
t
t
l
e
-
p
a
c
k
a
g
e
/
w
e
a
t
h
e
r
A
U
S
.
c
s
v

</pre>

```python
i
m
p
o
r
t
 
w
a
r
n
i
n
g
s


w
a
r
n
i
n
g
s
.
f
i
l
t
e
r
w
a
r
n
i
n
g
s
(
'
i
g
n
o
r
e
'
)
```

#
 
*
*
6
.
 
I
m
p
o
r
t
 
d
a
t
a
s
e
t
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
6
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
d
a
t
a
 
=
 
'
/
k
a
g
g
l
e
/
i
n
p
u
t
/
w
e
a
t
h
e
r
-
d
a
t
a
s
e
t
-
r
a
t
t
l
e
-
p
a
c
k
a
g
e
/
w
e
a
t
h
e
r
A
U
S
.
c
s
v
'


d
f
 
=
 
p
d
.
r
e
a
d
_
c
s
v
(
d
a
t
a
)
```

#
 
*
*
7
.
 
E
x
p
l
o
r
a
t
o
r
y
 
d
a
t
a
 
a
n
a
l
y
s
i
s
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
7
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






이
제
 
데
이
터
를
 
탐
색
하
여
 
데
이
터
에
 
대
한
 
인
사
이
트
를
 
얻
겠
습
니
다



```python
#
 
v
i
e
w
 
d
i
m
e
n
s
i
o
n
s
 
o
f
 
d
a
t
a
s
e
t


d
f
.
s
h
a
p
e
```

<pre>
(
1
4
5
4
6
0
,
 
2
3
)
</pre>
데
이
터
 
세
트
에
는
 
1
4
2
1
9
3
개
의
 
인
스
턴
스
와
 
2
4
개
의
 
변
수
가
 
있
음
을
 
알
 
수
 
있
습
니
다
.
.



```python
#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t


d
f
.
h
e
a
d
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
D
a
t
e
 
L
o
c
a
t
i
o
n
 
 
M
i
n
T
e
m
p
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
 
\

0
 
 
2
0
0
8
-
1
2
-
0
1
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
3
.
4
 
 
 
 
 
2
2
.
9
 
 
 
 
 
 
 
0
.
6
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 

1
 
 
2
0
0
8
-
1
2
-
0
2
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
7
.
4
 
 
 
 
 
2
5
.
1
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 

2
 
 
2
0
0
8
-
1
2
-
0
3
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
2
.
9
 
 
 
 
 
2
5
.
7
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 

3
 
 
2
0
0
8
-
1
2
-
0
4
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
9
.
2
 
 
 
 
 
2
8
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 

4
 
 
2
0
0
8
-
1
2
-
0
5
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
7
.
5
 
 
 
 
 
3
2
.
3
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 


 
 
W
i
n
d
G
u
s
t
D
i
r
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
W
i
n
d
D
i
r
9
a
m
 
 
.
.
.
 
H
u
m
i
d
i
t
y
9
a
m
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
\

0
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
 
 
W
 
 
.
.
.
 
 
 
 
 
 
 
 
7
1
.
0
 
 
 
 
 
 
 
 
 
2
2
.
0
 
 
 

1
 
 
 
 
 
 
 
 
 
W
N
W
 
 
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
N
N
W
 
 
.
.
.
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
 
2
5
.
0
 
 
 

2
 
 
 
 
 
 
 
 
 
W
S
W
 
 
 
 
 
 
 
 
 
 
 
4
6
.
0
 
 
 
 
 
 
 
 
 
 
W
 
 
.
.
.
 
 
 
 
 
 
 
 
3
8
.
0
 
 
 
 
 
 
 
 
 
3
0
.
0
 
 
 

3
 
 
 
 
 
 
 
 
 
 
N
E
 
 
 
 
 
 
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
 
 
S
E
 
 
.
.
.
 
 
 
 
 
 
 
 
4
5
.
0
 
 
 
 
 
 
 
 
 
1
6
.
0
 
 
 

4
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
 
 
 
4
1
.
0
 
 
 
 
 
 
 
 
E
N
E
 
 
.
.
.
 
 
 
 
 
 
 
 
8
2
.
0
 
 
 
 
 
 
 
 
 
3
3
.
0
 
 
 


 
 
 
P
r
e
s
s
u
r
e
9
a
m
 
 
P
r
e
s
s
u
r
e
3
p
m
 
 
C
l
o
u
d
9
a
m
 
 
C
l
o
u
d
3
p
m
 
 
T
e
m
p
9
a
m
 
 
T
e
m
p
3
p
m
 
 
R
a
i
n
T
o
d
a
y
 
 
\

0
 
 
 
 
 
 
 
1
0
0
7
.
7
 
 
 
 
 
 
 
1
0
0
7
.
1
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
1
6
.
9
 
 
 
 
 
2
1
.
8
 
 
 
 
 
 
 
 
 
N
o
 
 
 

1
 
 
 
 
 
 
 
1
0
1
0
.
6
 
 
 
 
 
 
 
1
0
0
7
.
8
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
1
7
.
2
 
 
 
 
 
2
4
.
3
 
 
 
 
 
 
 
 
 
N
o
 
 
 

2
 
 
 
 
 
 
 
1
0
0
7
.
6
 
 
 
 
 
 
 
1
0
0
8
.
7
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
2
.
0
 
 
 
 
 
2
1
.
0
 
 
 
 
 
2
3
.
2
 
 
 
 
 
 
 
 
 
N
o
 
 
 

3
 
 
 
 
 
 
 
1
0
1
7
.
6
 
 
 
 
 
 
 
1
0
1
2
.
8
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
1
8
.
1
 
 
 
 
 
2
6
.
5
 
 
 
 
 
 
 
 
 
N
o
 
 
 

4
 
 
 
 
 
 
 
1
0
1
0
.
8
 
 
 
 
 
 
 
1
0
0
6
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
1
7
.
8
 
 
 
 
 
2
9
.
7
 
 
 
 
 
 
 
 
 
N
o
 
 
 


 
 
 
R
a
i
n
T
o
m
o
r
r
o
w
 
 

0
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

1
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

2
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

3
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

4
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 


[
5
 
r
o
w
s
 
x
 
2
3
 
c
o
l
u
m
n
s
]
</pre>

```python
c
o
l
_
n
a
m
e
s
 
=
 
d
f
.
c
o
l
u
m
n
s


c
o
l
_
n
a
m
e
s
```

<pre>
I
n
d
e
x
(
[
'
D
a
t
e
'
,
 
'
L
o
c
a
t
i
o
n
'
,
 
'
M
i
n
T
e
m
p
'
,
 
'
M
a
x
T
e
m
p
'
,
 
'
R
a
i
n
f
a
l
l
'
,
 
'
E
v
a
p
o
r
a
t
i
o
n
'
,

 
 
 
 
 
 
 
'
S
u
n
s
h
i
n
e
'
,
 
'
W
i
n
d
G
u
s
t
D
i
r
'
,
 
'
W
i
n
d
G
u
s
t
S
p
e
e
d
'
,
 
'
W
i
n
d
D
i
r
9
a
m
'
,
 
'
W
i
n
d
D
i
r
3
p
m
'
,

 
 
 
 
 
 
 
'
W
i
n
d
S
p
e
e
d
9
a
m
'
,
 
'
W
i
n
d
S
p
e
e
d
3
p
m
'
,
 
'
H
u
m
i
d
i
t
y
9
a
m
'
,
 
'
H
u
m
i
d
i
t
y
3
p
m
'
,

 
 
 
 
 
 
 
'
P
r
e
s
s
u
r
e
9
a
m
'
,
 
'
P
r
e
s
s
u
r
e
3
p
m
'
,
 
'
C
l
o
u
d
9
a
m
'
,
 
'
C
l
o
u
d
3
p
m
'
,
 
'
T
e
m
p
9
a
m
'
,

 
 
 
 
 
 
 
'
T
e
m
p
3
p
m
'
,
 
'
R
a
i
n
T
o
d
a
y
'
,
 
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
,

 
 
 
 
 
 
d
t
y
p
e
=
'
o
b
j
e
c
t
'
)
</pre>
#
#
#
 
D
r
o
p
 
 
R
I
S
K
_
M
M
 
v
a
r
i
a
b
l
e




I
t
 
i
s
 
g
i
v
e
n
 
i
n
 
t
h
e
 
d
a
t
a
s
e
t
 
d
e
s
c
r
i
p
t
i
o
n
,
 
t
h
a
t
 
w
e
 
s
h
o
u
l
d
 
d
r
o
p
 
t
h
e
 
`
R
I
S
K
_
M
M
`
 
f
e
a
t
u
r
e
 
v
a
r
i
a
b
l
e
 
f
r
o
m
 
t
h
e
 
d
a
t
a
s
e
t
 
d
e
s
c
r
i
p
t
i
o
n
.
 
S
o
,
 
w
e
 


s
h
o
u
l
d
 
d
r
o
p
 
i
t
 
a
s
 
f
o
l
l
o
w
s
-



```python
#
d
f
.
d
r
o
p
(
[
'
R
I
S
K
_
M
M
'
]
,
 
a
x
i
s
=
1
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)
```


```python
#
 
v
i
e
w
 
s
u
m
m
a
r
y
 
o
f
 
d
a
t
a
s
e
t


d
f
.
i
n
f
o
(
)
```

<pre>
<
c
l
a
s
s
 
'
p
a
n
d
a
s
.
c
o
r
e
.
f
r
a
m
e
.
D
a
t
a
F
r
a
m
e
'
>

R
a
n
g
e
I
n
d
e
x
:
 
1
4
5
4
6
0
 
e
n
t
r
i
e
s
,
 
0
 
t
o
 
1
4
5
4
5
9

D
a
t
a
 
c
o
l
u
m
n
s
 
(
t
o
t
a
l
 
2
3
 
c
o
l
u
m
n
s
)
:

D
a
t
e
 
 
 
 
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
1
4
3
9
7
5
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
1
4
4
1
9
9
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
1
4
2
1
9
9
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
8
2
6
7
0
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
7
5
6
2
5
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
 
1
3
5
1
3
4
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
1
3
5
1
9
7
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
 
1
3
4
8
9
4
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
1
4
1
2
3
2
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
1
4
3
6
9
3
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
1
4
2
3
9
8
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
1
4
2
8
0
6
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
1
4
0
9
5
3
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
1
3
0
3
9
5
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
1
3
0
4
3
2
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
8
9
5
7
2
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
8
6
1
0
2
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
1
4
3
6
9
3
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
1
4
1
8
5
1
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
1
4
2
1
9
9
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

R
a
i
n
T
o
m
o
r
r
o
w
 
 
 
 
 
1
4
2
1
9
3
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

d
t
y
p
e
s
:
 
f
l
o
a
t
6
4
(
1
6
)
,
 
o
b
j
e
c
t
(
7
)

m
e
m
o
r
y
 
u
s
a
g
e
:
 
2
5
.
5
+
 
M
B

</pre>
#
#
#
 
T
y
p
e
s
 
o
f
 
v
a
r
i
a
b
l
e
s






이
 
섹
션
에
서
는
 
데
이
터
셋
을
 
범
주
형
 
변
수
와
 
수
치
형
 
변
수
로
 
분
리
합
니
다
.
 
데
이
터
셋
에
는
 
범
주
형
 
변
수
와
 
수
치
형
 
변
수
가
 
혼
합
되
어
 
있
습
니
다
.
 
범
주
형
 
변
수
는
 
데
이
터
 
타
입
이
 
o
b
j
e
c
t
입
니
다
.
 
수
치
형
 
변
수
는
 
데
이
터
 
타
입
이
 
f
l
o
a
t
6
4
입
니
다
.




먼
저
 
범
주
형
 
변
수
를
 
찾
아
보
겠
습
니
다
.



```python
#
 
f
i
n
d
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


c
a
t
e
g
o
r
i
c
a
l
 
=
 
[
v
a
r
 
f
o
r
 
v
a
r
 
i
n
 
d
f
.
c
o
l
u
m
n
s
 
i
f
 
d
f
[
v
a
r
]
.
d
t
y
p
e
=
=
'
O
'
]


p
r
i
n
t
(
'
T
h
e
r
e
 
a
r
e
 
{
}
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
\
n
'
.
f
o
r
m
a
t
(
l
e
n
(
c
a
t
e
g
o
r
i
c
a
l
)
)
)


p
r
i
n
t
(
'
T
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
a
r
e
 
:
'
,
 
c
a
t
e
g
o
r
i
c
a
l
)
```

<pre>
T
h
e
r
e
 
a
r
e
 
7
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


T
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
a
r
e
 
:
 
[
'
D
a
t
e
'
,
 
'
L
o
c
a
t
i
o
n
'
,
 
'
W
i
n
d
G
u
s
t
D
i
r
'
,
 
'
W
i
n
d
D
i
r
9
a
m
'
,
 
'
W
i
n
d
D
i
r
3
p
m
'
,
 
'
R
a
i
n
T
o
d
a
y
'
,
 
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]

</pre>

```python
#
 
v
i
e
w
 
t
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


d
f
[
c
a
t
e
g
o
r
i
c
a
l
]
.
h
e
a
d
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
D
a
t
e
 
L
o
c
a
t
i
o
n
 
W
i
n
d
G
u
s
t
D
i
r
 
W
i
n
d
D
i
r
9
a
m
 
W
i
n
d
D
i
r
3
p
m
 
R
a
i
n
T
o
d
a
y
 
 
\

0
 
 
2
0
0
8
-
1
2
-
0
1
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
W
N
W
 
 
 
 
 
 
 
 
N
o
 
 
 

1
 
 
2
0
0
8
-
1
2
-
0
2
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
W
N
W
 
 
 
 
 
 
 
 
N
N
W
 
 
 
 
 
 
 
 
W
S
W
 
 
 
 
 
 
 
 
N
o
 
 
 

2
 
 
2
0
0
8
-
1
2
-
0
3
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
W
S
W
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
W
S
W
 
 
 
 
 
 
 
 
N
o
 
 
 

3
 
 
2
0
0
8
-
1
2
-
0
4
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
N
E
 
 
 
 
 
 
 
 
 
S
E
 
 
 
 
 
 
 
 
 
 
E
 
 
 
 
 
 
 
 
N
o
 
 
 

4
 
 
2
0
0
8
-
1
2
-
0
5
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
E
N
E
 
 
 
 
 
 
 
 
 
N
W
 
 
 
 
 
 
 
 
N
o
 
 
 


 
 
R
a
i
n
T
o
m
o
r
r
o
w
 
 

0
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

1
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

2
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

3
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 

4
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 
</pre>
#
#
#
 
S
u
m
m
a
r
y
 
o
f
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s




-
 
데
이
터
에
는
 
D
a
t
e
 
열
이
 
있
는
 
날
짜
 
변
수
가
 
있
습
니
다
.


-
 
L
o
c
a
t
i
o
n
,
 
W
i
n
d
G
u
s
t
D
i
r
,
 
W
i
n
d
D
i
r
9
a
m
,
 
W
i
n
d
D
i
r
3
p
m
,
 
R
a
i
n
T
o
d
a
y
,
 
R
a
i
n
T
o
m
o
r
r
o
w
와
 
같
이
 
총
 
6
개
의
 
범
주
-
형
 
변
수
가
 
있
습
니
다
.


-
 
R
a
i
n
T
o
d
a
y
와
 
R
a
i
n
T
o
m
o
r
r
o
w
는
 
이
진
 
범
주
형
 
변
수
입
니
다
.


-
 
R
a
i
n
T
o
m
o
r
r
o
w
은
 
타
겟
 
변
수
입
니
다
.


#
#
 
E
x
p
l
o
r
e
 
p
r
o
b
l
e
m
s
 
w
i
t
h
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s






이
제
 
범
주
형
의
 
결
측
치
를
 
찾
아
봅
니
다
.






#
#
#
 
M
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s



```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


d
f
[
c
a
t
e
g
o
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
D
a
t
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
1
0
3
2
6

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
1
0
5
6
6

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
4
2
2
8

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
3
2
6
1

R
a
i
n
T
o
m
o
r
r
o
w
 
 
 
 
 
3
2
6
7

d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
p
r
i
n
t
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
c
o
n
t
a
i
n
i
n
g
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s


c
a
t
1
 
=
 
[
v
a
r
 
f
o
r
 
v
a
r
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
i
f
 
d
f
[
v
a
r
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
!
=
0
]


p
r
i
n
t
(
d
f
[
c
a
t
1
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
)
```

<pre>
W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
1
0
3
2
6

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
1
0
5
6
6

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
4
2
2
8

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
3
2
6
1

R
a
i
n
T
o
m
o
r
r
o
w
 
 
 
 
 
3
2
6
7

d
t
y
p
e
:
 
i
n
t
6
4

</pre>
우
리
는
 
총
 
4
개
의
 
결
측
치
가
 
있
는
 
범
주
형
 
데
이
터
를
 
찾
을
 
수
 
있
습
니
다
.
 
`
W
i
n
d
G
u
s
t
D
i
r
`
,
 
`
W
i
n
d
D
i
r
9
a
m
`
,
 
`
W
i
n
d
D
i
r
3
p
m
`
,
 
`
R
a
i
n
T
o
d
a
y
`
.


#
#
#
 
F
r
e
q
u
e
n
c
y
 
c
o
u
n
t
s
 
o
f
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s






이
제
 
빈
도
 
수
를
 
확
인
하
여
 
각
 
범
주
형
 
변
수
가
 
가
지
고
 
있
는
 
값
들
의
 
분
포
를
 
파
악
할
 
수
 
있
습
니
다
.



```python
#
 
v
i
e
w
 
f
r
e
q
u
e
n
c
y
 
o
f
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


f
o
r
 
v
a
r
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
:
 

 
 
 
 

 
 
 
 
p
r
i
n
t
(
d
f
[
v
a
r
]
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
)
```

<pre>
2
0
1
5
-
1
1
-
0
2
 
 
 
 
4
9

2
0
1
3
-
0
6
-
1
8
 
 
 
 
4
9

2
0
1
6
-
0
1
-
1
2
 
 
 
 
4
9

2
0
1
6
-
1
2
-
0
8
 
 
 
 
4
9

2
0
1
6
-
0
4
-
0
6
 
 
 
 
4
9

 
 
 
 
 
 
 
 
 
 
 
 
 
 
.
.

2
0
0
8
-
0
1
-
2
5
 
 
 
 
 
1

2
0
0
7
-
1
1
-
3
0
 
 
 
 
 
1

2
0
0
7
-
1
1
-
0
5
 
 
 
 
 
1

2
0
0
7
-
1
1
-
1
0
 
 
 
 
 
1

2
0
0
8
-
0
1
-
0
8
 
 
 
 
 
1

N
a
m
e
:
 
D
a
t
e
,
 
L
e
n
g
t
h
:
 
3
4
3
6
,
 
d
t
y
p
e
:
 
i
n
t
6
4

C
a
n
b
e
r
r
a
 
 
 
 
 
 
 
 
 
 
 
 
3
4
3
6

S
y
d
n
e
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
3
4
4

B
r
i
s
b
a
n
e
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

P
e
r
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

A
d
e
l
a
i
d
e
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

H
o
b
a
r
t
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

M
e
l
b
o
u
r
n
e
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

D
a
r
w
i
n
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

B
a
l
l
a
r
a
t
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

C
a
i
r
n
s
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

T
o
w
n
s
v
i
l
l
e
 
 
 
 
 
 
 
 
 
 
3
0
4
0

M
o
u
n
t
G
i
n
i
n
i
 
 
 
 
 
 
 
 
 
3
0
4
0

M
o
u
n
t
G
a
m
b
i
e
r
 
 
 
 
 
 
 
 
3
0
4
0

A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

B
e
n
d
i
g
o
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

A
l
i
c
e
S
p
r
i
n
g
s
 
 
 
 
 
 
 
 
3
0
4
0

G
o
l
d
C
o
a
s
t
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

L
a
u
n
c
e
s
t
o
n
 
 
 
 
 
 
 
 
 
 
3
0
4
0

A
l
b
a
n
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

W
o
l
l
o
n
g
o
n
g
 
 
 
 
 
 
 
 
 
 
3
0
4
0

N
e
w
c
a
s
t
l
e
 
 
 
 
 
 
 
 
 
 
 
3
0
3
9

P
e
n
r
i
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
3
9

T
u
g
g
e
r
a
n
o
n
g
 
 
 
 
 
 
 
 
 
3
0
3
9

W
i
t
c
h
c
l
i
f
f
e
 
 
 
 
 
 
 
 
 
3
0
0
9

N
o
r
f
o
l
k
I
s
l
a
n
d
 
 
 
 
 
 
 
3
0
0
9

C
o
f
f
s
H
a
r
b
o
u
r
 
 
 
 
 
 
 
 
3
0
0
9

M
e
l
b
o
u
r
n
e
A
i
r
p
o
r
t
 
 
 
 
3
0
0
9

P
e
r
t
h
A
i
r
p
o
r
t
 
 
 
 
 
 
 
 
3
0
0
9

M
o
r
e
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

S
y
d
n
e
y
A
i
r
p
o
r
t
 
 
 
 
 
 
 
3
0
0
9

W
i
l
l
i
a
m
t
o
w
n
 
 
 
 
 
 
 
 
 
3
0
0
9

P
o
r
t
l
a
n
d
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

P
e
a
r
c
e
R
A
A
F
 
 
 
 
 
 
 
 
 
 
3
0
0
9

W
a
t
s
o
n
i
a
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

N
u
r
i
o
o
t
p
a
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

W
a
g
g
a
W
a
g
g
a
 
 
 
 
 
 
 
 
 
 
3
0
0
9

M
i
l
d
u
r
a
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

R
i
c
h
m
o
n
d
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

C
o
b
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

S
a
l
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

D
a
r
t
m
o
o
r
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

W
o
o
m
e
r
a
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

B
a
d
g
e
r
y
s
C
r
e
e
k
 
 
 
 
 
 
 
3
0
0
9

W
a
l
p
o
l
e
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
6

N
o
r
a
h
H
e
a
d
 
 
 
 
 
 
 
 
 
 
 
3
0
0
4

S
a
l
m
o
n
G
u
m
s
 
 
 
 
 
 
 
 
 
 
3
0
0
1

U
l
u
r
u
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
1
5
7
8

N
h
i
l
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
1
5
7
8

K
a
t
h
e
r
i
n
e
 
 
 
 
 
 
 
 
 
 
 
1
5
7
8

N
a
m
e
:
 
L
o
c
a
t
i
o
n
,
 
d
t
y
p
e
:
 
i
n
t
6
4

W
 
 
 
 
 
 
9
9
1
5

S
E
 
 
 
 
 
9
4
1
8

N
 
 
 
 
 
 
9
3
1
3

S
S
E
 
 
 
 
9
2
1
6

E
 
 
 
 
 
 
9
1
8
1

S
 
 
 
 
 
 
9
1
6
8

W
S
W
 
 
 
 
9
0
6
9

S
W
 
 
 
 
 
8
9
6
7

S
S
W
 
 
 
 
8
7
3
6

W
N
W
 
 
 
 
8
2
5
2

N
W
 
 
 
 
 
8
1
2
2

E
N
E
 
 
 
 
8
1
0
4

E
S
E
 
 
 
 
7
3
7
2

N
E
 
 
 
 
 
7
1
3
3

N
N
W
 
 
 
 
6
6
2
0

N
N
E
 
 
 
 
6
5
4
8

N
a
m
e
:
 
W
i
n
d
G
u
s
t
D
i
r
,
 
d
t
y
p
e
:
 
i
n
t
6
4

N
 
 
 
 
 
 
1
1
7
5
8

S
E
 
 
 
 
 
 
9
2
8
7

E
 
 
 
 
 
 
 
9
1
7
6

S
S
E
 
 
 
 
 
9
1
1
2

N
W
 
 
 
 
 
 
8
7
4
9

S
 
 
 
 
 
 
 
8
6
5
9

W
 
 
 
 
 
 
 
8
4
5
9

S
W
 
 
 
 
 
 
8
4
2
3

N
N
E
 
 
 
 
 
8
1
2
9

N
N
W
 
 
 
 
 
7
9
8
0

E
N
E
 
 
 
 
 
7
8
3
6

N
E
 
 
 
 
 
 
7
6
7
1

E
S
E
 
 
 
 
 
7
6
3
0

S
S
W
 
 
 
 
 
7
5
8
7

W
N
W
 
 
 
 
 
7
4
1
4

W
S
W
 
 
 
 
 
7
0
2
4

N
a
m
e
:
 
W
i
n
d
D
i
r
9
a
m
,
 
d
t
y
p
e
:
 
i
n
t
6
4

S
E
 
 
 
 
 
1
0
8
3
8

W
 
 
 
 
 
 
1
0
1
1
0

S
 
 
 
 
 
 
 
9
9
2
6

W
S
W
 
 
 
 
 
9
5
1
8

S
S
E
 
 
 
 
 
9
3
9
9

S
W
 
 
 
 
 
 
9
3
5
4

N
 
 
 
 
 
 
 
8
8
9
0

W
N
W
 
 
 
 
 
8
8
7
4

N
W
 
 
 
 
 
 
8
6
1
0

E
S
E
 
 
 
 
 
8
5
0
5

E
 
 
 
 
 
 
 
8
4
7
2

N
E
 
 
 
 
 
 
8
2
6
3

S
S
W
 
 
 
 
 
8
1
5
6

N
N
W
 
 
 
 
 
7
8
7
0

E
N
E
 
 
 
 
 
7
8
5
7

N
N
E
 
 
 
 
 
6
5
9
0

N
a
m
e
:
 
W
i
n
d
D
i
r
3
p
m
,
 
d
t
y
p
e
:
 
i
n
t
6
4

N
o
 
 
 
 
 
1
1
0
3
1
9

Y
e
s
 
 
 
 
 
3
1
8
8
0

N
a
m
e
:
 
R
a
i
n
T
o
d
a
y
,
 
d
t
y
p
e
:
 
i
n
t
6
4

N
o
 
 
 
 
 
1
1
0
3
1
6

Y
e
s
 
 
 
 
 
3
1
8
7
7

N
a
m
e
:
 
R
a
i
n
T
o
m
o
r
r
o
w
,
 
d
t
y
p
e
:
 
i
n
t
6
4

</pre>

```python
#
 
v
i
e
w
 
f
r
e
q
u
e
n
c
y
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


f
o
r
 
v
a
r
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
:
 

 
 
 
 

 
 
 
 
p
r
i
n
t
(
d
f
[
v
a
r
]
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
/
n
p
.
f
l
o
a
t
(
l
e
n
(
d
f
)
)
)
```

<pre>
2
0
1
5
-
1
1
-
0
2
 
 
 
 
0
.
0
0
0
3
3
7

2
0
1
3
-
0
6
-
1
8
 
 
 
 
0
.
0
0
0
3
3
7

2
0
1
6
-
0
1
-
1
2
 
 
 
 
0
.
0
0
0
3
3
7

2
0
1
6
-
1
2
-
0
8
 
 
 
 
0
.
0
0
0
3
3
7

2
0
1
6
-
0
4
-
0
6
 
 
 
 
0
.
0
0
0
3
3
7

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
.
.
.
 
 
 

2
0
0
8
-
0
1
-
2
5
 
 
 
 
0
.
0
0
0
0
0
7

2
0
0
7
-
1
1
-
3
0
 
 
 
 
0
.
0
0
0
0
0
7

2
0
0
7
-
1
1
-
0
5
 
 
 
 
0
.
0
0
0
0
0
7

2
0
0
7
-
1
1
-
1
0
 
 
 
 
0
.
0
0
0
0
0
7

2
0
0
8
-
0
1
-
0
8
 
 
 
 
0
.
0
0
0
0
0
7

N
a
m
e
:
 
D
a
t
e
,
 
L
e
n
g
t
h
:
 
3
4
3
6
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

C
a
n
b
e
r
r
a
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
3
6
2
2

S
y
d
n
e
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
2
9
8
9

B
r
i
s
b
a
n
e
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
1
9
5
1

P
e
r
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
1
9
5
1

A
d
e
l
a
i
d
e
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
1
9
5
1

H
o
b
a
r
t
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
1
9
5
1

M
e
l
b
o
u
r
n
e
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
1
9
5
1

D
a
r
w
i
n
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
1
9
5
1

B
a
l
l
a
r
a
t
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

C
a
i
r
n
s
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

T
o
w
n
s
v
i
l
l
e
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

M
o
u
n
t
G
i
n
i
n
i
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

M
o
u
n
t
G
a
m
b
i
e
r
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

B
e
n
d
i
g
o
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

A
l
i
c
e
S
p
r
i
n
g
s
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

G
o
l
d
C
o
a
s
t
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

L
a
u
n
c
e
s
t
o
n
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

A
l
b
a
n
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

W
o
l
l
o
n
g
o
n
g
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
9

N
e
w
c
a
s
t
l
e
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
2

P
e
n
r
i
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
2

T
u
g
g
e
r
a
n
o
n
g
 
 
 
 
 
 
 
 
 
0
.
0
2
0
8
9
2

W
i
t
c
h
c
l
i
f
f
e
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

N
o
r
f
o
l
k
I
s
l
a
n
d
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

C
o
f
f
s
H
a
r
b
o
u
r
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

M
e
l
b
o
u
r
n
e
A
i
r
p
o
r
t
 
 
 
 
0
.
0
2
0
6
8
6

P
e
r
t
h
A
i
r
p
o
r
t
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

M
o
r
e
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

S
y
d
n
e
y
A
i
r
p
o
r
t
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

W
i
l
l
i
a
m
t
o
w
n
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

P
o
r
t
l
a
n
d
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

P
e
a
r
c
e
R
A
A
F
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

W
a
t
s
o
n
i
a
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

N
u
r
i
o
o
t
p
a
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

W
a
g
g
a
W
a
g
g
a
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

M
i
l
d
u
r
a
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

R
i
c
h
m
o
n
d
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

C
o
b
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

S
a
l
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

D
a
r
t
m
o
o
r
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

W
o
o
m
e
r
a
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

B
a
d
g
e
r
y
s
C
r
e
e
k
 
 
 
 
 
 
 
0
.
0
2
0
6
8
6

W
a
l
p
o
l
e
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
6
5

N
o
r
a
h
H
e
a
d
 
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
5
2

S
a
l
m
o
n
G
u
m
s
 
 
 
 
 
 
 
 
 
 
0
.
0
2
0
6
3
1

U
l
u
r
u
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
1
0
8
4
8

N
h
i
l
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
1
0
8
4
8

K
a
t
h
e
r
i
n
e
 
 
 
 
 
 
 
 
 
 
 
0
.
0
1
0
8
4
8

N
a
m
e
:
 
L
o
c
a
t
i
o
n
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

W
 
 
 
 
 
 
0
.
0
6
8
1
6
3

S
E
 
 
 
 
 
0
.
0
6
4
7
4
6

N
 
 
 
 
 
 
0
.
0
6
4
0
2
4

S
S
E
 
 
 
 
0
.
0
6
3
3
5
8

E
 
 
 
 
 
 
0
.
0
6
3
1
1
7

S
 
 
 
 
 
 
0
.
0
6
3
0
2
8

W
S
W
 
 
 
 
0
.
0
6
2
3
4
7

S
W
 
 
 
 
 
0
.
0
6
1
6
4
6

S
S
W
 
 
 
 
0
.
0
6
0
0
5
8

W
N
W
 
 
 
 
0
.
0
5
6
7
3
0

N
W
 
 
 
 
 
0
.
0
5
5
8
3
7

E
N
E
 
 
 
 
0
.
0
5
5
7
1
3

E
S
E
 
 
 
 
0
.
0
5
0
6
8
1

N
E
 
 
 
 
 
0
.
0
4
9
0
3
8

N
N
W
 
 
 
 
0
.
0
4
5
5
1
1

N
N
E
 
 
 
 
0
.
0
4
5
0
1
6

N
a
m
e
:
 
W
i
n
d
G
u
s
t
D
i
r
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

N
 
 
 
 
 
 
0
.
0
8
0
8
3
3

S
E
 
 
 
 
 
0
.
0
6
3
8
4
6

E
 
 
 
 
 
 
0
.
0
6
3
0
8
3

S
S
E
 
 
 
 
0
.
0
6
2
6
4
3

N
W
 
 
 
 
 
0
.
0
6
0
1
4
7

S
 
 
 
 
 
 
0
.
0
5
9
5
2
8

W
 
 
 
 
 
 
0
.
0
5
8
1
5
3

S
W
 
 
 
 
 
0
.
0
5
7
9
0
6

N
N
E
 
 
 
 
0
.
0
5
5
8
8
5

N
N
W
 
 
 
 
0
.
0
5
4
8
6
0

E
N
E
 
 
 
 
0
.
0
5
3
8
7
0

N
E
 
 
 
 
 
0
.
0
5
2
7
3
6

E
S
E
 
 
 
 
0
.
0
5
2
4
5
4

S
S
W
 
 
 
 
0
.
0
5
2
1
5
9

W
N
W
 
 
 
 
0
.
0
5
0
9
6
9

W
S
W
 
 
 
 
0
.
0
4
8
2
8
8

N
a
m
e
:
 
W
i
n
d
D
i
r
9
a
m
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

S
E
 
 
 
 
 
0
.
0
7
4
5
0
8

W
 
 
 
 
 
 
0
.
0
6
9
5
0
4

S
 
 
 
 
 
 
0
.
0
6
8
2
3
9

W
S
W
 
 
 
 
0
.
0
6
5
4
3
4

S
S
E
 
 
 
 
0
.
0
6
4
6
1
6

S
W
 
 
 
 
 
0
.
0
6
4
3
0
6

N
 
 
 
 
 
 
0
.
0
6
1
1
1
6

W
N
W
 
 
 
 
0
.
0
6
1
0
0
6

N
W
 
 
 
 
 
0
.
0
5
9
1
9
2

E
S
E
 
 
 
 
0
.
0
5
8
4
7
0

E
 
 
 
 
 
 
0
.
0
5
8
2
4
3

N
E
 
 
 
 
 
0
.
0
5
6
8
0
6

S
S
W
 
 
 
 
0
.
0
5
6
0
7
0

N
N
W
 
 
 
 
0
.
0
5
4
1
0
4

E
N
E
 
 
 
 
0
.
0
5
4
0
1
5

N
N
E
 
 
 
 
0
.
0
4
5
3
0
5

N
a
m
e
:
 
W
i
n
d
D
i
r
3
p
m
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

N
o
 
 
 
 
 
0
.
7
5
8
4
1
5

Y
e
s
 
 
 
 
0
.
2
1
9
1
6
7

N
a
m
e
:
 
R
a
i
n
T
o
d
a
y
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

N
o
 
 
 
 
 
0
.
7
5
8
3
9
4

Y
e
s
 
 
 
 
0
.
2
1
9
1
4
6

N
a
m
e
:
 
R
a
i
n
T
o
m
o
r
r
o
w
,
 
d
t
y
p
e
:
 
f
l
o
a
t
6
4

</pre>
#
#
#
 
N
u
m
b
e
r
 
o
f
 
l
a
b
e
l
s
:
 
c
a
r
d
i
n
a
l
i
t
y




카
테
고
리
 
변
수
 
내
 
라
벨
의
 
수
를
 
카
디
널
리
티
(
c
a
r
d
i
n
a
l
i
t
y
)
라
고
 
합
니
다
.
 
변
수
 
내
 
라
벨
의
 
수
가
 
많
을
수
록
(
h
i
g
h
 
c
a
r
d
i
n
a
l
i
t
y
)
 
머
신
 
러
닝
 
모
델
에
서
 
심
각
한
 
문
제
가
 
발
생
할
 
수
 
있
습
니
다
.
 
따
라
서
,
 
높
은
 
카
디
널
리
티
를
 
가
진
 
변
수
를
 
확
인
해
 
보
겠
습
니
다
.



```python
#
 
c
h
e
c
k
 
f
o
r
 
c
a
r
d
i
n
a
l
i
t
y
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


f
o
r
 
v
a
r
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
:

 
 
 
 

 
 
 
 
p
r
i
n
t
(
v
a
r
,
 
'
 
c
o
n
t
a
i
n
s
 
'
,
 
l
e
n
(
d
f
[
v
a
r
]
.
u
n
i
q
u
e
(
)
)
,
 
'
 
l
a
b
e
l
s
'
)
```

<pre>
D
a
t
e
 
 
c
o
n
t
a
i
n
s
 
 
3
4
3
6
 
 
l
a
b
e
l
s

L
o
c
a
t
i
o
n
 
 
c
o
n
t
a
i
n
s
 
 
4
9
 
 
l
a
b
e
l
s

W
i
n
d
G
u
s
t
D
i
r
 
 
c
o
n
t
a
i
n
s
 
 
1
7
 
 
l
a
b
e
l
s

W
i
n
d
D
i
r
9
a
m
 
 
c
o
n
t
a
i
n
s
 
 
1
7
 
 
l
a
b
e
l
s

W
i
n
d
D
i
r
3
p
m
 
 
c
o
n
t
a
i
n
s
 
 
1
7
 
 
l
a
b
e
l
s

R
a
i
n
T
o
d
a
y
 
 
c
o
n
t
a
i
n
s
 
 
3
 
 
l
a
b
e
l
s

R
a
i
n
T
o
m
o
r
r
o
w
 
 
c
o
n
t
a
i
n
s
 
 
3
 
 
l
a
b
e
l
s

</pre>
날
짜
(
D
a
t
e
)
 
변
수
가
 
전
처
리
(
p
r
e
p
r
o
c
e
s
s
i
n
g
)
 
되
어
야
 
한
다
는
 
것
을
 
알
 
수
 
있
습
니
다
.
 
다
음
 
섹
션
에
서
 
전
처
리
를
 
수
행
할
 
것
입
니
다
.




다
른
 
변
수
들
은
 
비
교
적
 
적
은
 
수
의
 
변
수
들
을
 
포
함
하
고
 
있
습
니
다
.


#
#
#
 
F
e
a
t
u
r
e
 
E
n
g
i
n
e
e
r
i
n
g
 
o
f
 
D
a
t
e
 
V
a
r
i
a
b
l
e



```python
d
f
[
'
D
a
t
e
'
]
.
d
t
y
p
e
s
```

<pre>
d
t
y
p
e
(
'
O
'
)
</pre>
데
이
터
셋
에
서
 
D
a
t
e
 
변
수
의
 
데
이
터
 
타
입
이
 
o
b
j
e
c
t
로
 
표
시
되
어
 
있
습
니
다
.
 
이
 
변
수
를
 
d
a
t
e
t
i
m
e
 
형
식
으
로
 
변
환
할
 
것
입
니
다
.
 
이
렇
게
 
함
으
로
써
 
날
짜
와
 
관
련
된
 
작
업
을
 
더
 
쉽
게
 
수
행
할
 
수
 
있
습
니
다
.



```python
#
 
p
a
r
s
e
 
t
h
e
 
d
a
t
e
s
,
 
c
u
r
r
e
n
t
l
y
 
c
o
d
e
d
 
a
s
 
s
t
r
i
n
g
s
,
 
i
n
t
o
 
d
a
t
e
t
i
m
e
 
f
o
r
m
a
t


d
f
[
'
D
a
t
e
'
]
 
=
 
p
d
.
t
o
_
d
a
t
e
t
i
m
e
(
d
f
[
'
D
a
t
e
'
]
)
```


```python
#
 
e
x
t
r
a
c
t
 
y
e
a
r
 
f
r
o
m
 
d
a
t
e


d
f
[
'
Y
e
a
r
'
]
 
=
 
d
f
[
'
D
a
t
e
'
]
.
d
t
.
y
e
a
r


d
f
[
'
Y
e
a
r
'
]
.
h
e
a
d
(
)
```

<pre>
0
 
 
 
 
2
0
0
8

1
 
 
 
 
2
0
0
8

2
 
 
 
 
2
0
0
8

3
 
 
 
 
2
0
0
8

4
 
 
 
 
2
0
0
8

N
a
m
e
:
 
Y
e
a
r
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
e
x
t
r
a
c
t
 
m
o
n
t
h
 
f
r
o
m
 
d
a
t
e


d
f
[
'
M
o
n
t
h
'
]
 
=
 
d
f
[
'
D
a
t
e
'
]
.
d
t
.
m
o
n
t
h


d
f
[
'
M
o
n
t
h
'
]
.
h
e
a
d
(
)
```

<pre>
0
 
 
 
 
1
2

1
 
 
 
 
1
2

2
 
 
 
 
1
2

3
 
 
 
 
1
2

4
 
 
 
 
1
2

N
a
m
e
:
 
M
o
n
t
h
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
e
x
t
r
a
c
t
 
d
a
y
 
f
r
o
m
 
d
a
t
e


d
f
[
'
D
a
y
'
]
 
=
 
d
f
[
'
D
a
t
e
'
]
.
d
t
.
d
a
y


d
f
[
'
D
a
y
'
]
.
h
e
a
d
(
)
```

<pre>
0
 
 
 
 
1

1
 
 
 
 
2

2
 
 
 
 
3

3
 
 
 
 
4

4
 
 
 
 
5

N
a
m
e
:
 
D
a
y
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
a
g
a
i
n
 
v
i
e
w
 
t
h
e
 
s
u
m
m
a
r
y
 
o
f
 
d
a
t
a
s
e
t


d
f
.
i
n
f
o
(
)
```

<pre>
<
c
l
a
s
s
 
'
p
a
n
d
a
s
.
c
o
r
e
.
f
r
a
m
e
.
D
a
t
a
F
r
a
m
e
'
>

R
a
n
g
e
I
n
d
e
x
:
 
1
4
5
4
6
0
 
e
n
t
r
i
e
s
,
 
0
 
t
o
 
1
4
5
4
5
9

D
a
t
a
 
c
o
l
u
m
n
s
 
(
t
o
t
a
l
 
2
6
 
c
o
l
u
m
n
s
)
:

D
a
t
e
 
 
 
 
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
d
a
t
e
t
i
m
e
6
4
[
n
s
]

L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
1
4
3
9
7
5
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
1
4
4
1
9
9
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
1
4
2
1
9
9
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
8
2
6
7
0
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
7
5
6
2
5
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
 
1
3
5
1
3
4
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
1
3
5
1
9
7
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
 
1
3
4
8
9
4
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
1
4
1
2
3
2
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
1
4
3
6
9
3
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
1
4
2
3
9
8
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
1
4
2
8
0
6
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
1
4
0
9
5
3
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
1
3
0
3
9
5
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
1
3
0
4
3
2
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
8
9
5
7
2
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
8
6
1
0
2
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
1
4
3
6
9
3
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
1
4
1
8
5
1
 
n
o
n
-
n
u
l
l
 
f
l
o
a
t
6
4

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
1
4
2
1
9
9
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

R
a
i
n
T
o
m
o
r
r
o
w
 
 
 
 
 
1
4
2
1
9
3
 
n
o
n
-
n
u
l
l
 
o
b
j
e
c
t

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
i
n
t
6
4

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
i
n
t
6
4

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
1
4
5
4
6
0
 
n
o
n
-
n
u
l
l
 
i
n
t
6
4

d
t
y
p
e
s
:
 
d
a
t
e
t
i
m
e
6
4
[
n
s
]
(
1
)
,
 
f
l
o
a
t
6
4
(
1
6
)
,
 
i
n
t
6
4
(
3
)
,
 
o
b
j
e
c
t
(
6
)

m
e
m
o
r
y
 
u
s
a
g
e
:
 
2
8
.
9
+
 
M
B

</pre>
D
a
t
e
 
변
수
에
서
 
세
 
개
의
 
추
가
적
인
 
열
이
 
생
성
되
었
습
니
다
.
 
이
제
 
원
래
의
 
D
a
t
e
 
변
수
를
 
데
이
터
셋
에
서
 
삭
제
하
도
록
 
하
겠
습
니
다
.



```python
#
 
d
r
o
p
 
t
h
e
 
o
r
i
g
i
n
a
l
 
D
a
t
e
 
v
a
r
i
a
b
l
e


d
f
.
d
r
o
p
(
'
D
a
t
e
'
,
 
a
x
i
s
=
1
,
 
i
n
p
l
a
c
e
 
=
 
T
r
u
e
)
```


```python
#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t
 
a
g
a
i
n


d
f
.
h
e
a
d
(
)
```

<pre>
 
 
L
o
c
a
t
i
o
n
 
 
M
i
n
T
e
m
p
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
W
i
n
d
G
u
s
t
D
i
r
 
 
\

0
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
3
.
4
 
 
 
 
 
2
2
.
9
 
 
 
 
 
 
 
0
.
6
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 

1
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
7
.
4
 
 
 
 
 
2
5
.
1
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
W
N
W
 
 
 

2
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
2
.
9
 
 
 
 
 
2
5
.
7
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
W
S
W
 
 
 

3
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
9
.
2
 
 
 
 
 
2
8
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
N
E
 
 
 

4
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
7
.
5
 
 
 
 
 
3
2
.
3
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 


 
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
W
i
n
d
D
i
r
9
a
m
 
W
i
n
d
D
i
r
3
p
m
 
 
.
.
.
 
 
P
r
e
s
s
u
r
e
3
p
m
 
 
C
l
o
u
d
9
a
m
 
 
C
l
o
u
d
3
p
m
 
 
\

0
 
 
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
W
N
W
 
 
.
.
.
 
 
 
 
 
 
 
1
0
0
7
.
1
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
N
a
N
 
 
 

1
 
 
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
N
N
W
 
 
 
 
 
 
 
 
W
S
W
 
 
.
.
.
 
 
 
 
 
 
 
1
0
0
7
.
8
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 

2
 
 
 
 
 
 
 
 
 
 
 
4
6
.
0
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
W
S
W
 
 
.
.
.
 
 
 
 
 
 
 
1
0
0
8
.
7
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
2
.
0
 
 
 

3
 
 
 
 
 
 
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
 
 
S
E
 
 
 
 
 
 
 
 
 
 
E
 
 
.
.
.
 
 
 
 
 
 
 
1
0
1
2
.
8
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 

4
 
 
 
 
 
 
 
 
 
 
 
4
1
.
0
 
 
 
 
 
 
 
 
E
N
E
 
 
 
 
 
 
 
 
 
N
W
 
 
.
.
.
 
 
 
 
 
 
 
1
0
0
6
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 


 
 
 
T
e
m
p
9
a
m
 
 
T
e
m
p
3
p
m
 
 
R
a
i
n
T
o
d
a
y
 
 
R
a
i
n
T
o
m
o
r
r
o
w
 
 
Y
e
a
r
 
 
M
o
n
t
h
 
 
D
a
y
 
 

0
 
 
 
 
 
1
6
.
9
 
 
 
 
 
2
1
.
8
 
 
 
 
 
 
 
 
 
N
o
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
1
 
 

1
 
 
 
 
 
1
7
.
2
 
 
 
 
 
2
4
.
3
 
 
 
 
 
 
 
 
 
N
o
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
2
 
 

2
 
 
 
 
 
2
1
.
0
 
 
 
 
 
2
3
.
2
 
 
 
 
 
 
 
 
 
N
o
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
3
 
 

3
 
 
 
 
 
1
8
.
1
 
 
 
 
 
2
6
.
5
 
 
 
 
 
 
 
 
 
N
o
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
4
 
 

4
 
 
 
 
 
1
7
.
8
 
 
 
 
 
2
9
.
7
 
 
 
 
 
 
 
 
 
N
o
 
 
 
 
 
 
 
 
 
 
 
 
N
o
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
5
 
 


[
5
 
r
o
w
s
 
x
 
2
5
 
c
o
l
u
m
n
s
]
</pre>
#
#
#
 
E
x
p
l
o
r
e
 
C
a
t
e
g
o
r
i
c
a
l
 
V
a
r
i
a
b
l
e
s






N
o
w
,
 
I
 
w
i
l
l
 
e
x
p
l
o
r
e
 
t
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
o
n
e
 
b
y
 
o
n
e
.
 



```python
#
 
f
i
n
d
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


c
a
t
e
g
o
r
i
c
a
l
 
=
 
[
v
a
r
 
f
o
r
 
v
a
r
 
i
n
 
d
f
.
c
o
l
u
m
n
s
 
i
f
 
d
f
[
v
a
r
]
.
d
t
y
p
e
=
=
'
O
'
]


p
r
i
n
t
(
'
T
h
e
r
e
 
a
r
e
 
{
}
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
\
n
'
.
f
o
r
m
a
t
(
l
e
n
(
c
a
t
e
g
o
r
i
c
a
l
)
)
)


p
r
i
n
t
(
'
T
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
a
r
e
 
:
'
,
 
c
a
t
e
g
o
r
i
c
a
l
)
```

<pre>
T
h
e
r
e
 
a
r
e
 
6
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


T
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
a
r
e
 
:
 
[
'
L
o
c
a
t
i
o
n
'
,
 
'
W
i
n
d
G
u
s
t
D
i
r
'
,
 
'
W
i
n
d
D
i
r
9
a
m
'
,
 
'
W
i
n
d
D
i
r
3
p
m
'
,
 
'
R
a
i
n
T
o
d
a
y
'
,
 
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]

</pre>
해
당
 
데
이
터
셋
에
는
 
총
 
6
개
의
 
범
주
형
 
변
수
가
 
있
습
니
다
.
 
D
a
t
e
 
변
수
는
 
제
거
되
었
습
니
다
.
 
먼
저
 
범
주
형
 
변
수
에
서
 
결
측
값
이
 
있
는
지
 
확
인
해
보
겠
습
니
다
.



```python
#
 
c
h
e
c
k
 
f
o
r
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 


d
f
[
c
a
t
e
g
o
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
1
0
3
2
6

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
1
0
5
6
6

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
4
2
2
8

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
3
2
6
1

R
a
i
n
T
o
m
o
r
r
o
w
 
 
 
 
 
3
2
6
7

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
#
#
#
 
E
x
p
l
o
r
e
 
`
L
o
c
a
t
i
o
n
`
 
v
a
r
i
a
b
l
e



```python
#
 
p
r
i
n
t
 
n
u
m
b
e
r
 
o
f
 
l
a
b
e
l
s
 
i
n
 
L
o
c
a
t
i
o
n
 
v
a
r
i
a
b
l
e


p
r
i
n
t
(
'
L
o
c
a
t
i
o
n
 
c
o
n
t
a
i
n
s
'
,
 
l
e
n
(
d
f
.
L
o
c
a
t
i
o
n
.
u
n
i
q
u
e
(
)
)
,
 
'
l
a
b
e
l
s
'
)
```

<pre>
L
o
c
a
t
i
o
n
 
c
o
n
t
a
i
n
s
 
4
9
 
l
a
b
e
l
s

</pre>

```python
#
 
c
h
e
c
k
 
l
a
b
e
l
s
 
i
n
 
l
o
c
a
t
i
o
n
 
v
a
r
i
a
b
l
e


d
f
.
L
o
c
a
t
i
o
n
.
u
n
i
q
u
e
(
)
```

<pre>
a
r
r
a
y
(
[
'
A
l
b
u
r
y
'
,
 
'
B
a
d
g
e
r
y
s
C
r
e
e
k
'
,
 
'
C
o
b
a
r
'
,
 
'
C
o
f
f
s
H
a
r
b
o
u
r
'
,
 
'
M
o
r
e
e
'
,

 
 
 
 
 
 
 
'
N
e
w
c
a
s
t
l
e
'
,
 
'
N
o
r
a
h
H
e
a
d
'
,
 
'
N
o
r
f
o
l
k
I
s
l
a
n
d
'
,
 
'
P
e
n
r
i
t
h
'
,
 
'
R
i
c
h
m
o
n
d
'
,

 
 
 
 
 
 
 
'
S
y
d
n
e
y
'
,
 
'
S
y
d
n
e
y
A
i
r
p
o
r
t
'
,
 
'
W
a
g
g
a
W
a
g
g
a
'
,
 
'
W
i
l
l
i
a
m
t
o
w
n
'
,

 
 
 
 
 
 
 
'
W
o
l
l
o
n
g
o
n
g
'
,
 
'
C
a
n
b
e
r
r
a
'
,
 
'
T
u
g
g
e
r
a
n
o
n
g
'
,
 
'
M
o
u
n
t
G
i
n
i
n
i
'
,
 
'
B
a
l
l
a
r
a
t
'
,

 
 
 
 
 
 
 
'
B
e
n
d
i
g
o
'
,
 
'
S
a
l
e
'
,
 
'
M
e
l
b
o
u
r
n
e
A
i
r
p
o
r
t
'
,
 
'
M
e
l
b
o
u
r
n
e
'
,
 
'
M
i
l
d
u
r
a
'
,

 
 
 
 
 
 
 
'
N
h
i
l
'
,
 
'
P
o
r
t
l
a
n
d
'
,
 
'
W
a
t
s
o
n
i
a
'
,
 
'
D
a
r
t
m
o
o
r
'
,
 
'
B
r
i
s
b
a
n
e
'
,
 
'
C
a
i
r
n
s
'
,

 
 
 
 
 
 
 
'
G
o
l
d
C
o
a
s
t
'
,
 
'
T
o
w
n
s
v
i
l
l
e
'
,
 
'
A
d
e
l
a
i
d
e
'
,
 
'
M
o
u
n
t
G
a
m
b
i
e
r
'
,
 
'
N
u
r
i
o
o
t
p
a
'
,

 
 
 
 
 
 
 
'
W
o
o
m
e
r
a
'
,
 
'
A
l
b
a
n
y
'
,
 
'
W
i
t
c
h
c
l
i
f
f
e
'
,
 
'
P
e
a
r
c
e
R
A
A
F
'
,
 
'
P
e
r
t
h
A
i
r
p
o
r
t
'
,

 
 
 
 
 
 
 
'
P
e
r
t
h
'
,
 
'
S
a
l
m
o
n
G
u
m
s
'
,
 
'
W
a
l
p
o
l
e
'
,
 
'
H
o
b
a
r
t
'
,
 
'
L
a
u
n
c
e
s
t
o
n
'
,

 
 
 
 
 
 
 
'
A
l
i
c
e
S
p
r
i
n
g
s
'
,
 
'
D
a
r
w
i
n
'
,
 
'
K
a
t
h
e
r
i
n
e
'
,
 
'
U
l
u
r
u
'
]
,
 
d
t
y
p
e
=
o
b
j
e
c
t
)
</pre>

```python
#
 
c
h
e
c
k
 
f
r
e
q
u
e
n
c
y
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
v
a
l
u
e
s
 
i
n
 
L
o
c
a
t
i
o
n
 
v
a
r
i
a
b
l
e


d
f
.
L
o
c
a
t
i
o
n
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
```

<pre>
C
a
n
b
e
r
r
a
 
 
 
 
 
 
 
 
 
 
 
 
3
4
3
6

S
y
d
n
e
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
3
4
4

B
r
i
s
b
a
n
e
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

P
e
r
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

A
d
e
l
a
i
d
e
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

H
o
b
a
r
t
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

M
e
l
b
o
u
r
n
e
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

D
a
r
w
i
n
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
1
9
3

B
a
l
l
a
r
a
t
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

C
a
i
r
n
s
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

T
o
w
n
s
v
i
l
l
e
 
 
 
 
 
 
 
 
 
 
3
0
4
0

M
o
u
n
t
G
i
n
i
n
i
 
 
 
 
 
 
 
 
 
3
0
4
0

M
o
u
n
t
G
a
m
b
i
e
r
 
 
 
 
 
 
 
 
3
0
4
0

A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

B
e
n
d
i
g
o
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

A
l
i
c
e
S
p
r
i
n
g
s
 
 
 
 
 
 
 
 
3
0
4
0

G
o
l
d
C
o
a
s
t
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

L
a
u
n
c
e
s
t
o
n
 
 
 
 
 
 
 
 
 
 
3
0
4
0

A
l
b
a
n
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
4
0

W
o
l
l
o
n
g
o
n
g
 
 
 
 
 
 
 
 
 
 
3
0
4
0

N
e
w
c
a
s
t
l
e
 
 
 
 
 
 
 
 
 
 
 
3
0
3
9

P
e
n
r
i
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
3
9

T
u
g
g
e
r
a
n
o
n
g
 
 
 
 
 
 
 
 
 
3
0
3
9

W
i
t
c
h
c
l
i
f
f
e
 
 
 
 
 
 
 
 
 
3
0
0
9

N
o
r
f
o
l
k
I
s
l
a
n
d
 
 
 
 
 
 
 
3
0
0
9

C
o
f
f
s
H
a
r
b
o
u
r
 
 
 
 
 
 
 
 
3
0
0
9

M
e
l
b
o
u
r
n
e
A
i
r
p
o
r
t
 
 
 
 
3
0
0
9

P
e
r
t
h
A
i
r
p
o
r
t
 
 
 
 
 
 
 
 
3
0
0
9

M
o
r
e
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

S
y
d
n
e
y
A
i
r
p
o
r
t
 
 
 
 
 
 
 
3
0
0
9

W
i
l
l
i
a
m
t
o
w
n
 
 
 
 
 
 
 
 
 
3
0
0
9

P
o
r
t
l
a
n
d
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

P
e
a
r
c
e
R
A
A
F
 
 
 
 
 
 
 
 
 
 
3
0
0
9

W
a
t
s
o
n
i
a
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

N
u
r
i
o
o
t
p
a
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

W
a
g
g
a
W
a
g
g
a
 
 
 
 
 
 
 
 
 
 
3
0
0
9

M
i
l
d
u
r
a
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

R
i
c
h
m
o
n
d
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

C
o
b
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

S
a
l
e
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

D
a
r
t
m
o
o
r
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

W
o
o
m
e
r
a
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
9

B
a
d
g
e
r
y
s
C
r
e
e
k
 
 
 
 
 
 
 
3
0
0
9

W
a
l
p
o
l
e
 
 
 
 
 
 
 
 
 
 
 
 
 
3
0
0
6

N
o
r
a
h
H
e
a
d
 
 
 
 
 
 
 
 
 
 
 
3
0
0
4

S
a
l
m
o
n
G
u
m
s
 
 
 
 
 
 
 
 
 
 
3
0
0
1

U
l
u
r
u
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
1
5
7
8

N
h
i
l
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
1
5
7
8

K
a
t
h
e
r
i
n
e
 
 
 
 
 
 
 
 
 
 
 
1
5
7
8

N
a
m
e
:
 
L
o
c
a
t
i
o
n
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
l
e
t
'
s
 
d
o
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 
o
f
 
L
o
c
a
t
i
o
n
 
v
a
r
i
a
b
l
e

#
 
g
e
t
 
k
-
1
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
s
 
a
f
t
e
r
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 

#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t
 
w
i
t
h
 
h
e
a
d
(
)
 
m
e
t
h
o
d


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
L
o
c
a
t
i
o
n
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
)
.
h
e
a
d
(
)
```

<pre>
 
 
 
A
l
b
a
n
y
 
 
A
l
b
u
r
y
 
 
A
l
i
c
e
S
p
r
i
n
g
s
 
 
B
a
d
g
e
r
y
s
C
r
e
e
k
 
 
B
a
l
l
a
r
a
t
 
 
B
e
n
d
i
g
o
 
 
B
r
i
s
b
a
n
e
 
 
\

0
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 

1
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 

2
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 

3
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 

4
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 


 
 
 
C
a
i
r
n
s
 
 
C
a
n
b
e
r
r
a
 
 
C
o
b
a
r
 
 
.
.
.
 
 
T
o
w
n
s
v
i
l
l
e
 
 
T
u
g
g
e
r
a
n
o
n
g
 
 
U
l
u
r
u
 
 
W
a
g
g
a
W
a
g
g
a
 
 
\

0
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 

1
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 

2
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 

3
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 

4
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 


 
 
 
W
a
l
p
o
l
e
 
 
W
a
t
s
o
n
i
a
 
 
W
i
l
l
i
a
m
t
o
w
n
 
 
W
i
t
c
h
c
l
i
f
f
e
 
 
W
o
l
l
o
n
g
o
n
g
 
 
W
o
o
m
e
r
a
 
 

0
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 

1
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 

2
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 

3
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 

4
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
0
 
 


[
5
 
r
o
w
s
 
x
 
4
8
 
c
o
l
u
m
n
s
]
</pre>
#
#
#
 
E
x
p
l
o
r
e
 
`
W
i
n
d
G
u
s
t
D
i
r
`
 
v
a
r
i
a
b
l
e



```python
#
 
p
r
i
n
t
 
n
u
m
b
e
r
 
o
f
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
G
u
s
t
D
i
r
 
v
a
r
i
a
b
l
e


p
r
i
n
t
(
'
W
i
n
d
G
u
s
t
D
i
r
 
c
o
n
t
a
i
n
s
'
,
 
l
e
n
(
d
f
[
'
W
i
n
d
G
u
s
t
D
i
r
'
]
.
u
n
i
q
u
e
(
)
)
,
 
'
l
a
b
e
l
s
'
)
```

<pre>
W
i
n
d
G
u
s
t
D
i
r
 
c
o
n
t
a
i
n
s
 
1
7
 
l
a
b
e
l
s

</pre>

```python
#
 
c
h
e
c
k
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
G
u
s
t
D
i
r
 
v
a
r
i
a
b
l
e


d
f
[
'
W
i
n
d
G
u
s
t
D
i
r
'
]
.
u
n
i
q
u
e
(
)
```

<pre>
a
r
r
a
y
(
[
'
W
'
,
 
'
W
N
W
'
,
 
'
W
S
W
'
,
 
'
N
E
'
,
 
'
N
N
W
'
,
 
'
N
'
,
 
'
N
N
E
'
,
 
'
S
W
'
,
 
n
a
n
,
 
'
E
N
E
'
,

 
 
 
 
 
 
 
'
S
S
E
'
,
 
'
S
'
,
 
'
N
W
'
,
 
'
S
E
'
,
 
'
E
S
E
'
,
 
'
E
'
,
 
'
S
S
W
'
]
,
 
d
t
y
p
e
=
o
b
j
e
c
t
)
</pre>

```python
#
 
c
h
e
c
k
 
f
r
e
q
u
e
n
c
y
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
v
a
l
u
e
s
 
i
n
 
W
i
n
d
G
u
s
t
D
i
r
 
v
a
r
i
a
b
l
e


d
f
.
W
i
n
d
G
u
s
t
D
i
r
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
```

<pre>
W
 
 
 
 
 
 
9
9
1
5

S
E
 
 
 
 
 
9
4
1
8

N
 
 
 
 
 
 
9
3
1
3

S
S
E
 
 
 
 
9
2
1
6

E
 
 
 
 
 
 
9
1
8
1

S
 
 
 
 
 
 
9
1
6
8

W
S
W
 
 
 
 
9
0
6
9

S
W
 
 
 
 
 
8
9
6
7

S
S
W
 
 
 
 
8
7
3
6

W
N
W
 
 
 
 
8
2
5
2

N
W
 
 
 
 
 
8
1
2
2

E
N
E
 
 
 
 
8
1
0
4

E
S
E
 
 
 
 
7
3
7
2

N
E
 
 
 
 
 
7
1
3
3

N
N
W
 
 
 
 
6
6
2
0

N
N
E
 
 
 
 
6
5
4
8

N
a
m
e
:
 
W
i
n
d
G
u
s
t
D
i
r
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
l
e
t
'
s
 
d
o
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 
o
f
 
W
i
n
d
G
u
s
t
D
i
r
 
v
a
r
i
a
b
l
e

#
 
g
e
t
 
k
-
1
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
s
 
a
f
t
e
r
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 

#
 
a
l
s
o
 
a
d
d
 
a
n
 
a
d
d
i
t
i
o
n
a
l
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
 
t
o
 
i
n
d
i
c
a
t
e
 
t
h
e
r
e
 
w
a
s
 
m
i
s
s
i
n
g
 
d
a
t
a

#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t
 
w
i
t
h
 
h
e
a
d
(
)
 
m
e
t
h
o
d


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
W
i
n
d
G
u
s
t
D
i
r
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
h
e
a
d
(
)
```

<pre>
 
 
 
E
N
E
 
 
E
S
E
 
 
N
 
 
N
E
 
 
N
N
E
 
 
N
N
W
 
 
N
W
 
 
S
 
 
S
E
 
 
S
S
E
 
 
S
S
W
 
 
S
W
 
 
W
 
 
W
N
W
 
 
W
S
W
 
 
N
a
N

0
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

1
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
1
 
 
 
 
0
 
 
 
 
0

2
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
1
 
 
 
 
0

3
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

4
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
</pre>

```python
#
 
s
u
m
 
t
h
e
 
n
u
m
b
e
r
 
o
f
 
1
s
 
p
e
r
 
b
o
o
l
e
a
n
 
v
a
r
i
a
b
l
e
 
o
v
e
r
 
t
h
e
 
r
o
w
s
 
o
f
 
t
h
e
 
d
a
t
a
s
e
t

#
 
i
t
 
w
i
l
l
 
t
e
l
l
 
u
s
 
h
o
w
 
m
a
n
y
 
o
b
s
e
r
v
a
t
i
o
n
s
 
w
e
 
h
a
v
e
 
f
o
r
 
e
a
c
h
 
c
a
t
e
g
o
r
y


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
W
i
n
d
G
u
s
t
D
i
r
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
s
u
m
(
a
x
i
s
=
0
)
```

<pre>
E
N
E
 
 
 
 
 
8
1
0
4

E
S
E
 
 
 
 
 
7
3
7
2

N
 
 
 
 
 
 
 
9
3
1
3

N
E
 
 
 
 
 
 
7
1
3
3

N
N
E
 
 
 
 
 
6
5
4
8

N
N
W
 
 
 
 
 
6
6
2
0

N
W
 
 
 
 
 
 
8
1
2
2

S
 
 
 
 
 
 
 
9
1
6
8

S
E
 
 
 
 
 
 
9
4
1
8

S
S
E
 
 
 
 
 
9
2
1
6

S
S
W
 
 
 
 
 
8
7
3
6

S
W
 
 
 
 
 
 
8
9
6
7

W
 
 
 
 
 
 
 
9
9
1
5

W
N
W
 
 
 
 
 
8
2
5
2

W
S
W
 
 
 
 
 
9
0
6
9

N
a
N
 
 
 
 
1
0
3
2
6

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
W
i
n
d
G
u
s
t
D
i
r
 
변
수
에
는
 
1
0
3
2
6
개
의
 
결
측
치
가
 
있
다
는
 
것
을
 
확
인
할
 
수
 
있
습
니
다
.


#
#
#
 
E
x
p
l
o
r
e
 
`
W
i
n
d
D
i
r
9
a
m
`
 
v
a
r
i
a
b
l
e



```python
#
 
p
r
i
n
t
 
n
u
m
b
e
r
 
o
f
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
D
i
r
9
a
m
 
v
a
r
i
a
b
l
e


p
r
i
n
t
(
'
W
i
n
d
D
i
r
9
a
m
 
c
o
n
t
a
i
n
s
'
,
 
l
e
n
(
d
f
[
'
W
i
n
d
D
i
r
9
a
m
'
]
.
u
n
i
q
u
e
(
)
)
,
 
'
l
a
b
e
l
s
'
)
```

<pre>
W
i
n
d
D
i
r
9
a
m
 
c
o
n
t
a
i
n
s
 
1
7
 
l
a
b
e
l
s

</pre>

```python
#
 
c
h
e
c
k
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
D
i
r
9
a
m
 
v
a
r
i
a
b
l
e


d
f
[
'
W
i
n
d
D
i
r
9
a
m
'
]
.
u
n
i
q
u
e
(
)
```

<pre>
a
r
r
a
y
(
[
'
W
'
,
 
'
N
N
W
'
,
 
'
S
E
'
,
 
'
E
N
E
'
,
 
'
S
W
'
,
 
'
S
S
E
'
,
 
'
S
'
,
 
'
N
E
'
,
 
n
a
n
,
 
'
S
S
W
'
,
 
'
N
'
,

 
 
 
 
 
 
 
'
W
S
W
'
,
 
'
E
S
E
'
,
 
'
E
'
,
 
'
N
W
'
,
 
'
W
N
W
'
,
 
'
N
N
E
'
]
,
 
d
t
y
p
e
=
o
b
j
e
c
t
)
</pre>

```python
#
 
c
h
e
c
k
 
f
r
e
q
u
e
n
c
y
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
v
a
l
u
e
s
 
i
n
 
W
i
n
d
D
i
r
9
a
m
 
v
a
r
i
a
b
l
e


d
f
[
'
W
i
n
d
D
i
r
9
a
m
'
]
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
```

<pre>
N
 
 
 
 
 
 
1
1
7
5
8

S
E
 
 
 
 
 
 
9
2
8
7

E
 
 
 
 
 
 
 
9
1
7
6

S
S
E
 
 
 
 
 
9
1
1
2

N
W
 
 
 
 
 
 
8
7
4
9

S
 
 
 
 
 
 
 
8
6
5
9

W
 
 
 
 
 
 
 
8
4
5
9

S
W
 
 
 
 
 
 
8
4
2
3

N
N
E
 
 
 
 
 
8
1
2
9

N
N
W
 
 
 
 
 
7
9
8
0

E
N
E
 
 
 
 
 
7
8
3
6

N
E
 
 
 
 
 
 
7
6
7
1

E
S
E
 
 
 
 
 
7
6
3
0

S
S
W
 
 
 
 
 
7
5
8
7

W
N
W
 
 
 
 
 
7
4
1
4

W
S
W
 
 
 
 
 
7
0
2
4

N
a
m
e
:
 
W
i
n
d
D
i
r
9
a
m
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
l
e
t
'
s
 
d
o
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 
o
f
 
W
i
n
d
D
i
r
9
a
m
 
v
a
r
i
a
b
l
e

#
 
g
e
t
 
k
-
1
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
s
 
a
f
t
e
r
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 

#
 
a
l
s
o
 
a
d
d
 
a
n
 
a
d
d
i
t
i
o
n
a
l
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
 
t
o
 
i
n
d
i
c
a
t
e
 
t
h
e
r
e
 
w
a
s
 
m
i
s
s
i
n
g
 
d
a
t
a

#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t
 
w
i
t
h
 
h
e
a
d
(
)
 
m
e
t
h
o
d


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
W
i
n
d
D
i
r
9
a
m
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
h
e
a
d
(
)
```

<pre>
 
 
 
E
N
E
 
 
E
S
E
 
 
N
 
 
N
E
 
 
N
N
E
 
 
N
N
W
 
 
N
W
 
 
S
 
 
S
E
 
 
S
S
E
 
 
S
S
W
 
 
S
W
 
 
W
 
 
W
N
W
 
 
W
S
W
 
 
N
a
N

0
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

1
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
1
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

2
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

3
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

4
 
 
 
 
1
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
</pre>

```python
#
 
s
u
m
 
t
h
e
 
n
u
m
b
e
r
 
o
f
 
1
s
 
p
e
r
 
b
o
o
l
e
a
n
 
v
a
r
i
a
b
l
e
 
o
v
e
r
 
t
h
e
 
r
o
w
s
 
o
f
 
t
h
e
 
d
a
t
a
s
e
t

#
 
i
t
 
w
i
l
l
 
t
e
l
l
 
u
s
 
h
o
w
 
m
a
n
y
 
o
b
s
e
r
v
a
t
i
o
n
s
 
w
e
 
h
a
v
e
 
f
o
r
 
e
a
c
h
 
c
a
t
e
g
o
r
y


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
W
i
n
d
D
i
r
9
a
m
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
s
u
m
(
a
x
i
s
=
0
)
```

<pre>
E
N
E
 
 
 
 
 
7
8
3
6

E
S
E
 
 
 
 
 
7
6
3
0

N
 
 
 
 
 
 
1
1
7
5
8

N
E
 
 
 
 
 
 
7
6
7
1

N
N
E
 
 
 
 
 
8
1
2
9

N
N
W
 
 
 
 
 
7
9
8
0

N
W
 
 
 
 
 
 
8
7
4
9

S
 
 
 
 
 
 
 
8
6
5
9

S
E
 
 
 
 
 
 
9
2
8
7

S
S
E
 
 
 
 
 
9
1
1
2

S
S
W
 
 
 
 
 
7
5
8
7

S
W
 
 
 
 
 
 
8
4
2
3

W
 
 
 
 
 
 
 
8
4
5
9

W
N
W
 
 
 
 
 
7
4
1
4

W
S
W
 
 
 
 
 
7
0
2
4

N
a
N
 
 
 
 
1
0
5
6
6

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
W
i
n
d
D
i
r
9
a
m
 
변
수
에
는
 
1
0
5
6
6
개
의
 
결
측
치
가
 
있
다
는
 
것
을
 
확
인
할
 
수
 
있
습
니
다
.


#
#
#
 
E
x
p
l
o
r
e
 
`
W
i
n
d
D
i
r
3
p
m
`
 
v
a
r
i
a
b
l
e



```python
#
 
p
r
i
n
t
 
n
u
m
b
e
r
 
o
f
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
D
i
r
3
p
m
 
v
a
r
i
a
b
l
e


p
r
i
n
t
(
'
W
i
n
d
D
i
r
3
p
m
 
c
o
n
t
a
i
n
s
'
,
 
l
e
n
(
d
f
[
'
W
i
n
d
D
i
r
3
p
m
'
]
.
u
n
i
q
u
e
(
)
)
,
 
'
l
a
b
e
l
s
'
)
```

<pre>
W
i
n
d
D
i
r
3
p
m
 
c
o
n
t
a
i
n
s
 
1
7
 
l
a
b
e
l
s

</pre>

```python
#
 
c
h
e
c
k
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
D
i
r
3
p
m
 
v
a
r
i
a
b
l
e


d
f
[
'
W
i
n
d
D
i
r
3
p
m
'
]
.
u
n
i
q
u
e
(
)
```

<pre>
a
r
r
a
y
(
[
'
W
N
W
'
,
 
'
W
S
W
'
,
 
'
E
'
,
 
'
N
W
'
,
 
'
W
'
,
 
'
S
S
E
'
,
 
'
E
S
E
'
,
 
'
E
N
E
'
,
 
'
N
N
W
'
,
 
'
S
S
W
'
,

 
 
 
 
 
 
 
'
S
W
'
,
 
'
S
E
'
,
 
'
N
'
,
 
'
S
'
,
 
'
N
N
E
'
,
 
n
a
n
,
 
'
N
E
'
]
,
 
d
t
y
p
e
=
o
b
j
e
c
t
)
</pre>

```python
#
 
c
h
e
c
k
 
f
r
e
q
u
e
n
c
y
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
v
a
l
u
e
s
 
i
n
 
W
i
n
d
D
i
r
3
p
m
 
v
a
r
i
a
b
l
e


d
f
[
'
W
i
n
d
D
i
r
3
p
m
'
]
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
```

<pre>
S
E
 
 
 
 
 
1
0
8
3
8

W
 
 
 
 
 
 
1
0
1
1
0

S
 
 
 
 
 
 
 
9
9
2
6

W
S
W
 
 
 
 
 
9
5
1
8

S
S
E
 
 
 
 
 
9
3
9
9

S
W
 
 
 
 
 
 
9
3
5
4

N
 
 
 
 
 
 
 
8
8
9
0

W
N
W
 
 
 
 
 
8
8
7
4

N
W
 
 
 
 
 
 
8
6
1
0

E
S
E
 
 
 
 
 
8
5
0
5

E
 
 
 
 
 
 
 
8
4
7
2

N
E
 
 
 
 
 
 
8
2
6
3

S
S
W
 
 
 
 
 
8
1
5
6

N
N
W
 
 
 
 
 
7
8
7
0

E
N
E
 
 
 
 
 
7
8
5
7

N
N
E
 
 
 
 
 
6
5
9
0

N
a
m
e
:
 
W
i
n
d
D
i
r
3
p
m
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
l
e
t
'
s
 
d
o
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 
o
f
 
W
i
n
d
D
i
r
3
p
m
 
v
a
r
i
a
b
l
e

#
 
g
e
t
 
k
-
1
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
s
 
a
f
t
e
r
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 

#
 
a
l
s
o
 
a
d
d
 
a
n
 
a
d
d
i
t
i
o
n
a
l
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
 
t
o
 
i
n
d
i
c
a
t
e
 
t
h
e
r
e
 
w
a
s
 
m
i
s
s
i
n
g
 
d
a
t
a

#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t
 
w
i
t
h
 
h
e
a
d
(
)
 
m
e
t
h
o
d


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
W
i
n
d
D
i
r
3
p
m
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
h
e
a
d
(
)
```

<pre>
 
 
 
E
N
E
 
 
E
S
E
 
 
N
 
 
N
E
 
 
N
N
E
 
 
N
N
W
 
 
N
W
 
 
S
 
 
S
E
 
 
S
S
E
 
 
S
S
W
 
 
S
W
 
 
W
 
 
W
N
W
 
 
W
S
W
 
 
N
a
N

0
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
1
 
 
 
 
0
 
 
 
 
0

1
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
1
 
 
 
 
0

2
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
1
 
 
 
 
0

3
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0

4
 
 
 
 
0
 
 
 
 
0
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
1
 
 
0
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
</pre>

```python
#
 
s
u
m
 
t
h
e
 
n
u
m
b
e
r
 
o
f
 
1
s
 
p
e
r
 
b
o
o
l
e
a
n
 
v
a
r
i
a
b
l
e
 
o
v
e
r
 
t
h
e
 
r
o
w
s
 
o
f
 
t
h
e
 
d
a
t
a
s
e
t

#
 
i
t
 
w
i
l
l
 
t
e
l
l
 
u
s
 
h
o
w
 
m
a
n
y
 
o
b
s
e
r
v
a
t
i
o
n
s
 
w
e
 
h
a
v
e
 
f
o
r
 
e
a
c
h
 
c
a
t
e
g
o
r
y


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
W
i
n
d
D
i
r
3
p
m
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
s
u
m
(
a
x
i
s
=
0
)
```

<pre>
E
N
E
 
 
 
 
 
7
8
5
7

E
S
E
 
 
 
 
 
8
5
0
5

N
 
 
 
 
 
 
 
8
8
9
0

N
E
 
 
 
 
 
 
8
2
6
3

N
N
E
 
 
 
 
 
6
5
9
0

N
N
W
 
 
 
 
 
7
8
7
0

N
W
 
 
 
 
 
 
8
6
1
0

S
 
 
 
 
 
 
 
9
9
2
6

S
E
 
 
 
 
 
1
0
8
3
8

S
S
E
 
 
 
 
 
9
3
9
9

S
S
W
 
 
 
 
 
8
1
5
6

S
W
 
 
 
 
 
 
9
3
5
4

W
 
 
 
 
 
 
1
0
1
1
0

W
N
W
 
 
 
 
 
8
8
7
4

W
S
W
 
 
 
 
 
9
5
1
8

N
a
N
 
 
 
 
 
4
2
2
8

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
W
i
n
d
D
i
r
3
p
m
 
변
수
에
는
 
4
2
2
8
개
의
 
결
측
치
가
 
있
다
는
 
것
을
 
확
인
할
 
수
 
있
습
니
다
.


#
#
#
 
E
x
p
l
o
r
e
 
`
R
a
i
n
T
o
d
a
y
`
 
v
a
r
i
a
b
l
e



```python
#
 
p
r
i
n
t
 
n
u
m
b
e
r
 
o
f
 
l
a
b
e
l
s
 
i
n
 
R
a
i
n
T
o
d
a
y
 
v
a
r
i
a
b
l
e


p
r
i
n
t
(
'
R
a
i
n
T
o
d
a
y
 
c
o
n
t
a
i
n
s
'
,
 
l
e
n
(
d
f
[
'
R
a
i
n
T
o
d
a
y
'
]
.
u
n
i
q
u
e
(
)
)
,
 
'
l
a
b
e
l
s
'
)
```

<pre>
R
a
i
n
T
o
d
a
y
 
c
o
n
t
a
i
n
s
 
3
 
l
a
b
e
l
s

</pre>

```python
#
 
c
h
e
c
k
 
l
a
b
e
l
s
 
i
n
 
W
i
n
d
G
u
s
t
D
i
r
 
v
a
r
i
a
b
l
e


d
f
[
'
R
a
i
n
T
o
d
a
y
'
]
.
u
n
i
q
u
e
(
)
```

<pre>
a
r
r
a
y
(
[
'
N
o
'
,
 
'
Y
e
s
'
,
 
n
a
n
]
,
 
d
t
y
p
e
=
o
b
j
e
c
t
)
</pre>

```python
#
 
c
h
e
c
k
 
f
r
e
q
u
e
n
c
y
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
v
a
l
u
e
s
 
i
n
 
W
i
n
d
G
u
s
t
D
i
r
 
v
a
r
i
a
b
l
e


d
f
.
R
a
i
n
T
o
d
a
y
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
```

<pre>
N
o
 
 
 
 
 
1
1
0
3
1
9

Y
e
s
 
 
 
 
 
3
1
8
8
0

N
a
m
e
:
 
R
a
i
n
T
o
d
a
y
,
 
d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
l
e
t
'
s
 
d
o
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 
o
f
 
R
a
i
n
T
o
d
a
y
 
v
a
r
i
a
b
l
e

#
 
g
e
t
 
k
-
1
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
s
 
a
f
t
e
r
 
O
n
e
 
H
o
t
 
E
n
c
o
d
i
n
g
 

#
 
a
l
s
o
 
a
d
d
 
a
n
 
a
d
d
i
t
i
o
n
a
l
 
d
u
m
m
y
 
v
a
r
i
a
b
l
e
 
t
o
 
i
n
d
i
c
a
t
e
 
t
h
e
r
e
 
w
a
s
 
m
i
s
s
i
n
g
 
d
a
t
a

#
 
p
r
e
v
i
e
w
 
t
h
e
 
d
a
t
a
s
e
t
 
w
i
t
h
 
h
e
a
d
(
)
 
m
e
t
h
o
d


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
R
a
i
n
T
o
d
a
y
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
h
e
a
d
(
)
```

<pre>
 
 
 
Y
e
s
 
 
N
a
N

0
 
 
 
 
0
 
 
 
 
0

1
 
 
 
 
0
 
 
 
 
0

2
 
 
 
 
0
 
 
 
 
0

3
 
 
 
 
0
 
 
 
 
0

4
 
 
 
 
0
 
 
 
 
0
</pre>

```python
#
 
s
u
m
 
t
h
e
 
n
u
m
b
e
r
 
o
f
 
1
s
 
p
e
r
 
b
o
o
l
e
a
n
 
v
a
r
i
a
b
l
e
 
o
v
e
r
 
t
h
e
 
r
o
w
s
 
o
f
 
t
h
e
 
d
a
t
a
s
e
t

#
 
i
t
 
w
i
l
l
 
t
e
l
l
 
u
s
 
h
o
w
 
m
a
n
y
 
o
b
s
e
r
v
a
t
i
o
n
s
 
w
e
 
h
a
v
e
 
f
o
r
 
e
a
c
h
 
c
a
t
e
g
o
r
y


p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
d
f
.
R
a
i
n
T
o
d
a
y
,
 
d
r
o
p
_
f
i
r
s
t
=
T
r
u
e
,
 
d
u
m
m
y
_
n
a
=
T
r
u
e
)
.
s
u
m
(
a
x
i
s
=
0
)
```

<pre>
Y
e
s
 
 
 
 
3
1
8
8
0

N
a
N
 
 
 
 
 
3
2
6
1

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
R
a
i
n
T
o
d
a
y
 
변
수
에
는
 
3
2
6
1
개
의
 
결
측
치
가
 
있
다
는
 
것
을
 
확
인
할
 
수
 
있
습
니
다
.


#
#
#
 
E
x
p
l
o
r
e
 
N
u
m
e
r
i
c
a
l
 
V
a
r
i
a
b
l
e
s



```python
#
 
f
i
n
d
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


n
u
m
e
r
i
c
a
l
 
=
 
[
v
a
r
 
f
o
r
 
v
a
r
 
i
n
 
d
f
.
c
o
l
u
m
n
s
 
i
f
 
d
f
[
v
a
r
]
.
d
t
y
p
e
!
=
'
O
'
]


p
r
i
n
t
(
'
T
h
e
r
e
 
a
r
e
 
{
}
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
\
n
'
.
f
o
r
m
a
t
(
l
e
n
(
n
u
m
e
r
i
c
a
l
)
)
)


p
r
i
n
t
(
'
T
h
e
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
a
r
e
 
:
'
,
 
n
u
m
e
r
i
c
a
l
)
```

<pre>
T
h
e
r
e
 
a
r
e
 
1
9
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


T
h
e
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
a
r
e
 
:
 
[
'
M
i
n
T
e
m
p
'
,
 
'
M
a
x
T
e
m
p
'
,
 
'
R
a
i
n
f
a
l
l
'
,
 
'
E
v
a
p
o
r
a
t
i
o
n
'
,
 
'
S
u
n
s
h
i
n
e
'
,
 
'
W
i
n
d
G
u
s
t
S
p
e
e
d
'
,
 
'
W
i
n
d
S
p
e
e
d
9
a
m
'
,
 
'
W
i
n
d
S
p
e
e
d
3
p
m
'
,
 
'
H
u
m
i
d
i
t
y
9
a
m
'
,
 
'
H
u
m
i
d
i
t
y
3
p
m
'
,
 
'
P
r
e
s
s
u
r
e
9
a
m
'
,
 
'
P
r
e
s
s
u
r
e
3
p
m
'
,
 
'
C
l
o
u
d
9
a
m
'
,
 
'
C
l
o
u
d
3
p
m
'
,
 
'
T
e
m
p
9
a
m
'
,
 
'
T
e
m
p
3
p
m
'
,
 
'
Y
e
a
r
'
,
 
'
M
o
n
t
h
'
,
 
'
D
a
y
'
]

</pre>

```python
#
 
v
i
e
w
 
t
h
e
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


d
f
[
n
u
m
e
r
i
c
a
l
]
.
h
e
a
d
(
)
```

<pre>
 
 
 
M
i
n
T
e
m
p
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
\

0
 
 
 
 
 
1
3
.
4
 
 
 
 
 
2
2
.
9
 
 
 
 
 
 
 
0
.
6
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 

1
 
 
 
 
 
 
7
.
4
 
 
 
 
 
2
5
.
1
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 

2
 
 
 
 
 
1
2
.
9
 
 
 
 
 
2
5
.
7
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
4
6
.
0
 
 
 

3
 
 
 
 
 
 
9
.
2
 
 
 
 
 
2
8
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
2
4
.
0
 
 
 

4
 
 
 
 
 
1
7
.
5
 
 
 
 
 
3
2
.
3
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
 
 
 
 
4
1
.
0
 
 
 


 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
P
r
e
s
s
u
r
e
9
a
m
 
 
\

0
 
 
 
 
 
 
 
 
 
 
2
0
.
0
 
 
 
 
 
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
 
 
7
1
.
0
 
 
 
 
 
 
 
 
 
2
2
.
0
 
 
 
 
 
 
 
1
0
0
7
.
7
 
 
 

1
 
 
 
 
 
 
 
 
 
 
 
4
.
0
 
 
 
 
 
 
 
 
 
 
2
2
.
0
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
 
2
5
.
0
 
 
 
 
 
 
 
1
0
1
0
.
6
 
 
 

2
 
 
 
 
 
 
 
 
 
 
1
9
.
0
 
 
 
 
 
 
 
 
 
 
2
6
.
0
 
 
 
 
 
 
 
 
 
3
8
.
0
 
 
 
 
 
 
 
 
 
3
0
.
0
 
 
 
 
 
 
 
1
0
0
7
.
6
 
 
 

3
 
 
 
 
 
 
 
 
 
 
1
1
.
0
 
 
 
 
 
 
 
 
 
 
 
9
.
0
 
 
 
 
 
 
 
 
 
4
5
.
0
 
 
 
 
 
 
 
 
 
1
6
.
0
 
 
 
 
 
 
 
1
0
1
7
.
6
 
 
 

4
 
 
 
 
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
 
 
 
2
0
.
0
 
 
 
 
 
 
 
 
 
8
2
.
0
 
 
 
 
 
 
 
 
 
3
3
.
0
 
 
 
 
 
 
 
1
0
1
0
.
8
 
 
 


 
 
 
P
r
e
s
s
u
r
e
3
p
m
 
 
C
l
o
u
d
9
a
m
 
 
C
l
o
u
d
3
p
m
 
 
T
e
m
p
9
a
m
 
 
T
e
m
p
3
p
m
 
 
Y
e
a
r
 
 
M
o
n
t
h
 
 
D
a
y
 
 

0
 
 
 
 
 
 
 
1
0
0
7
.
1
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
1
6
.
9
 
 
 
 
 
2
1
.
8
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
1
 
 

1
 
 
 
 
 
 
 
1
0
0
7
.
8
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
1
7
.
2
 
 
 
 
 
2
4
.
3
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
2
 
 

2
 
 
 
 
 
 
 
1
0
0
8
.
7
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
2
.
0
 
 
 
 
 
2
1
.
0
 
 
 
 
 
2
3
.
2
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
3
 
 

3
 
 
 
 
 
 
 
1
0
1
2
.
8
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
 
 
N
a
N
 
 
 
 
 
1
8
.
1
 
 
 
 
 
2
6
.
5
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
4
 
 

4
 
 
 
 
 
 
 
1
0
0
6
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
1
7
.
8
 
 
 
 
 
2
9
.
7
 
 
2
0
0
8
 
 
 
 
 
1
2
 
 
 
 
5
 
 
</pre>
#
#
#
 
S
u
m
m
a
r
y
 
o
f
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s






-
 
1
6
개
의
 
숫
자
형
 
변
수
가
 
있
습
니
다
.


-
 
이
들
은
 
M
i
n
T
e
m
p
,
 
M
a
x
T
e
m
p
,
 
R
a
i
n
f
a
l
l
,
 
E
v
a
p
o
r
a
t
i
o
n
,
 
S
u
n
s
h
i
n
e
,
 
W
i
n
d
G
u
s
t
S
p
e
e
d
,
 
W
i
n
d
S
p
e
e
d
9
a
m
,
 
W
i
n
d
S
p
e
e
d
3
p
m
,
 
H
u
m
i
d
i
t
y
9
a
m
,
 
H
u
m
i
d
i
t
y
3
p
m
,
 
P
r
e
s
s
u
r
e
9
a
m
,
 
P
r
e
s
s
u
r
e
3
p
m
,
 
C
l
o
u
d
9
a
m
,
 
C
l
o
u
d
3
p
m
,
 
T
e
m
p
9
a
m
 
및
 
T
e
m
p
3
p
m
입
니
다
.


-
 
이
 
모
든
 
숫
자
형
 
변
수
는
 
연
속
형
입
니
다
.


#
#
 
E
x
p
l
o
r
e
 
p
r
o
b
l
e
m
s
 
w
i
t
h
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s






N
o
w
,
 
I
 
w
i
l
l
 
e
x
p
l
o
r
e
 
t
h
e
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
.






#
#
#
 
M
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s



```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


d
f
[
n
u
m
e
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
 
1
4
8
5

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
 
1
2
6
1

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
 
3
2
6
1

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
6
2
7
9
0

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
6
9
8
3
5

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
1
0
2
6
3

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
 
1
7
6
7

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
 
3
0
6
2

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
 
2
6
5
4

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
 
4
5
0
7

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
1
5
0
6
5

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
1
5
0
2
8

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
5
5
8
8
8

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
5
9
3
5
8

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
 
1
7
6
7

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
 
3
6
0
9

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
총
 
1
6
개
의
 
수
치
형
 
특
성
들
이
 
결
측
값
이
 
있
다
는
 
것
을
 
확
인
할
 
수
 
있
습
니
다
.


#
#
#
 
O
u
t
l
i
e
r
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s



```python
#
 
v
i
e
w
 
s
u
m
m
a
r
y
 
s
t
a
t
i
s
t
i
c
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


p
r
i
n
t
(
r
o
u
n
d
(
d
f
[
n
u
m
e
r
i
c
a
l
]
.
d
e
s
c
r
i
b
e
(
)
)
,
2
)
```

<pre>
 
 
 
 
 
 
 
 
M
i
n
T
e
m
p
 
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
\

c
o
u
n
t
 
 
1
4
3
9
7
5
.
0
 
 
1
4
4
1
9
9
.
0
 
 
1
4
2
1
9
9
.
0
 
 
 
 
 
 
8
2
6
7
0
.
0
 
 
 
7
5
6
2
5
.
0
 
 
 
 
 
 
 
1
3
5
1
9
7
.
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
1
2
.
0
 
 
 
 
 
 
2
3
.
0
 
 
 
 
 
 
 
2
.
0
 
 
 
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
 
 
 
 
4
0
.
0
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
6
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
 
 
 
4
.
0
 
 
 
 
 
 
 
4
.
0
 
 
 
 
 
 
 
 
 
 
 
1
4
.
0
 
 
 

m
i
n
 
 
 
 
 
 
 
 
-
8
.
0
 
 
 
 
 
 
-
5
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
 
 
6
.
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
1
8
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
3
.
0
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
 
 
 
 
3
1
.
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
1
2
.
0
 
 
 
 
 
 
2
3
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
 
 
 
 
3
9
.
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
1
7
.
0
 
 
 
 
 
 
2
8
.
0
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
1
1
.
0
 
 
 
 
 
 
 
 
 
 
 
4
8
.
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
3
4
.
0
 
 
 
 
 
 
4
8
.
0
 
 
 
 
 
3
7
1
.
0
 
 
 
 
 
 
 
 
1
4
5
.
0
 
 
 
 
 
 
1
4
.
0
 
 
 
 
 
 
 
 
 
 
1
3
5
.
0
 
 
 


 
 
 
 
 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
P
r
e
s
s
u
r
e
9
a
m
 
 
\

c
o
u
n
t
 
 
 
 
 
 
1
4
3
6
9
3
.
0
 
 
 
 
 
 
1
4
2
3
9
8
.
0
 
 
 
 
 
1
4
2
8
0
6
.
0
 
 
 
 
 
1
4
0
9
5
3
.
0
 
 
 
 
 
1
3
0
3
9
5
.
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
 
 
 
1
4
.
0
 
 
 
 
 
 
 
 
 
 
1
9
.
0
 
 
 
 
 
 
 
 
 
6
9
.
0
 
 
 
 
 
 
 
 
 
5
2
.
0
 
 
 
 
 
 
 
1
0
1
8
.
0
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
 
 
 
 
9
.
0
 
 
 
 
 
 
 
 
 
 
 
9
.
0
 
 
 
 
 
 
 
 
 
1
9
.
0
 
 
 
 
 
 
 
 
 
2
1
.
0
 
 
 
 
 
 
 
 
 
 
7
.
0
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
9
8
0
.
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
 
 
 
1
3
.
0
 
 
 
 
 
 
 
 
 
5
7
.
0
 
 
 
 
 
 
 
 
 
3
7
.
0
 
 
 
 
 
 
 
1
0
1
3
.
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
 
 
 
1
3
.
0
 
 
 
 
 
 
 
 
 
 
1
9
.
0
 
 
 
 
 
 
 
 
 
7
0
.
0
 
 
 
 
 
 
 
 
 
5
2
.
0
 
 
 
 
 
 
 
1
0
1
8
.
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
 
 
 
1
9
.
0
 
 
 
 
 
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
 
 
8
3
.
0
 
 
 
 
 
 
 
 
 
6
6
.
0
 
 
 
 
 
 
 
1
0
2
2
.
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
 
 
1
3
0
.
0
 
 
 
 
 
 
 
 
 
 
8
7
.
0
 
 
 
 
 
 
 
 
1
0
0
.
0
 
 
 
 
 
 
 
 
1
0
0
.
0
 
 
 
 
 
 
 
1
0
4
1
.
0
 
 
 


 
 
 
 
 
 
 
P
r
e
s
s
u
r
e
3
p
m
 
 
C
l
o
u
d
9
a
m
 
 
C
l
o
u
d
3
p
m
 
 
 
T
e
m
p
9
a
m
 
 
 
T
e
m
p
3
p
m
 
 
 
 
 
 
Y
e
a
r
 
 
\

c
o
u
n
t
 
 
 
 
 
1
3
0
4
3
2
.
0
 
 
 
8
9
5
7
2
.
0
 
 
 
8
6
1
0
2
.
0
 
 
1
4
3
6
9
3
.
0
 
 
1
4
1
8
5
1
.
0
 
 
1
4
5
4
6
0
.
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
1
0
1
5
.
0
 
 
 
 
 
 
 
4
.
0
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
1
7
.
0
 
 
 
 
 
 
2
2
.
0
 
 
 
 
2
0
1
3
.
0
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
3
.
0
 
 
 
 
 
 
 
3
.
0
 
 
 
 
 
 
 
6
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
3
.
0
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
 
9
7
7
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
-
7
.
0
 
 
 
 
 
 
-
5
.
0
 
 
 
 
2
0
0
7
.
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
1
0
1
0
.
0
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
2
.
0
 
 
 
 
 
 
1
2
.
0
 
 
 
 
 
 
1
7
.
0
 
 
 
 
2
0
1
1
.
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
1
0
1
5
.
0
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
1
7
.
0
 
 
 
 
 
 
2
1
.
0
 
 
 
 
2
0
1
3
.
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
1
0
2
0
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
2
2
.
0
 
 
 
 
 
 
2
6
.
0
 
 
 
 
2
0
1
5
.
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
0
4
0
.
0
 
 
 
 
 
 
 
9
.
0
 
 
 
 
 
 
 
9
.
0
 
 
 
 
 
 
4
0
.
0
 
 
 
 
 
 
4
7
.
0
 
 
 
 
2
0
1
7
.
0
 
 
 


 
 
 
 
 
 
 
 
 
 
M
o
n
t
h
 
 
 
 
 
 
 
D
a
y
 
 

c
o
u
n
t
 
 
1
4
5
4
6
0
.
0
 
 
1
4
5
4
6
0
.
0
 
 

m
e
a
n
 
 
 
 
 
 
 
 
6
.
0
 
 
 
 
 
 
1
6
.
0
 
 

s
t
d
 
 
 
 
 
 
 
 
 
3
.
0
 
 
 
 
 
 
 
9
.
0
 
 

m
i
n
 
 
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
1
.
0
 
 

2
5
%
 
 
 
 
 
 
 
 
 
3
.
0
 
 
 
 
 
 
 
8
.
0
 
 

5
0
%
 
 
 
 
 
 
 
 
 
6
.
0
 
 
 
 
 
 
1
6
.
0
 
 

7
5
%
 
 
 
 
 
 
 
 
 
9
.
0
 
 
 
 
 
 
2
3
.
0
 
 

m
a
x
 
 
 
 
 
 
 
 
1
2
.
0
 
 
 
 
 
 
3
1
.
0
 
 
 
2

</pre>
`
R
a
i
n
f
a
l
l
`
,
 
`
E
v
a
p
o
r
a
t
i
o
n
`
,
 
`
W
i
n
d
S
p
e
e
d
9
a
m
`
 
,
 
`
W
i
n
d
S
p
e
e
d
3
p
m
`
 
은
 
기
본
적
으
로
 
이
상
치
를
 
포
함
하
고
 
있
는
것
으
로
 
보
입
니
다
.




이
를
 
시
각
화
하
기
 
위
해
 
b
o
x
p
l
o
t
을
 
이
용
하
도
록
 
해
봅
니
다
.



```python
#
 
d
r
a
w
 
b
o
x
p
l
o
t
s
 
t
o
 
v
i
s
u
a
l
i
z
e
 
o
u
t
l
i
e
r
s


p
l
t
.
f
i
g
u
r
e
(
f
i
g
s
i
z
e
=
(
1
5
,
1
0
)
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
1
)

f
i
g
 
=
 
d
f
.
b
o
x
p
l
o
t
(
c
o
l
u
m
n
=
'
R
a
i
n
f
a
l
l
'
)

f
i
g
.
s
e
t
_
t
i
t
l
e
(
'
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
R
a
i
n
f
a
l
l
'
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
2
)

f
i
g
 
=
 
d
f
.
b
o
x
p
l
o
t
(
c
o
l
u
m
n
=
'
E
v
a
p
o
r
a
t
i
o
n
'
)

f
i
g
.
s
e
t
_
t
i
t
l
e
(
'
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
E
v
a
p
o
r
a
t
i
o
n
'
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
3
)

f
i
g
 
=
 
d
f
.
b
o
x
p
l
o
t
(
c
o
l
u
m
n
=
'
W
i
n
d
S
p
e
e
d
9
a
m
'
)

f
i
g
.
s
e
t
_
t
i
t
l
e
(
'
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
W
i
n
d
S
p
e
e
d
9
a
m
'
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
4
)

f
i
g
 
=
 
d
f
.
b
o
x
p
l
o
t
(
c
o
l
u
m
n
=
'
W
i
n
d
S
p
e
e
d
3
p
m
'
)

f
i
g
.
s
e
t
_
t
i
t
l
e
(
'
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
W
i
n
d
S
p
e
e
d
3
p
m
'
)
```

<pre>
T
e
x
t
(
0
,
 
0
.
5
,
 
'
W
i
n
d
S
p
e
e
d
3
p
m
'
)
</pre>
<pre>
<
F
i
g
u
r
e
 
s
i
z
e
 
1
0
8
0
x
7
2
0
 
w
i
t
h
 
4
 
A
x
e
s
>
</pre>
위
 
그
래
프
를
 
통
해
 
육
안
으
로
 
보
일
 
정
도
의
 
이
상
치
가
 
있
는
 
것
이
 
확
인
되
었
습
니
다
.


#
#
#
 
C
h
e
c
k
 
t
h
e
 
d
i
s
t
r
i
b
u
t
i
o
n
 
o
f
 
v
a
r
i
a
b
l
e
s






이
제
 
히
스
토
그
램
을
 
그
려
서
 
분
포
를
 
확
인
하
고
 
정
규
 
분
포
인
지
 
왜
도
(
s
k
e
w
n
e
s
s
)
가
 
있
는
지
 
찾
아
보
겠
습
니
다
.
 
변
수
가
 
정
규
 
분
포
를
 
따
른
다
면
,
 
극
단
치
 
분
석
(
E
x
t
r
e
m
e
 
V
a
l
u
e
 
A
n
a
l
y
s
i
s
)
을
 
수
행
하
겠
습
니
다
.
 
그
러
나
 
만
약
 
왜
도
가
 
있
다
면
,
 
I
Q
R
(
I
n
t
e
r
q
u
a
n
t
i
l
e
 
r
a
n
g
e
)
을
 
찾
아
보
겠
습
니
다
.



```python
#
 
p
l
o
t
 
h
i
s
t
o
g
r
a
m
 
t
o
 
c
h
e
c
k
 
d
i
s
t
r
i
b
u
t
i
o
n


p
l
t
.
f
i
g
u
r
e
(
f
i
g
s
i
z
e
=
(
1
5
,
1
0
)
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
1
)

f
i
g
 
=
 
d
f
.
R
a
i
n
f
a
l
l
.
h
i
s
t
(
b
i
n
s
=
1
0
)

f
i
g
.
s
e
t
_
x
l
a
b
e
l
(
'
R
a
i
n
f
a
l
l
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
R
a
i
n
T
o
m
o
r
r
o
w
'
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
2
)

f
i
g
 
=
 
d
f
.
E
v
a
p
o
r
a
t
i
o
n
.
h
i
s
t
(
b
i
n
s
=
1
0
)

f
i
g
.
s
e
t
_
x
l
a
b
e
l
(
'
E
v
a
p
o
r
a
t
i
o
n
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
R
a
i
n
T
o
m
o
r
r
o
w
'
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
3
)

f
i
g
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
9
a
m
.
h
i
s
t
(
b
i
n
s
=
1
0
)

f
i
g
.
s
e
t
_
x
l
a
b
e
l
(
'
W
i
n
d
S
p
e
e
d
9
a
m
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
R
a
i
n
T
o
m
o
r
r
o
w
'
)



p
l
t
.
s
u
b
p
l
o
t
(
2
,
 
2
,
 
4
)

f
i
g
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
3
p
m
.
h
i
s
t
(
b
i
n
s
=
1
0
)

f
i
g
.
s
e
t
_
x
l
a
b
e
l
(
'
W
i
n
d
S
p
e
e
d
3
p
m
'
)

f
i
g
.
s
e
t
_
y
l
a
b
e
l
(
'
R
a
i
n
T
o
m
o
r
r
o
w
'
)
```

<pre>
T
e
x
t
(
0
,
 
0
.
5
,
 
'
R
a
i
n
T
o
m
o
r
r
o
w
'
)
</pre>
<pre>
<
F
i
g
u
r
e
 
s
i
z
e
 
1
0
8
0
x
7
2
0
 
w
i
t
h
 
4
 
A
x
e
s
>
</pre>
모
든
 
네
 
개
의
 
변
수
가
 
비
대
칭
이
라
는
 
것
을
 
알
 
수
 
있
습
니
다
.
 
따
라
서
,
 
이
상
치
를
 
찾
기
 
위
해
 
사
분
위
범
위
를
 
사
용
할
 
것
입
니
다
.











```python
#
 
f
i
n
d
 
o
u
t
l
i
e
r
s
 
f
o
r
 
R
a
i
n
f
a
l
l
 
v
a
r
i
a
b
l
e


I
Q
R
 
=
 
d
f
.
R
a
i
n
f
a
l
l
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
-
 
d
f
.
R
a
i
n
f
a
l
l
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)

L
o
w
e
r
_
f
e
n
c
e
 
=
 
d
f
.
R
a
i
n
f
a
l
l
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)
 
-
 
(
I
Q
R
 
*
 
3
)

U
p
p
e
r
_
f
e
n
c
e
 
=
 
d
f
.
R
a
i
n
f
a
l
l
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
+
 
(
I
Q
R
 
*
 
3
)

p
r
i
n
t
(
'
R
a
i
n
f
a
l
l
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
{
l
o
w
e
r
b
o
u
n
d
a
r
y
}
 
o
r
 
>
 
{
u
p
p
e
r
b
o
u
n
d
a
r
y
}
'
.
f
o
r
m
a
t
(
l
o
w
e
r
b
o
u
n
d
a
r
y
=
L
o
w
e
r
_
f
e
n
c
e
,
 
u
p
p
e
r
b
o
u
n
d
a
r
y
=
U
p
p
e
r
_
f
e
n
c
e
)
)

```

<pre>
R
a
i
n
f
a
l
l
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
-
2
.
4
0
0
0
0
0
0
0
0
0
0
0
0
0
0
4
 
o
r
 
>
 
3
.
2

</pre>
R
a
i
n
f
a
l
l
 
변
수
에
서
 
최
소
값
은
 
0
.
0
이
고
,
 
최
대
값
은
 
3
7
1
.
0
입
니
다
.
 
따
라
서
,
 
이
상
치
는
 
3
.
2
보
다
 
큰
 
값
입
니
다
.



```python
#
 
f
i
n
d
 
o
u
t
l
i
e
r
s
 
f
o
r
 
E
v
a
p
o
r
a
t
i
o
n
 
v
a
r
i
a
b
l
e


I
Q
R
 
=
 
d
f
.
E
v
a
p
o
r
a
t
i
o
n
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
-
 
d
f
.
E
v
a
p
o
r
a
t
i
o
n
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)

L
o
w
e
r
_
f
e
n
c
e
 
=
 
d
f
.
E
v
a
p
o
r
a
t
i
o
n
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)
 
-
 
(
I
Q
R
 
*
 
3
)

U
p
p
e
r
_
f
e
n
c
e
 
=
 
d
f
.
E
v
a
p
o
r
a
t
i
o
n
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
+
 
(
I
Q
R
 
*
 
3
)

p
r
i
n
t
(
'
E
v
a
p
o
r
a
t
i
o
n
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
{
l
o
w
e
r
b
o
u
n
d
a
r
y
}
 
o
r
 
>
 
{
u
p
p
e
r
b
o
u
n
d
a
r
y
}
'
.
f
o
r
m
a
t
(
l
o
w
e
r
b
o
u
n
d
a
r
y
=
L
o
w
e
r
_
f
e
n
c
e
,
 
u
p
p
e
r
b
o
u
n
d
a
r
y
=
U
p
p
e
r
_
f
e
n
c
e
)
)

```

<pre>
E
v
a
p
o
r
a
t
i
o
n
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
-
1
1
.
8
0
0
0
0
0
0
0
0
0
0
0
0
0
2
 
o
r
 
>
 
2
1
.
8
0
0
0
0
0
0
0
0
0
0
0
0
0
4

</pre>
E
v
a
p
o
r
a
t
i
o
n
 
변
수
에
서
 
최
소
값
과
 
최
대
값
은
 
각
각
 
0
.
0
과
 
1
4
5
.
0
입
니
다
.
 
이
상
치
는
 
2
1
.
8
보
다
 
큰
 
값
입
니
다
.



```python
#
 
f
i
n
d
 
o
u
t
l
i
e
r
s
 
f
o
r
 
W
i
n
d
S
p
e
e
d
9
a
m
 
v
a
r
i
a
b
l
e


I
Q
R
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
9
a
m
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
-
 
d
f
.
W
i
n
d
S
p
e
e
d
9
a
m
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)

L
o
w
e
r
_
f
e
n
c
e
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
9
a
m
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)
 
-
 
(
I
Q
R
 
*
 
3
)

U
p
p
e
r
_
f
e
n
c
e
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
9
a
m
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
+
 
(
I
Q
R
 
*
 
3
)

p
r
i
n
t
(
'
W
i
n
d
S
p
e
e
d
9
a
m
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
{
l
o
w
e
r
b
o
u
n
d
a
r
y
}
 
o
r
 
>
 
{
u
p
p
e
r
b
o
u
n
d
a
r
y
}
'
.
f
o
r
m
a
t
(
l
o
w
e
r
b
o
u
n
d
a
r
y
=
L
o
w
e
r
_
f
e
n
c
e
,
 
u
p
p
e
r
b
o
u
n
d
a
r
y
=
U
p
p
e
r
_
f
e
n
c
e
)
)

```

<pre>
W
i
n
d
S
p
e
e
d
9
a
m
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
-
2
9
.
0
 
o
r
 
>
 
5
5
.
0

</pre>
W
i
n
d
S
p
e
e
d
9
a
m
 
변
수
에
서
 
최
소
값
과
 
최
대
값
은
 
각
각
 
0
.
0
과
 
1
3
0
.
0
입
니
다
.
 
따
라
서
,
 
이
상
치
는
 
5
5
.
0
보
다
 
큰
 
값
입
니
다
.



```python
#
 
f
i
n
d
 
o
u
t
l
i
e
r
s
 
f
o
r
 
W
i
n
d
S
p
e
e
d
3
p
m
 
v
a
r
i
a
b
l
e


I
Q
R
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
3
p
m
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
-
 
d
f
.
W
i
n
d
S
p
e
e
d
3
p
m
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)

L
o
w
e
r
_
f
e
n
c
e
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
3
p
m
.
q
u
a
n
t
i
l
e
(
0
.
2
5
)
 
-
 
(
I
Q
R
 
*
 
3
)

U
p
p
e
r
_
f
e
n
c
e
 
=
 
d
f
.
W
i
n
d
S
p
e
e
d
3
p
m
.
q
u
a
n
t
i
l
e
(
0
.
7
5
)
 
+
 
(
I
Q
R
 
*
 
3
)

p
r
i
n
t
(
'
W
i
n
d
S
p
e
e
d
3
p
m
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
{
l
o
w
e
r
b
o
u
n
d
a
r
y
}
 
o
r
 
>
 
{
u
p
p
e
r
b
o
u
n
d
a
r
y
}
'
.
f
o
r
m
a
t
(
l
o
w
e
r
b
o
u
n
d
a
r
y
=
L
o
w
e
r
_
f
e
n
c
e
,
 
u
p
p
e
r
b
o
u
n
d
a
r
y
=
U
p
p
e
r
_
f
e
n
c
e
)
)

```

<pre>
W
i
n
d
S
p
e
e
d
3
p
m
 
o
u
t
l
i
e
r
s
 
a
r
e
 
v
a
l
u
e
s
 
<
 
-
2
0
.
0
 
o
r
 
>
 
5
7
.
0

</pre>
W
i
n
d
S
p
e
e
d
3
p
m
 
변
수
의
 
최
소
값
과
 
최
대
값
은
 
각
각
 
0
.
0
과
 
8
7
.
0
입
니
다
.
 
이
상
치
는
 
값
이
 
5
7
.
0
보
다
 
큰
 
경
우
입
니
다
.


#
 
*
*
8
.
 
D
e
c
l
a
r
e
 
f
e
a
t
u
r
e
 
v
e
c
t
o
r
 
a
n
d
 
t
a
r
g
e
t
 
v
a
r
i
a
b
l
e
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
8
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
X
 
=
 
d
f
.
d
r
o
p
(
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
,
 
a
x
i
s
=
1
)


y
 
=
 
d
f
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
```

#
 
*
*
9
.
 
S
p
l
i
t
 
d
a
t
a
 
i
n
t
o
 
s
e
p
a
r
a
t
e
 
t
r
a
i
n
i
n
g
 
a
n
d
 
t
e
s
t
 
s
e
t
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
9
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
#
 
s
p
l
i
t
 
X
 
a
n
d
 
y
 
i
n
t
o
 
t
r
a
i
n
i
n
g
 
a
n
d
 
t
e
s
t
i
n
g
 
s
e
t
s


f
r
o
m
 
s
k
l
e
a
r
n
.
m
o
d
e
l
_
s
e
l
e
c
t
i
o
n
 
i
m
p
o
r
t
 
t
r
a
i
n
_
t
e
s
t
_
s
p
l
i
t


X
_
t
r
a
i
n
,
 
X
_
t
e
s
t
,
 
y
_
t
r
a
i
n
,
 
y
_
t
e
s
t
 
=
 
t
r
a
i
n
_
t
e
s
t
_
s
p
l
i
t
(
X
,
 
y
,
 
t
e
s
t
_
s
i
z
e
 
=
 
0
.
2
,
 
r
a
n
d
o
m
_
s
t
a
t
e
 
=
 
0
)

```


```python
#
 
c
h
e
c
k
 
t
h
e
 
s
h
a
p
e
 
o
f
 
X
_
t
r
a
i
n
 
a
n
d
 
X
_
t
e
s
t


X
_
t
r
a
i
n
.
s
h
a
p
e
,
 
X
_
t
e
s
t
.
s
h
a
p
e
```

<pre>
(
(
1
1
6
3
6
8
,
 
2
4
)
,
 
(
2
9
0
9
2
,
 
2
4
)
)
</pre>
#
 
*
*
1
0
.
 
F
e
a
t
u
r
e
 
E
n
g
i
n
e
e
r
i
n
g
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
0
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






특
성
 
엔
지
니
어
링
은
 
원
시
 
데
이
터
를
 
유
용
한
 
특
성
으
로
 
변
환
하
여
 
모
델
을
 
이
해
하
고
 
예
측
 
능
력
을
 
높
이
는
 
과
정
입
니
다
.
 
다
른
 
유
형
의
 
변
수
에
 
대
해
 
특
성
 
엔
지
니
어
링
을
 
수
행
할
 
것
입
니
다
.




먼
저
,
 
범
주
형
 
및
 
수
치
 
변
수
를
 
다
시
 
별
도
로
 
표
시
하
겠
습
니
다
.



```python
#
 
c
h
e
c
k
 
d
a
t
a
 
t
y
p
e
s
 
i
n
 
X
_
t
r
a
i
n


X
_
t
r
a
i
n
.
d
t
y
p
e
s
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
 
o
b
j
e
c
t

M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
f
l
o
a
t
6
4

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
 
 
o
b
j
e
c
t

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
f
l
o
a
t
6
4

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
 
 
o
b
j
e
c
t

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
 
o
b
j
e
c
t

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
f
l
o
a
t
6
4

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
f
l
o
a
t
6
4

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
f
l
o
a
t
6
4

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
f
l
o
a
t
6
4

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
f
l
o
a
t
6
4

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
f
l
o
a
t
6
4

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
f
l
o
a
t
6
4

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
 
o
b
j
e
c
t

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
6
4

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
6
4

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
6
4

d
t
y
p
e
:
 
o
b
j
e
c
t
</pre>

```python
#
 
d
i
s
p
l
a
y
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


c
a
t
e
g
o
r
i
c
a
l
 
=
 
[
c
o
l
 
f
o
r
 
c
o
l
 
i
n
 
X
_
t
r
a
i
n
.
c
o
l
u
m
n
s
 
i
f
 
X
_
t
r
a
i
n
[
c
o
l
]
.
d
t
y
p
e
s
 
=
=
 
'
O
'
]


c
a
t
e
g
o
r
i
c
a
l
```

<pre>
[
'
L
o
c
a
t
i
o
n
'
,
 
'
W
i
n
d
G
u
s
t
D
i
r
'
,
 
'
W
i
n
d
D
i
r
9
a
m
'
,
 
'
W
i
n
d
D
i
r
3
p
m
'
,
 
'
R
a
i
n
T
o
d
a
y
'
]
</pre>

```python
#
 
d
i
s
p
l
a
y
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s


n
u
m
e
r
i
c
a
l
 
=
 
[
c
o
l
 
f
o
r
 
c
o
l
 
i
n
 
X
_
t
r
a
i
n
.
c
o
l
u
m
n
s
 
i
f
 
X
_
t
r
a
i
n
[
c
o
l
]
.
d
t
y
p
e
s
 
!
=
 
'
O
'
]


n
u
m
e
r
i
c
a
l
```

<pre>
[
'
M
i
n
T
e
m
p
'
,

 
'
M
a
x
T
e
m
p
'
,

 
'
R
a
i
n
f
a
l
l
'
,

 
'
E
v
a
p
o
r
a
t
i
o
n
'
,

 
'
S
u
n
s
h
i
n
e
'
,

 
'
W
i
n
d
G
u
s
t
S
p
e
e
d
'
,

 
'
W
i
n
d
S
p
e
e
d
9
a
m
'
,

 
'
W
i
n
d
S
p
e
e
d
3
p
m
'
,

 
'
H
u
m
i
d
i
t
y
9
a
m
'
,

 
'
H
u
m
i
d
i
t
y
3
p
m
'
,

 
'
P
r
e
s
s
u
r
e
9
a
m
'
,

 
'
P
r
e
s
s
u
r
e
3
p
m
'
,

 
'
C
l
o
u
d
9
a
m
'
,

 
'
C
l
o
u
d
3
p
m
'
,

 
'
T
e
m
p
9
a
m
'
,

 
'
T
e
m
p
3
p
m
'
,

 
'
Y
e
a
r
'
,

 
'
M
o
n
t
h
'
,

 
'
D
a
y
'
]
</pre>
#
#
#
 
E
n
g
i
n
e
e
r
i
n
g
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s







```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
X
_
t
r
a
i
n


X
_
t
r
a
i
n
[
n
u
m
e
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
 
1
1
8
3

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
 
1
0
1
9

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
 
2
6
1
7

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
5
0
3
5
5

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
5
5
8
9
9

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
 
8
2
1
8

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
 
1
4
0
9

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
 
2
4
5
6

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
 
2
1
4
7

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
 
3
5
9
8

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
1
2
0
9
1

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
1
2
0
6
4

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
4
4
7
9
6

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
4
7
5
5
7

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
 
1
4
1
5

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
 
2
8
6
5

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
X
_
t
e
s
t


X
_
t
e
s
t
[
n
u
m
e
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
 
 
3
0
2

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
 
 
2
4
2

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
 
 
6
4
4

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
1
2
4
3
5

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
1
3
9
3
6

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
 
2
0
4
5

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
 
 
3
5
8

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
 
 
6
0
6

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
 
 
5
0
7

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
 
 
9
0
9

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
 
2
9
7
4

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
 
2
9
6
4

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
1
1
0
9
2

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
1
1
8
0
1

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
 
 
3
5
2

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
 
 
7
4
4

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
p
r
i
n
t
 
p
e
r
c
e
n
t
a
g
e
 
o
f
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
t
h
e
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
t
r
a
i
n
i
n
g
 
s
e
t


f
o
r
 
c
o
l
 
i
n
 
n
u
m
e
r
i
c
a
l
:

 
 
 
 
i
f
 
X
_
t
r
a
i
n
[
c
o
l
]
.
i
s
n
u
l
l
(
)
.
m
e
a
n
(
)
>
0
:

 
 
 
 
 
 
 
 
p
r
i
n
t
(
c
o
l
,
 
r
o
u
n
d
(
X
_
t
r
a
i
n
[
c
o
l
]
.
i
s
n
u
l
l
(
)
.
m
e
a
n
(
)
,
4
)
)
```

<pre>
M
i
n
T
e
m
p
 
0
.
0
1
0
2

M
a
x
T
e
m
p
 
0
.
0
0
8
8

R
a
i
n
f
a
l
l
 
0
.
0
2
2
5

E
v
a
p
o
r
a
t
i
o
n
 
0
.
4
3
2
7

S
u
n
s
h
i
n
e
 
0
.
4
8
0
4

W
i
n
d
G
u
s
t
S
p
e
e
d
 
0
.
0
7
0
6

W
i
n
d
S
p
e
e
d
9
a
m
 
0
.
0
1
2
1

W
i
n
d
S
p
e
e
d
3
p
m
 
0
.
0
2
1
1

H
u
m
i
d
i
t
y
9
a
m
 
0
.
0
1
8
5

H
u
m
i
d
i
t
y
3
p
m
 
0
.
0
3
0
9

P
r
e
s
s
u
r
e
9
a
m
 
0
.
1
0
3
9

P
r
e
s
s
u
r
e
3
p
m
 
0
.
1
0
3
7

C
l
o
u
d
9
a
m
 
0
.
3
8
5

C
l
o
u
d
3
p
m
 
0
.
4
0
8
7

T
e
m
p
9
a
m
 
0
.
0
1
2
2

T
e
m
p
3
p
m
 
0
.
0
2
4
6

</pre>
#
#
#
 
A
s
s
u
m
p
t
i
o
n






데
이
터
가
 
완
전
히
 
무
작
위
로
 
누
락
되
었
다
고
 
가
정
합
니
다
 
(
M
C
A
R
)
.
 
누
락
된
 
값
 
채
우
기
에
는
 
두
 
가
지
 
방
법
이
 
있
습
니
다
.
 
평
균
 
또
는
 
중
앙
값
 
채
우
기
와
 
무
작
위
 
샘
플
 
채
우
기
입
니
다
.
 
데
이
터
 
세
트
에
 
이
상
치
가
 
있
을
 
때
 
중
앙
값
 
채
우
기
를
 
사
용
해
야
 
합
니
다
.
 
이
에
 
따
라
 
중
앙
값
 
채
우
기
를
 
사
용
할
 
것
입
니
다
.
 
중
앙
값
 
채
우
기
는
 
이
상
치
에
 
강
건
합
니
다
.




누
락
된
 
값
을
 
데
이
터
의
 
적
절
한
 
통
계
 
측
정
치
인
 
중
앙
값
으
로
 
대
체
할
 
것
입
니
다
.
 
대
체
는
 
학
습
 
세
트
에
서
 
수
행
되
어
야
 
하
며
,
 
그
 
후
에
 
테
스
트
 
세
트
로
 
전
파
됩
니
다
.
 
즉
,
 
학
습
 
및
 
테
스
트
 
세
트
 
모
두
에
서
 
누
락
된
 
값
을
 
채
우
기
 
위
해
 
사
용
할
 
통
계
 
측
정
치
는
 
학
습
 
세
트
에
서
만
 
추
출
해
야
 
합
니
다
.
 
이
는
 
과
적
합
을
 
방
지
하
기
 
위
함
입
니
다
.



```python
#
 
i
m
p
u
t
e
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
X
_
t
r
a
i
n
 
a
n
d
 
X
_
t
e
s
t
 
w
i
t
h
 
r
e
s
p
e
c
t
i
v
e
 
c
o
l
u
m
n
 
m
e
d
i
a
n
 
i
n
 
X
_
t
r
a
i
n


f
o
r
 
d
f
1
 
i
n
 
[
X
_
t
r
a
i
n
,
 
X
_
t
e
s
t
]
:

 
 
 
 
f
o
r
 
c
o
l
 
i
n
 
n
u
m
e
r
i
c
a
l
:

 
 
 
 
 
 
 
 
c
o
l
_
m
e
d
i
a
n
=
X
_
t
r
a
i
n
[
c
o
l
]
.
m
e
d
i
a
n
(
)

 
 
 
 
 
 
 
 
d
f
1
[
c
o
l
]
.
f
i
l
l
n
a
(
c
o
l
_
m
e
d
i
a
n
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)
 
 
 
 
 
 
 
 
 
 
 

 
 
 
 
 
 
```


```python
#
 
c
h
e
c
k
 
a
g
a
i
n
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
X
_
t
r
a
i
n


X
_
t
r
a
i
n
[
n
u
m
e
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
0

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
0

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
0

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
0

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
0

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
0

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
0

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
0

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
0

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
0

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
0

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
X
_
t
e
s
t


X
_
t
e
s
t
[
n
u
m
e
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
0

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
0

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
0

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
0

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
0

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
0

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
0

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
0

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
0

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
0

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
0

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
이
제
 
수
치
형
 
변
수
들
에
는
 
결
측
치
가
 
없
도
록
 
만
들
었
습
니
다
.


#
#
#
 
E
n
g
i
n
e
e
r
i
n
g
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s



```python
#
 
p
r
i
n
t
 
p
e
r
c
e
n
t
a
g
e
 
o
f
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
t
h
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
t
r
a
i
n
i
n
g
 
s
e
t


X
_
t
r
a
i
n
[
c
a
t
e
g
o
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
m
e
a
n
(
)
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
0
.
0
7
1
0
6
8

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
0
.
0
7
2
5
9
7

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
0
.
0
2
8
9
5
1

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
0
.
0
2
2
4
8
9

d
t
y
p
e
:
 
f
l
o
a
t
6
4
</pre>

```python
#
 
p
r
i
n
t
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
w
i
t
h
 
m
i
s
s
i
n
g
 
d
a
t
a


f
o
r
 
c
o
l
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
:

 
 
 
 
i
f
 
X
_
t
r
a
i
n
[
c
o
l
]
.
i
s
n
u
l
l
(
)
.
m
e
a
n
(
)
>
0
:

 
 
 
 
 
 
 
 
p
r
i
n
t
(
c
o
l
,
 
(
X
_
t
r
a
i
n
[
c
o
l
]
.
i
s
n
u
l
l
(
)
.
m
e
a
n
(
)
)
)
```

<pre>
W
i
n
d
G
u
s
t
D
i
r
 
0
.
0
7
1
0
6
7
6
4
7
4
6
3
2
2
0
1
3

W
i
n
d
D
i
r
9
a
m
 
0
.
0
7
2
5
9
7
2
7
7
6
0
2
0
8
9
9
2

W
i
n
d
D
i
r
3
p
m
 
0
.
0
2
8
9
5
1
2
5
8
0
7
7
8
2
2
0
8
3

R
a
i
n
T
o
d
a
y
 
0
.
0
2
2
4
8
9
0
0
0
4
1
2
4
8
4
5
3

</pre>

```python
#
 
i
m
p
u
t
e
 
m
i
s
s
i
n
g
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
w
i
t
h
 
m
o
s
t
 
f
r
e
q
u
e
n
t
 
v
a
l
u
e


f
o
r
 
d
f
2
 
i
n
 
[
X
_
t
r
a
i
n
,
 
X
_
t
e
s
t
]
:

 
 
 
 
d
f
2
[
'
W
i
n
d
G
u
s
t
D
i
r
'
]
.
f
i
l
l
n
a
(
X
_
t
r
a
i
n
[
'
W
i
n
d
G
u
s
t
D
i
r
'
]
.
m
o
d
e
(
)
[
0
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)

 
 
 
 
d
f
2
[
'
W
i
n
d
D
i
r
9
a
m
'
]
.
f
i
l
l
n
a
(
X
_
t
r
a
i
n
[
'
W
i
n
d
D
i
r
9
a
m
'
]
.
m
o
d
e
(
)
[
0
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)

 
 
 
 
d
f
2
[
'
W
i
n
d
D
i
r
3
p
m
'
]
.
f
i
l
l
n
a
(
X
_
t
r
a
i
n
[
'
W
i
n
d
D
i
r
3
p
m
'
]
.
m
o
d
e
(
)
[
0
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)

 
 
 
 
d
f
2
[
'
R
a
i
n
T
o
d
a
y
'
]
.
f
i
l
l
n
a
(
X
_
t
r
a
i
n
[
'
R
a
i
n
T
o
d
a
y
'
]
.
m
o
d
e
(
)
[
0
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)
```


```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
X
_
t
r
a
i
n


X
_
t
r
a
i
n
[
c
a
t
e
g
o
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
0

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
0

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
0

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s
 
i
n
 
X
_
t
e
s
t


X
_
t
e
s
t
[
c
a
t
e
g
o
r
i
c
a
l
]
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
0

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
0

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
0

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
즉
 
최
빈
값
으
로
 
범
주
형
의
 
결
측
치
들
을
 
처
리
했
습
니
다
.


이
제
 
최
종
적
으
로
 
점
검
해
봅
니
다
.



```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
X
_
t
r
a
i
n


X
_
t
r
a
i
n
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
0

M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
0

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
0

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
0

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
 
0

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
0

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
0

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
0

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
0

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
0

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
0

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
0

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
0

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
0

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
0

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>

```python
#
 
c
h
e
c
k
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
X
_
t
e
s
t


X
_
t
e
s
t
.
i
s
n
u
l
l
(
)
.
s
u
m
(
)
```

<pre>
L
o
c
a
t
i
o
n
 
 
 
 
 
 
 
 
 
0

M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

M
a
x
T
e
m
p
 
 
 
 
 
 
 
 
 
 
0

R
a
i
n
f
a
l
l
 
 
 
 
 
 
 
 
 
0

E
v
a
p
o
r
a
t
i
o
n
 
 
 
 
 
 
0

S
u
n
s
h
i
n
e
 
 
 
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
D
i
r
 
 
 
 
 
 
0

W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
 
0

W
i
n
d
D
i
r
9
a
m
 
 
 
 
 
 
 
0

W
i
n
d
D
i
r
3
p
m
 
 
 
 
 
 
 
0

W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
 
 
0

W
i
n
d
S
p
e
e
d
3
p
m
 
 
 
 
 
0

H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
 
 
0

H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
 
 
0

P
r
e
s
s
u
r
e
3
p
m
 
 
 
 
 
 
0

C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
 
 
0

C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
 
0

T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
 
 
0

T
e
m
p
3
p
m
 
 
 
 
 
 
 
 
 
 
0

R
a
i
n
T
o
d
a
y
 
 
 
 
 
 
 
 
0

Y
e
a
r
 
 
 
 
 
 
 
 
 
 
 
 
 
0

M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
0

D
a
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0

d
t
y
p
e
:
 
i
n
t
6
4
</pre>
W
e
 
c
a
n
 
s
e
e
 
t
h
a
t
 
t
h
e
r
e
 
a
r
e
 
n
o
 
m
i
s
s
i
n
g
 
v
a
l
u
e
s
 
i
n
 
X
_
t
r
a
i
n
 
a
n
d
 
X
_
t
e
s
t
.


#
#
#
 
E
n
g
i
n
e
e
r
i
n
g
 
o
u
t
l
i
e
r
s
 
i
n
 
n
u
m
e
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s






R
a
i
n
f
a
l
l
,
 
E
v
a
p
o
r
a
t
i
o
n
,
 
W
i
n
d
S
p
e
e
d
9
a
m
 
및
 
W
i
n
d
S
p
e
e
d
3
p
m
 
열
에
 
이
상
치
(
o
u
t
l
i
e
r
s
)
가
 
포
함
되
어
 
있
는
 
것
으
로
 
확
인
되
었
습
니
다
.
 
이
상
치
를
 
제
거
하
기
 
위
해
 
상
한
선
(
t
o
p
-
c
o
d
i
n
g
)
 
접
근
법
을
 
사
용
하
여
 
최
대
값
을
 
제
한
하
겠
습
니
다
.



```python
d
e
f
 
m
a
x
_
v
a
l
u
e
(
d
f
3
,
 
v
a
r
i
a
b
l
e
,
 
t
o
p
)
:

 
 
 
 
r
e
t
u
r
n
 
n
p
.
w
h
e
r
e
(
d
f
3
[
v
a
r
i
a
b
l
e
]
>
t
o
p
,
 
t
o
p
,
 
d
f
3
[
v
a
r
i
a
b
l
e
]
)


f
o
r
 
d
f
3
 
i
n
 
[
X
_
t
r
a
i
n
,
 
X
_
t
e
s
t
]
:

 
 
 
 
d
f
3
[
'
R
a
i
n
f
a
l
l
'
]
 
=
 
m
a
x
_
v
a
l
u
e
(
d
f
3
,
 
'
R
a
i
n
f
a
l
l
'
,
 
3
.
2
)

 
 
 
 
d
f
3
[
'
E
v
a
p
o
r
a
t
i
o
n
'
]
 
=
 
m
a
x
_
v
a
l
u
e
(
d
f
3
,
 
'
E
v
a
p
o
r
a
t
i
o
n
'
,
 
2
1
.
8
)

 
 
 
 
d
f
3
[
'
W
i
n
d
S
p
e
e
d
9
a
m
'
]
 
=
 
m
a
x
_
v
a
l
u
e
(
d
f
3
,
 
'
W
i
n
d
S
p
e
e
d
9
a
m
'
,
 
5
5
)

 
 
 
 
d
f
3
[
'
W
i
n
d
S
p
e
e
d
3
p
m
'
]
 
=
 
m
a
x
_
v
a
l
u
e
(
d
f
3
,
 
'
W
i
n
d
S
p
e
e
d
3
p
m
'
,
 
5
7
)
```


```python
X
_
t
r
a
i
n
.
R
a
i
n
f
a
l
l
.
m
a
x
(
)
,
 
X
_
t
e
s
t
.
R
a
i
n
f
a
l
l
.
m
a
x
(
)
```

<pre>
(
3
.
2
,
 
3
.
2
)
</pre>

```python
X
_
t
r
a
i
n
.
E
v
a
p
o
r
a
t
i
o
n
.
m
a
x
(
)
,
 
X
_
t
e
s
t
.
E
v
a
p
o
r
a
t
i
o
n
.
m
a
x
(
)
```

<pre>
(
2
1
.
8
,
 
2
1
.
8
)
</pre>

```python
X
_
t
r
a
i
n
.
W
i
n
d
S
p
e
e
d
9
a
m
.
m
a
x
(
)
,
 
X
_
t
e
s
t
.
W
i
n
d
S
p
e
e
d
9
a
m
.
m
a
x
(
)
```

<pre>
(
5
5
.
0
,
 
5
5
.
0
)
</pre>

```python
X
_
t
r
a
i
n
.
W
i
n
d
S
p
e
e
d
3
p
m
.
m
a
x
(
)
,
 
X
_
t
e
s
t
.
W
i
n
d
S
p
e
e
d
3
p
m
.
m
a
x
(
)
```

<pre>
(
5
7
.
0
,
 
5
7
.
0
)
</pre>

```python
X
_
t
r
a
i
n
[
n
u
m
e
r
i
c
a
l
]
.
d
e
s
c
r
i
b
e
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
 
 
 
 
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
M
a
x
T
e
m
p
 
 
 
 
 
 
 
R
a
i
n
f
a
l
l
 
 
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
1
2
.
1
9
0
1
8
9
 
 
 
 
 
 
2
3
.
2
0
3
1
0
7
 
 
 
 
 
 
 
0
.
6
7
0
8
0
0
 
 
 
 
 
 
 
5
.
0
9
3
3
6
2
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
6
.
3
6
6
8
9
3
 
 
 
 
 
 
 
7
.
0
8
5
4
0
8
 
 
 
 
 
 
 
1
.
1
8
1
5
1
2
 
 
 
 
 
 
 
2
.
8
0
0
2
0
0
 
 
 

m
i
n
 
 
 
 
 
 
 
 
-
8
.
5
0
0
0
0
0
 
 
 
 
 
 
-
4
.
8
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
7
.
7
0
0
0
0
0
 
 
 
 
 
 
1
8
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
4
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
1
2
.
0
0
0
0
0
0
 
 
 
 
 
 
2
2
.
6
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
4
.
7
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
1
6
.
8
0
0
0
0
0
 
 
 
 
 
 
2
8
.
2
0
0
0
0
0
 
 
 
 
 
 
 
0
.
6
0
0
0
0
0
 
 
 
 
 
 
 
5
.
2
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
3
1
.
9
0
0
0
0
0
 
 
 
 
 
 
4
8
.
1
0
0
0
0
0
 
 
 
 
 
 
 
3
.
2
0
0
0
0
0
 
 
 
 
 
 
2
1
.
8
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
7
.
9
8
2
4
7
6
 
 
 
 
 
 
3
9
.
9
8
2
0
9
1
 
 
 
 
 
 
1
4
.
0
2
9
3
8
1
 
 
 
 
 
 
1
8
.
6
8
7
4
6
6
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
2
.
7
6
1
6
3
9
 
 
 
 
 
 
1
3
.
1
2
7
9
5
3
 
 
 
 
 
 
 
8
.
8
3
5
5
9
6
 
 
 
 
 
 
 
8
.
7
0
0
6
1
8
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
6
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
8
.
2
0
0
0
0
0
 
 
 
 
 
 
3
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
7
.
0
0
0
0
0
0
 
 
 
 
 
 
1
3
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
8
.
4
0
0
0
0
0
 
 
 
 
 
 
3
9
.
0
0
0
0
0
0
 
 
 
 
 
 
1
3
.
0
0
0
0
0
0
 
 
 
 
 
 
1
9
.
0
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
8
.
6
0
0
0
0
0
 
 
 
 
 
 
4
6
.
0
0
0
0
0
0
 
 
 
 
 
 
1
9
.
0
0
0
0
0
0
 
 
 
 
 
 
2
4
.
0
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
1
4
.
5
0
0
0
0
0
 
 
 
 
 
1
3
5
.
0
0
0
0
0
0
 
 
 
 
 
 
5
5
.
0
0
0
0
0
0
 
 
 
 
 
 
5
7
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
 
 
P
r
e
s
s
u
r
e
9
a
m
 
 
 
 
P
r
e
s
s
u
r
e
3
p
m
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
6
8
.
9
5
0
6
9
1
 
 
 
 
 
 
5
1
.
6
0
5
8
2
8
 
 
 
 
1
0
1
7
.
6
3
9
8
9
1
 
 
 
 
1
0
1
5
.
2
4
4
9
4
6
 
 
 

s
t
d
 
 
 
 
 
 
 
 
1
8
.
8
1
1
4
3
7
 
 
 
 
 
 
2
0
.
4
3
9
9
9
9
 
 
 
 
 
 
 
6
.
7
2
8
2
3
4
 
 
 
 
 
 
 
6
.
6
6
1
5
1
7
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
9
8
0
.
5
0
0
0
0
0
 
 
 
 
 
9
7
7
.
1
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
5
7
.
0
0
0
0
0
0
 
 
 
 
 
 
3
7
.
0
0
0
0
0
0
 
 
 
 
1
0
1
3
.
5
0
0
0
0
0
 
 
 
 
1
0
1
1
.
1
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
7
0
.
0
0
0
0
0
0
 
 
 
 
 
 
5
2
.
0
0
0
0
0
0
 
 
 
 
1
0
1
7
.
6
0
0
0
0
0
 
 
 
 
1
0
1
5
.
2
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
8
3
.
0
0
0
0
0
0
 
 
 
 
 
 
6
5
.
0
0
0
0
0
0
 
 
 
 
1
0
2
1
.
8
0
0
0
0
0
 
 
 
 
1
0
1
9
.
4
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
1
0
0
.
0
0
0
0
0
0
 
 
 
 
 
1
0
0
.
0
0
0
0
0
0
 
 
 
 
1
0
4
1
.
0
0
0
0
0
0
 
 
 
 
1
0
3
9
.
6
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
C
l
o
u
d
9
a
m
 
 
 
 
 
 
 
C
l
o
u
d
3
p
m
 
 
 
 
 
 
 
 
T
e
m
p
9
a
m
 
 
 
 
 
 
 
 
T
e
m
p
3
p
m
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
4
.
6
6
4
0
9
2
 
 
 
 
 
 
 
4
.
7
1
0
7
2
8
 
 
 
 
 
 
1
6
.
9
7
9
4
5
4
 
 
 
 
 
 
2
1
.
6
5
7
1
9
5
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
2
.
2
8
0
6
8
7
 
 
 
 
 
 
 
2
.
1
0
6
0
4
0
 
 
 
 
 
 
 
6
.
4
4
9
6
4
1
 
 
 
 
 
 
 
6
.
8
4
8
2
9
3
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
-
7
.
2
0
0
0
0
0
 
 
 
 
 
 
-
5
.
4
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
3
.
0
0
0
0
0
0
 
 
 
 
 
 
 
4
.
0
0
0
0
0
0
 
 
 
 
 
 
1
2
.
3
0
0
0
0
0
 
 
 
 
 
 
1
6
.
7
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
5
.
0
0
0
0
0
0
 
 
 
 
 
 
 
5
.
0
0
0
0
0
0
 
 
 
 
 
 
1
6
.
7
0
0
0
0
0
 
 
 
 
 
 
2
1
.
1
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
6
.
0
0
0
0
0
0
 
 
 
 
 
 
 
6
.
0
0
0
0
0
0
 
 
 
 
 
 
2
1
.
5
0
0
0
0
0
 
 
 
 
 
 
2
6
.
2
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
9
.
0
0
0
0
0
0
 
 
 
 
 
 
 
8
.
0
0
0
0
0
0
 
 
 
 
 
 
4
0
.
2
0
0
0
0
0
 
 
 
 
 
 
4
6
.
7
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
Y
e
a
r
 
 
 
 
 
 
 
 
 
 
M
o
n
t
h
 
 
 
 
 
 
 
 
 
 
 
 
D
a
y
 
 

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 

m
e
a
n
 
 
 
 
 
2
0
1
2
.
7
6
7
0
5
8
 
 
 
 
 
 
 
6
.
3
9
5
0
9
1
 
 
 
 
 
 
1
5
.
7
3
1
9
5
4
 
 

s
t
d
 
 
 
 
 
 
 
 
 
2
.
5
3
8
4
0
1
 
 
 
 
 
 
 
3
.
4
2
5
4
5
1
 
 
 
 
 
 
 
8
.
7
9
6
9
3
1
 
 

m
i
n
 
 
 
 
 
 
2
0
0
7
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 

2
5
%
 
 
 
 
 
 
2
0
1
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
3
.
0
0
0
0
0
0
 
 
 
 
 
 
 
8
.
0
0
0
0
0
0
 
 

5
0
%
 
 
 
 
 
 
2
0
1
3
.
0
0
0
0
0
0
 
 
 
 
 
 
 
6
.
0
0
0
0
0
0
 
 
 
 
 
 
1
6
.
0
0
0
0
0
0
 
 

7
5
%
 
 
 
 
 
 
2
0
1
5
.
0
0
0
0
0
0
 
 
 
 
 
 
 
9
.
0
0
0
0
0
0
 
 
 
 
 
 
2
3
.
0
0
0
0
0
0
 
 

m
a
x
 
 
 
 
 
 
2
0
1
7
.
0
0
0
0
0
0
 
 
 
 
 
 
1
2
.
0
0
0
0
0
0
 
 
 
 
 
 
3
1
.
0
0
0
0
0
0
 
 
</pre>
이
제
 
R
a
i
n
f
a
l
l
,
 
E
v
a
p
o
r
a
t
i
o
n
,
 
W
i
n
d
S
p
e
e
d
9
a
m
 
및
 
W
i
n
d
S
p
e
e
d
3
p
m
 
열
의
 
이
상
값
이
 
최
댓
값
으
로
 
제
한
되
었
습
니
다
.


#
#
#
 
E
n
c
o
d
e
 
c
a
t
e
g
o
r
i
c
a
l
 
v
a
r
i
a
b
l
e
s



```python
c
a
t
e
g
o
r
i
c
a
l
```

<pre>
[
'
L
o
c
a
t
i
o
n
'
,
 
'
W
i
n
d
G
u
s
t
D
i
r
'
,
 
'
W
i
n
d
D
i
r
9
a
m
'
,
 
'
W
i
n
d
D
i
r
3
p
m
'
,
 
'
R
a
i
n
T
o
d
a
y
'
]
</pre>

```python
X
_
t
r
a
i
n
[
c
a
t
e
g
o
r
i
c
a
l
]
.
h
e
a
d
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
 
 
 
 
L
o
c
a
t
i
o
n
 
W
i
n
d
G
u
s
t
D
i
r
 
W
i
n
d
D
i
r
9
a
m
 
W
i
n
d
D
i
r
3
p
m
 
R
a
i
n
T
o
d
a
y

2
2
9
2
6
 
 
 
N
o
r
f
o
l
k
I
s
l
a
n
d
 
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
N
o

8
0
7
3
5
 
 
 
 
 
 
 
 
W
a
t
s
o
n
i
a
 
 
 
 
 
 
 
 
 
 
N
E
 
 
 
 
 
 
 
 
N
N
W
 
 
 
 
 
 
 
 
N
N
E
 
 
 
 
 
 
 
 
N
o

1
2
1
7
6
4
 
 
 
 
 
 
 
 
 
 
P
e
r
t
h
 
 
 
 
 
 
 
 
 
 
S
W
 
 
 
 
 
 
 
 
 
 
N
 
 
 
 
 
 
 
 
 
S
W
 
 
 
 
 
 
 
Y
e
s

1
3
9
8
2
1
 
 
 
 
 
 
 
 
 
D
a
r
w
i
n
 
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
 
 
E
 
 
 
 
 
 
 
 
N
o

1
8
6
7
 
 
 
 
 
 
 
 
 
 
 
A
l
b
u
r
y
 
 
 
 
 
 
 
 
 
 
 
E
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
 
 
E
 
 
 
 
 
 
 
Y
e
s
</pre>

```python
#
 
e
n
c
o
d
e
 
R
a
i
n
T
o
d
a
y
 
v
a
r
i
a
b
l
e


i
m
p
o
r
t
 
c
a
t
e
g
o
r
y
_
e
n
c
o
d
e
r
s
 
a
s
 
c
e


e
n
c
o
d
e
r
 
=
 
c
e
.
B
i
n
a
r
y
E
n
c
o
d
e
r
(
c
o
l
s
=
[
'
R
a
i
n
T
o
d
a
y
'
]
)


X
_
t
r
a
i
n
 
=
 
e
n
c
o
d
e
r
.
f
i
t
_
t
r
a
n
s
f
o
r
m
(
X
_
t
r
a
i
n
)


X
_
t
e
s
t
 
=
 
e
n
c
o
d
e
r
.
t
r
a
n
s
f
o
r
m
(
X
_
t
e
s
t
)
```

좀
더
 
정
확
한
 
측
정
을
 
위
해
 
R
a
i
n
T
o
d
a
y
 
특
성
을
 
이
진
화
합
니
다
.



```python
X
_
t
r
a
i
n
.
h
e
a
d
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
 
 
 
 
L
o
c
a
t
i
o
n
 
 
M
i
n
T
e
m
p
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
 
\

2
2
9
2
6
 
 
 
N
o
r
f
o
l
k
I
s
l
a
n
d
 
 
 
 
 
1
8
.
8
 
 
 
 
 
2
3
.
7
 
 
 
 
 
 
 
0
.
2
 
 
 
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
7
.
3
 
 
 

8
0
7
3
5
 
 
 
 
 
 
 
 
W
a
t
s
o
n
i
a
 
 
 
 
 
 
9
.
3
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
0
.
2
 
 
 
 
 
 
 
 
 
 
1
.
6
 
 
 
 
 
 
1
0
.
9
 
 
 

1
2
1
7
6
4
 
 
 
 
 
 
 
 
 
 
P
e
r
t
h
 
 
 
 
 
1
0
.
9
 
 
 
 
 
2
2
.
2
 
 
 
 
 
 
 
1
.
4
 
 
 
 
 
 
 
 
 
 
1
.
2
 
 
 
 
 
 
 
9
.
6
 
 
 

1
3
9
8
2
1
 
 
 
 
 
 
 
 
 
D
a
r
w
i
n
 
 
 
 
 
1
9
.
3
 
 
 
 
 
2
9
.
9
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
9
.
2
 
 
 
 
 
 
1
1
.
0
 
 
 

1
8
6
7
 
 
 
 
 
 
 
 
 
 
 
A
l
b
u
r
y
 
 
 
 
 
1
5
.
7
 
 
 
 
 
1
7
.
6
 
 
 
 
 
 
 
3
.
2
 
 
 
 
 
 
 
 
 
 
4
.
7
 
 
 
 
 
 
 
8
.
4
 
 
 


 
 
 
 
 
 
 
W
i
n
d
G
u
s
t
D
i
r
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
W
i
n
d
D
i
r
9
a
m
 
W
i
n
d
D
i
r
3
p
m
 
 
.
.
.
 
 
P
r
e
s
s
u
r
e
3
p
m
 
 
\

2
2
9
2
6
 
 
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
 
 
 
5
2
.
0
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
E
S
E
 
 
.
.
.
 
 
 
 
 
 
 
1
0
1
3
.
9
 
 
 

8
0
7
3
5
 
 
 
 
 
 
 
 
 
 
 
N
E
 
 
 
 
 
 
 
 
 
 
 
4
8
.
0
 
 
 
 
 
 
 
 
N
N
W
 
 
 
 
 
 
 
 
N
N
E
 
 
.
.
.
 
 
 
 
 
 
 
1
0
1
4
.
6
 
 
 

1
2
1
7
6
4
 
 
 
 
 
 
 
 
 
 
S
W
 
 
 
 
 
 
 
 
 
 
 
2
6
.
0
 
 
 
 
 
 
 
 
 
 
N
 
 
 
 
 
 
 
 
 
S
W
 
 
.
.
.
 
 
 
 
 
 
 
1
0
1
4
.
9
 
 
 

1
3
9
8
2
1
 
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
 
 
 
4
3
.
0
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
 
 
E
 
 
.
.
.
 
 
 
 
 
 
 
1
0
1
2
.
1
 
 
 

1
8
6
7
 
 
 
 
 
 
 
 
 
 
 
 
 
E
 
 
 
 
 
 
 
 
 
 
 
2
0
.
0
 
 
 
 
 
 
 
 
E
S
E
 
 
 
 
 
 
 
 
 
 
E
 
 
.
.
.
 
 
 
 
 
 
 
1
0
1
0
.
5
 
 
 


 
 
 
 
 
 
 
 
C
l
o
u
d
9
a
m
 
 
C
l
o
u
d
3
p
m
 
 
T
e
m
p
9
a
m
 
 
T
e
m
p
3
p
m
 
 
R
a
i
n
T
o
d
a
y
_
0
 
 
R
a
i
n
T
o
d
a
y
_
1
 
 
Y
e
a
r
 
 
\

2
2
9
2
6
 
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
2
1
.
4
 
 
 
 
 
2
2
.
2
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
1
 
 
2
0
1
4
 
 
 

8
0
7
3
5
 
 
 
 
 
 
 
 
3
.
0
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
1
4
.
3
 
 
 
 
 
2
3
.
2
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
1
 
 
2
0
1
6
 
 
 

1
2
1
7
6
4
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
2
.
0
 
 
 
 
 
1
6
.
6
 
 
 
 
 
2
1
.
5
 
 
 
 
 
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
2
0
1
1
 
 
 

1
3
9
8
2
1
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
2
3
.
2
 
 
 
 
 
2
9
.
1
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
 
 
 
 
 
1
 
 
2
0
1
0
 
 
 

1
8
6
7
 
 
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
 
 
8
.
0
 
 
 
 
 
1
6
.
5
 
 
 
 
 
1
7
.
3
 
 
 
 
 
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
 
 
 
 
 
0
 
 
2
0
1
4
 
 
 


 
 
 
 
 
 
 
 
M
o
n
t
h
 
 
D
a
y
 
 

2
2
9
2
6
 
 
 
 
 
 
 
3
 
 
 
1
2
 
 

8
0
7
3
5
 
 
 
 
 
 
1
0
 
 
 
 
6
 
 

1
2
1
7
6
4
 
 
 
 
 
 
8
 
 
 
3
1
 
 

1
3
9
8
2
1
 
 
 
 
 
 
6
 
 
 
1
1
 
 

1
8
6
7
 
 
 
 
 
 
 
 
4
 
 
 
1
0
 
 


[
5
 
r
o
w
s
 
x
 
2
5
 
c
o
l
u
m
n
s
]
</pre>
이
제
 
훈
련
셋
을
 
만
듭
니
다
.



```python
X
_
t
r
a
i
n
 
=
 
p
d
.
c
o
n
c
a
t
(
[
X
_
t
r
a
i
n
[
n
u
m
e
r
i
c
a
l
]
,
 
X
_
t
r
a
i
n
[
[
'
R
a
i
n
T
o
d
a
y
_
0
'
,
 
'
R
a
i
n
T
o
d
a
y
_
1
'
]
]
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
r
a
i
n
.
L
o
c
a
t
i
o
n
)
,
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
r
a
i
n
.
W
i
n
d
G
u
s
t
D
i
r
)
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
r
a
i
n
.
W
i
n
d
D
i
r
9
a
m
)
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
r
a
i
n
.
W
i
n
d
D
i
r
3
p
m
)
]
,
 
a
x
i
s
=
1
)
```


```python
X
_
t
r
a
i
n
.
h
e
a
d
(
)
```

<pre>
 
 
 
 
 
 
 
 
M
i
n
T
e
m
p
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
\

2
2
9
2
6
 
 
 
 
 
 
1
8
.
8
 
 
 
 
 
2
3
.
7
 
 
 
 
 
 
 
0
.
2
 
 
 
 
 
 
 
 
 
 
5
.
0
 
 
 
 
 
 
 
7
.
3
 
 
 
 
 
 
 
 
 
 
 
5
2
.
0
 
 
 

8
0
7
3
5
 
 
 
 
 
 
 
9
.
3
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
0
.
2
 
 
 
 
 
 
 
 
 
 
1
.
6
 
 
 
 
 
 
1
0
.
9
 
 
 
 
 
 
 
 
 
 
 
4
8
.
0
 
 
 

1
2
1
7
6
4
 
 
 
 
 
1
0
.
9
 
 
 
 
 
2
2
.
2
 
 
 
 
 
 
 
1
.
4
 
 
 
 
 
 
 
 
 
 
1
.
2
 
 
 
 
 
 
 
9
.
6
 
 
 
 
 
 
 
 
 
 
 
2
6
.
0
 
 
 

1
3
9
8
2
1
 
 
 
 
 
1
9
.
3
 
 
 
 
 
2
9
.
9
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
9
.
2
 
 
 
 
 
 
1
1
.
0
 
 
 
 
 
 
 
 
 
 
 
4
3
.
0
 
 
 

1
8
6
7
 
 
 
 
 
 
 
1
5
.
7
 
 
 
 
 
1
7
.
6
 
 
 
 
 
 
 
3
.
2
 
 
 
 
 
 
 
 
 
 
4
.
7
 
 
 
 
 
 
 
8
.
4
 
 
 
 
 
 
 
 
 
 
 
2
0
.
0
 
 
 


 
 
 
 
 
 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
.
.
.
 
 
N
N
W
 
 
N
W
 
 
S
 
 
\

2
2
9
2
6
 
 
 
 
 
 
 
 
 
 
 
3
1
.
0
 
 
 
 
 
 
 
 
 
 
2
8
.
0
 
 
 
 
 
 
 
 
 
7
4
.
0
 
 
 
 
 
 
 
 
 
7
3
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

8
0
7
3
5
 
 
 
 
 
 
 
 
 
 
 
1
3
.
0
 
 
 
 
 
 
 
 
 
 
2
4
.
0
 
 
 
 
 
 
 
 
 
7
4
.
0
 
 
 
 
 
 
 
 
 
5
5
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

1
2
1
7
6
4
 
 
 
 
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
1
1
.
0
 
 
 
 
 
 
 
 
 
8
5
.
0
 
 
 
 
 
 
 
 
 
4
7
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

1
3
9
8
2
1
 
 
 
 
 
 
 
 
 
 
2
6
.
0
 
 
 
 
 
 
 
 
 
 
1
7
.
0
 
 
 
 
 
 
 
 
 
4
4
.
0
 
 
 
 
 
 
 
 
 
3
7
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

1
8
6
7
 
 
 
 
 
 
 
 
 
 
 
 
1
1
.
0
 
 
 
 
 
 
 
 
 
 
1
3
.
0
 
 
 
 
 
 
 
 
1
0
0
.
0
 
 
 
 
 
 
 
 
1
0
0
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 


 
 
 
 
 
 
 
 
S
E
 
 
S
S
E
 
 
S
S
W
 
 
S
W
 
 
W
 
 
W
N
W
 
 
W
S
W
 
 

2
2
9
2
6
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

8
0
7
3
5
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

1
2
1
7
6
4
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
1
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

1
3
9
8
2
1
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

1
8
6
7
 
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 


[
5
 
r
o
w
s
 
x
 
1
1
8
 
c
o
l
u
m
n
s
]
</pre>
테
스
트
셋
 
또
한
 
똑
같
은
 
방
식
으
로
 
만
들
어
 
줍
니
다
.



```python
X
_
t
e
s
t
 
=
 
p
d
.
c
o
n
c
a
t
(
[
X
_
t
e
s
t
[
n
u
m
e
r
i
c
a
l
]
,
 
X
_
t
e
s
t
[
[
'
R
a
i
n
T
o
d
a
y
_
0
'
,
 
'
R
a
i
n
T
o
d
a
y
_
1
'
]
]
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
e
s
t
.
L
o
c
a
t
i
o
n
)
,
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
e
s
t
.
W
i
n
d
G
u
s
t
D
i
r
)
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
e
s
t
.
W
i
n
d
D
i
r
9
a
m
)
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
d
.
g
e
t
_
d
u
m
m
i
e
s
(
X
_
t
e
s
t
.
W
i
n
d
D
i
r
3
p
m
)
]
,
 
a
x
i
s
=
1
)
```


```python
X
_
t
e
s
t
.
h
e
a
d
(
)
```

<pre>
 
 
 
 
 
 
 
 
M
i
n
T
e
m
p
 
 
M
a
x
T
e
m
p
 
 
R
a
i
n
f
a
l
l
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
\

1
3
8
1
7
5
 
 
 
 
 
2
1
.
9
 
 
 
 
 
3
9
.
4
 
 
 
 
 
 
 
1
.
6
 
 
 
 
 
 
 
 
 
1
1
.
2
 
 
 
 
 
 
1
1
.
5
 
 
 
 
 
 
 
 
 
 
 
5
7
.
0
 
 
 

3
8
6
3
8
 
 
 
 
 
 
2
0
.
5
 
 
 
 
 
3
7
.
5
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
9
.
2
 
 
 
 
 
 
 
8
.
4
 
 
 
 
 
 
 
 
 
 
 
5
9
.
0
 
 
 

1
2
4
0
5
8
 
 
 
 
 
 
5
.
1
 
 
 
 
 
1
7
.
2
 
 
 
 
 
 
 
0
.
2
 
 
 
 
 
 
 
 
 
 
4
.
7
 
 
 
 
 
 
 
8
.
4
 
 
 
 
 
 
 
 
 
 
 
5
0
.
0
 
 
 

9
9
2
1
4
 
 
 
 
 
 
1
1
.
9
 
 
 
 
 
1
6
.
8
 
 
 
 
 
 
 
1
.
0
 
 
 
 
 
 
 
 
 
 
4
.
7
 
 
 
 
 
 
 
8
.
4
 
 
 
 
 
 
 
 
 
 
 
2
8
.
0
 
 
 

2
5
0
9
7
 
 
 
 
 
 
 
7
.
5
 
 
 
 
 
2
1
.
3
 
 
 
 
 
 
 
0
.
0
 
 
 
 
 
 
 
 
 
 
4
.
7
 
 
 
 
 
 
 
8
.
4
 
 
 
 
 
 
 
 
 
 
 
1
5
.
0
 
 
 


 
 
 
 
 
 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
.
.
.
 
 
N
N
W
 
 
N
W
 
 
S
 
 
\

1
3
8
1
7
5
 
 
 
 
 
 
 
 
 
 
2
0
.
0
 
 
 
 
 
 
 
 
 
 
3
3
.
0
 
 
 
 
 
 
 
 
 
5
0
.
0
 
 
 
 
 
 
 
 
 
2
6
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

3
8
6
3
8
 
 
 
 
 
 
 
 
 
 
 
1
7
.
0
 
 
 
 
 
 
 
 
 
 
2
0
.
0
 
 
 
 
 
 
 
 
 
4
7
.
0
 
 
 
 
 
 
 
 
 
2
2
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

1
2
4
0
5
8
 
 
 
 
 
 
 
 
 
 
2
8
.
0
 
 
 
 
 
 
 
 
 
 
2
2
.
0
 
 
 
 
 
 
 
 
 
6
8
.
0
 
 
 
 
 
 
 
 
 
5
1
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

9
9
2
1
4
 
 
 
 
 
 
 
 
 
 
 
1
1
.
0
 
 
 
 
 
 
 
 
 
 
1
3
.
0
 
 
 
 
 
 
 
 
 
8
0
.
0
 
 
 
 
 
 
 
 
 
7
9
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 

2
5
0
9
7
 
 
 
 
 
 
 
 
 
 
 
 
2
.
0
 
 
 
 
 
 
 
 
 
 
 
7
.
0
 
 
 
 
 
 
 
 
 
8
8
.
0
 
 
 
 
 
 
 
 
 
5
2
.
0
 
 
.
.
.
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 


 
 
 
 
 
 
 
 
S
E
 
 
S
S
E
 
 
S
S
W
 
 
S
W
 
 
W
 
 
W
N
W
 
 
W
S
W
 
 

1
3
8
1
7
5
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

3
8
6
3
8
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

1
2
4
0
5
8
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
1
 
 
 
 
0
 
 
 
 
0
 
 

9
9
2
1
4
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
1
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 

2
5
0
9
7
 
 
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 
 
0
 
 
0
 
 
 
 
0
 
 
 
 
0
 
 


[
5
 
r
o
w
s
 
x
 
1
1
8
 
c
o
l
u
m
n
s
]
</pre>
이
제
 
훈
련
셋
과
 
데
이
터
셋
을
 
만
들
었
으
니
 
각
 
특
성
들
에
 
대
해
 
스
케
일
링
을
 
합
니
다
.


#
 
*
*
1
1
.
 
F
e
a
t
u
r
e
 
S
c
a
l
i
n
g
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
1
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
X
_
t
r
a
i
n
.
d
e
s
c
r
i
b
e
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
 
 
 
 
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
M
a
x
T
e
m
p
 
 
 
 
 
 
 
R
a
i
n
f
a
l
l
 
 
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
1
2
.
1
9
0
1
8
9
 
 
 
 
 
 
2
3
.
2
0
3
1
0
7
 
 
 
 
 
 
 
0
.
6
7
0
8
0
0
 
 
 
 
 
 
 
5
.
0
9
3
3
6
2
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
6
.
3
6
6
8
9
3
 
 
 
 
 
 
 
7
.
0
8
5
4
0
8
 
 
 
 
 
 
 
1
.
1
8
1
5
1
2
 
 
 
 
 
 
 
2
.
8
0
0
2
0
0
 
 
 

m
i
n
 
 
 
 
 
 
 
 
-
8
.
5
0
0
0
0
0
 
 
 
 
 
 
-
4
.
8
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
7
.
7
0
0
0
0
0
 
 
 
 
 
 
1
8
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
4
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
1
2
.
0
0
0
0
0
0
 
 
 
 
 
 
2
2
.
6
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
4
.
7
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
1
6
.
8
0
0
0
0
0
 
 
 
 
 
 
2
8
.
2
0
0
0
0
0
 
 
 
 
 
 
 
0
.
6
0
0
0
0
0
 
 
 
 
 
 
 
5
.
2
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
3
1
.
9
0
0
0
0
0
 
 
 
 
 
 
4
8
.
1
0
0
0
0
0
 
 
 
 
 
 
 
3
.
2
0
0
0
0
0
 
 
 
 
 
 
2
1
.
8
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
7
.
9
8
2
4
7
6
 
 
 
 
 
 
3
9
.
9
8
2
0
9
1
 
 
 
 
 
 
1
4
.
0
2
9
3
8
1
 
 
 
 
 
 
1
8
.
6
8
7
4
6
6
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
2
.
7
6
1
6
3
9
 
 
 
 
 
 
1
3
.
1
2
7
9
5
3
 
 
 
 
 
 
 
8
.
8
3
5
5
9
6
 
 
 
 
 
 
 
8
.
7
0
0
6
1
8
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
6
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
8
.
2
0
0
0
0
0
 
 
 
 
 
 
3
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
7
.
0
0
0
0
0
0
 
 
 
 
 
 
1
3
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
8
.
4
0
0
0
0
0
 
 
 
 
 
 
3
9
.
0
0
0
0
0
0
 
 
 
 
 
 
1
3
.
0
0
0
0
0
0
 
 
 
 
 
 
1
9
.
0
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
8
.
6
0
0
0
0
0
 
 
 
 
 
 
4
6
.
0
0
0
0
0
0
 
 
 
 
 
 
1
9
.
0
0
0
0
0
0
 
 
 
 
 
 
2
4
.
0
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
1
4
.
5
0
0
0
0
0
 
 
 
 
 
1
3
5
.
0
0
0
0
0
0
 
 
 
 
 
 
5
5
.
0
0
0
0
0
0
 
 
 
 
 
 
5
7
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
 
N
N
W
 
 
 
 
 
 
 
 
 
 
 
 
 
N
W
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
.
.
.
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
6
8
.
9
5
0
6
9
1
 
 
 
 
 
 
5
1
.
6
0
5
8
2
8
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
5
4
0
7
8
 
 
 
 
 
 
 
0
.
0
5
9
1
2
3
 
 
 

s
t
d
 
 
 
 
 
 
 
 
1
8
.
8
1
1
4
3
7
 
 
 
 
 
 
2
0
.
4
3
9
9
9
9
 
 
.
.
.
 
 
 
 
 
 
 
0
.
2
2
6
1
7
3
 
 
 
 
 
 
 
0
.
2
3
5
8
5
5
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
5
7
.
0
0
0
0
0
0
 
 
 
 
 
 
3
7
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
7
0
.
0
0
0
0
0
0
 
 
 
 
 
 
5
2
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
8
3
.
0
0
0
0
0
0
 
 
 
 
 
 
6
5
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
1
0
0
.
0
0
0
0
0
0
 
 
 
 
 
1
0
0
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
S
 
 
 
 
 
 
 
 
 
 
 
 
 
S
E
 
 
 
 
 
 
 
 
 
 
 
 
S
S
E
 
 
 
 
 
 
 
 
 
 
 
 
S
S
W
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
0
6
8
4
4
7
 
 
 
 
 
 
 
0
.
1
0
3
7
2
3
 
 
 
 
 
 
 
0
.
0
6
5
2
2
4
 
 
 
 
 
 
 
0
.
0
5
6
0
5
5
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
2
5
2
5
1
2
 
 
 
 
 
 
 
0
.
3
0
4
9
0
2
 
 
 
 
 
 
 
0
.
2
4
6
9
2
2
 
 
 
 
 
 
 
0
.
2
3
0
0
2
9
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
S
W
 
 
 
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
 
 
 
 
W
N
W
 
 
 
 
 
 
 
 
 
 
 
 
W
S
W
 
 

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
0
6
4
7
8
6
 
 
 
 
 
 
 
0
.
0
6
9
3
2
3
 
 
 
 
 
 
 
0
.
0
6
0
3
0
9
 
 
 
 
 
 
 
0
.
0
6
4
9
5
8
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
2
4
6
1
4
9
 
 
 
 
 
 
 
0
.
2
5
4
0
0
4
 
 
 
 
 
 
 
0
.
2
3
8
0
5
9
 
 
 
 
 
 
 
0
.
2
4
6
4
5
2
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 


[
8
 
r
o
w
s
 
x
 
1
1
8
 
c
o
l
u
m
n
s
]
</pre>

```python
c
o
l
s
 
=
 
X
_
t
r
a
i
n
.
c
o
l
u
m
n
s
```


```python
f
r
o
m
 
s
k
l
e
a
r
n
.
p
r
e
p
r
o
c
e
s
s
i
n
g
 
i
m
p
o
r
t
 
M
i
n
M
a
x
S
c
a
l
e
r


s
c
a
l
e
r
 
=
 
M
i
n
M
a
x
S
c
a
l
e
r
(
)


X
_
t
r
a
i
n
 
=
 
s
c
a
l
e
r
.
f
i
t
_
t
r
a
n
s
f
o
r
m
(
X
_
t
r
a
i
n
)


X
_
t
e
s
t
 
=
 
s
c
a
l
e
r
.
t
r
a
n
s
f
o
r
m
(
X
_
t
e
s
t
)

```


```python
X
_
t
r
a
i
n
 
=
 
p
d
.
D
a
t
a
F
r
a
m
e
(
X
_
t
r
a
i
n
,
 
c
o
l
u
m
n
s
=
[
c
o
l
s
]
)
```


```python
X
_
t
e
s
t
 
=
 
p
d
.
D
a
t
a
F
r
a
m
e
(
X
_
t
e
s
t
,
 
c
o
l
u
m
n
s
=
[
c
o
l
s
]
)
```


```python
X
_
t
r
a
i
n
.
d
e
s
c
r
i
b
e
(
)
```

<pre>
 
 
 
 
 
 
 
 
 
 
 
 
 
M
i
n
T
e
m
p
 
 
 
 
 
 
 
 
M
a
x
T
e
m
p
 
 
 
 
 
 
 
R
a
i
n
f
a
l
l
 
 
 
 
E
v
a
p
o
r
a
t
i
o
n
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
5
1
2
1
3
3
 
 
 
 
 
 
 
0
.
5
2
9
3
5
9
 
 
 
 
 
 
 
0
.
2
0
9
6
2
5
 
 
 
 
 
 
 
0
.
2
3
3
6
4
0
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
1
5
7
5
9
6
 
 
 
 
 
 
 
0
.
1
3
3
9
4
0
 
 
 
 
 
 
 
0
.
3
6
9
2
2
3
 
 
 
 
 
 
 
0
.
1
2
8
4
5
0
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
4
0
0
9
9
0
 
 
 
 
 
 
 
0
.
4
3
1
0
0
2
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
1
8
3
4
8
6
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
5
0
7
4
2
6
 
 
 
 
 
 
 
0
.
5
1
7
9
5
8
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
2
1
5
5
9
6
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
6
2
6
2
3
8
 
 
 
 
 
 
 
0
.
6
2
3
8
1
9
 
 
 
 
 
 
 
0
.
1
8
7
5
0
0
 
 
 
 
 
 
 
0
.
2
3
8
5
3
2
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
S
u
n
s
h
i
n
e
 
 
W
i
n
d
G
u
s
t
S
p
e
e
d
 
 
 
W
i
n
d
S
p
e
e
d
9
a
m
 
 
 
W
i
n
d
S
p
e
e
d
3
p
m
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
5
5
0
5
1
6
 
 
 
 
 
 
 
0
.
2
6
3
4
2
7
 
 
 
 
 
 
 
0
.
2
5
5
0
8
0
 
 
 
 
 
 
 
0
.
3
2
7
8
5
0
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
1
9
0
4
5
8
 
 
 
 
 
 
 
0
.
1
0
1
7
6
7
 
 
 
 
 
 
 
0
.
1
6
0
6
4
7
 
 
 
 
 
 
 
0
.
1
5
2
6
4
2
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
5
6
5
5
1
7
 
 
 
 
 
 
 
0
.
1
9
3
7
9
8
 
 
 
 
 
 
 
0
.
1
2
7
2
7
3
 
 
 
 
 
 
 
0
.
2
2
8
0
7
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
5
7
9
3
1
0
 
 
 
 
 
 
 
0
.
2
5
5
8
1
4
 
 
 
 
 
 
 
0
.
2
3
6
3
6
4
 
 
 
 
 
 
 
0
.
3
3
3
3
3
3
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
5
9
3
1
0
3
 
 
 
 
 
 
 
0
.
3
1
0
0
7
8
 
 
 
 
 
 
 
0
.
3
4
5
4
5
5
 
 
 
 
 
 
 
0
.
4
2
1
0
5
3
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
H
u
m
i
d
i
t
y
9
a
m
 
 
 
 
H
u
m
i
d
i
t
y
3
p
m
 
 
.
.
.
 
 
 
 
 
 
 
 
 
 
 
 
N
N
W
 
 
 
 
 
 
 
 
 
 
 
 
 
N
W
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
.
.
.
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
6
8
9
5
0
7
 
 
 
 
 
 
 
0
.
5
1
6
0
5
8
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
5
4
0
7
8
 
 
 
 
 
 
 
0
.
0
5
9
1
2
3
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
1
8
8
1
1
4
 
 
 
 
 
 
 
0
.
2
0
4
4
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
2
2
6
1
7
3
 
 
 
 
 
 
 
0
.
2
3
5
8
5
5
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
5
7
0
0
0
0
 
 
 
 
 
 
 
0
.
3
7
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
7
0
0
0
0
0
 
 
 
 
 
 
 
0
.
5
2
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
8
3
0
0
0
0
 
 
 
 
 
 
 
0
.
6
5
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
.
.
.
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
S
 
 
 
 
 
 
 
 
 
 
 
 
 
S
E
 
 
 
 
 
 
 
 
 
 
 
 
S
S
E
 
 
 
 
 
 
 
 
 
 
 
 
S
S
W
 
 
\

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
0
6
8
4
4
7
 
 
 
 
 
 
 
0
.
1
0
3
7
2
3
 
 
 
 
 
 
 
0
.
0
6
5
2
2
4
 
 
 
 
 
 
 
0
.
0
5
6
0
5
5
 
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
2
5
2
5
1
2
 
 
 
 
 
 
 
0
.
3
0
4
9
0
2
 
 
 
 
 
 
 
0
.
2
4
6
9
2
2
 
 
 
 
 
 
 
0
.
2
3
0
0
2
9
 
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
S
W
 
 
 
 
 
 
 
 
 
 
 
 
 
 
W
 
 
 
 
 
 
 
 
 
 
 
 
W
N
W
 
 
 
 
 
 
 
 
 
 
 
 
W
S
W
 
 

c
o
u
n
t
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 
1
1
6
3
6
8
.
0
0
0
0
0
0
 
 

m
e
a
n
 
 
 
 
 
 
 
 
0
.
0
6
4
7
8
6
 
 
 
 
 
 
 
0
.
0
6
9
3
2
3
 
 
 
 
 
 
 
0
.
0
6
0
3
0
9
 
 
 
 
 
 
 
0
.
0
6
4
9
5
8
 
 

s
t
d
 
 
 
 
 
 
 
 
 
0
.
2
4
6
1
4
9
 
 
 
 
 
 
 
0
.
2
5
4
0
0
4
 
 
 
 
 
 
 
0
.
2
3
8
0
5
9
 
 
 
 
 
 
 
0
.
2
4
6
4
5
2
 
 

m
i
n
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

2
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

5
0
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

7
5
%
 
 
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 
 
 
 
 
 
0
.
0
0
0
0
0
0
 
 

m
a
x
 
 
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 
 
 
 
 
 
1
.
0
0
0
0
0
0
 
 


[
8
 
r
o
w
s
 
x
 
1
1
8
 
c
o
l
u
m
n
s
]
</pre>
여
전
히
 
테
스
트
셋
은
 
훈
련
을
 
시
키
지
 
않
도
록
 
주
의
해
야
합
니
다
.


이
제
 
훈
련
을
 
시
작
해
봅
시
다
.




#
#
 
(
수
정
됨
)
이
후
 
코
드
를
 
진
행
하
기
 
전
 
y
데
이
터
셋
에
도
 
결
측
값
이
 
있
는
 
것
을
 
확
인
 
아
래
코
드
를
 
추
가
하
여
 
결
측
치
를
 
처
리
합
니
다
.



```python
f
r
o
m
 
s
k
l
e
a
r
n
.
p
r
e
p
r
o
c
e
s
s
i
n
g
 
i
m
p
o
r
t
 
L
a
b
e
l
E
n
c
o
d
e
r


y
_
t
r
a
i
n
 
=
 
p
d
.
D
a
t
a
F
r
a
m
e
(
y
_
t
r
a
i
n
)

y
_
t
e
s
t
 
=
 
p
d
.
D
a
t
a
F
r
a
m
e
(
y
_
t
e
s
t
)


y
_
t
r
a
i
n
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
f
i
l
l
n
a
(
y
_
t
r
a
i
n
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
m
o
d
e
(
)
[
0
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)

y
_
t
e
s
t
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
f
i
l
l
n
a
(
y
_
t
e
s
t
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
m
o
d
e
(
)
[
0
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)


t
r
a
i
n
_
l
e
 
=
 
L
a
b
e
l
E
n
c
o
d
e
r
(
)

t
e
s
t
_
l
e
 
=
 
L
a
b
e
l
E
n
c
o
d
e
r
(
)


t
r
a
i
n
_
l
e
.
f
i
t
(
y
_
t
r
a
i
n
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
a
s
t
y
p
e
(
'
s
t
r
'
)
.
d
r
o
p
_
d
u
p
l
i
c
a
t
e
s
(
)
)

t
e
s
t
_
l
e
.
f
i
t
(
y
_
t
e
s
t
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
a
s
t
y
p
e
(
'
s
t
r
'
)
.
d
r
o
p
_
d
u
p
l
i
c
a
t
e
s
(
)
)


y
_
t
r
a
i
n
[
'
e
n
c
'
]
 
=
 
t
r
a
i
n
_
l
e
.
t
r
a
n
s
f
o
r
m
(
y
_
t
r
a
i
n
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
a
s
t
y
p
e
(
'
s
t
r
'
)
)

y
_
t
e
s
t
[
'
e
n
c
_
t
e
s
t
'
]
 
=
 
t
e
s
t
_
l
e
.
t
r
a
n
s
f
o
r
m
(
y
_
t
e
s
t
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
.
a
s
t
y
p
e
(
'
s
t
r
'
)
)


y
_
t
r
a
i
n
.
d
r
o
p
(
c
o
l
u
m
n
s
=
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)

y
_
t
e
s
t
.
d
r
o
p
(
c
o
l
u
m
n
s
=
[
'
R
a
i
n
T
o
m
o
r
r
o
w
'
]
,
 
i
n
p
l
a
c
e
=
T
r
u
e
)
```

#
 
*
*
1
2
.
 
M
o
d
e
l
 
t
r
a
i
n
i
n
g
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
2
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
#
 
t
r
a
i
n
 
a
 
l
o
g
i
s
t
i
c
 
r
e
g
r
e
s
s
i
o
n
 
m
o
d
e
l
 
o
n
 
t
h
e
 
t
r
a
i
n
i
n
g
 
s
e
t

f
r
o
m
 
s
k
l
e
a
r
n
.
l
i
n
e
a
r
_
m
o
d
e
l
 
i
m
p
o
r
t
 
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n



#
 
i
n
s
t
a
n
t
i
a
t
e
 
t
h
e
 
m
o
d
e
l

l
o
g
r
e
g
 
=
 
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
)



#
 
f
i
t
 
t
h
e
 
m
o
d
e
l

l
o
g
r
e
g
.
f
i
t
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)

```

<pre>
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
1
.
0
,
 
c
l
a
s
s
_
w
e
i
g
h
t
=
N
o
n
e
,
 
d
u
a
l
=
F
a
l
s
e
,
 
f
i
t
_
i
n
t
e
r
c
e
p
t
=
T
r
u
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
e
r
c
e
p
t
_
s
c
a
l
i
n
g
=
1
,
 
l
1
_
r
a
t
i
o
=
N
o
n
e
,
 
m
a
x
_
i
t
e
r
=
1
0
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
m
u
l
t
i
_
c
l
a
s
s
=
'
w
a
r
n
'
,
 
n
_
j
o
b
s
=
N
o
n
e
,
 
p
e
n
a
l
t
y
=
'
l
2
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
t
o
l
=
0
.
0
0
0
1
,
 
v
e
r
b
o
s
e
=
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
w
a
r
m
_
s
t
a
r
t
=
F
a
l
s
e
)
</pre>
#
 
*
*
1
3
.
 
P
r
e
d
i
c
t
 
r
e
s
u
l
t
s
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
3
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
y
_
p
r
e
d
_
t
e
s
t
 
=
 
l
o
g
r
e
g
.
p
r
e
d
i
c
t
(
X
_
t
e
s
t
)


y
_
p
r
e
d
_
t
e
s
t
```

<pre>
a
r
r
a
y
(
[
0
,
 
0
,
 
0
,
 
.
.
.
,
 
1
,
 
0
,
 
0
]
)
</pre>
#
#
#
 
p
r
e
d
i
c
t
_
p
r
o
b
a
 
m
e
t
h
o
d






p
r
e
d
i
c
t
_
p
r
o
b
a
(
)
 
메
서
드
는
 
이
 
경
우
와
 
같
이
 
이
진
 
분
류
 
문
제
에
서
 
대
상
 
변
수
(
0
과
 
1
)
에
 
대
한
 
확
률
을
 
배
열
 
형
태
로
 
반
환
합
니
다
.
 
여
기
서
 
0
은
 
비
가
 
오
지
 
않
을
 
확
률
,
 
1
은
 
비
가
 
올
 
확
률
입
니
다
.
 
예
측
된
 
확
률
이
 
0
.
4
이
면
,
 
해
당
 
데
이
터
에
 
대
해
 
모
델
은
 
비
가
 
오
지
 
않
을
 
확
률
이
 
0
.
6
,
 
비
가
 
올
 
확
률
이
 
0
.
4
라
고
 
예
측
한
 
것
입
니
다
.



```python
#
 
p
r
o
b
a
b
i
l
i
t
y
 
o
f
 
g
e
t
t
i
n
g
 
o
u
t
p
u
t
 
a
s
 
0
 
-
 
n
o
 
r
a
i
n


l
o
g
r
e
g
.
p
r
e
d
i
c
t
_
p
r
o
b
a
(
X
_
t
e
s
t
)
[
:
,
0
]
```

<pre>
a
r
r
a
y
(
[
0
.
8
3
2
1
8
0
1
2
,
 
0
.
7
4
5
4
7
8
9
7
,
 
0
.
7
9
8
6
4
8
9
9
,
 
.
.
.
,
 
0
.
4
2
0
2
5
8
2
8
,
 
0
.
6
5
7
4
6
9
9
1
,

 
 
 
 
 
 
 
0
.
9
6
9
5
4
6
5
3
]
)
</pre>

```python
#
 
p
r
o
b
a
b
i
l
i
t
y
 
o
f
 
g
e
t
t
i
n
g
 
o
u
t
p
u
t
 
a
s
 
1
 
-
 
r
a
i
n


l
o
g
r
e
g
.
p
r
e
d
i
c
t
_
p
r
o
b
a
(
X
_
t
e
s
t
)
[
:
,
1
]
```

<pre>
a
r
r
a
y
(
[
0
.
1
6
7
8
1
9
8
8
,
 
0
.
2
5
4
5
2
1
0
3
,
 
0
.
2
0
1
3
5
1
0
1
,
 
.
.
.
,
 
0
.
5
7
9
7
4
1
7
2
,
 
0
.
3
4
2
5
3
0
0
9
,

 
 
 
 
 
 
 
0
.
0
3
0
4
5
3
4
7
]
)
</pre>
#
 
*
*
1
4
.
 
C
h
e
c
k
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
4
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
f
r
o
m
 
s
k
l
e
a
r
n
.
m
e
t
r
i
c
s
 
i
m
p
o
r
t
 
a
c
c
u
r
a
c
y
_
s
c
o
r
e


p
r
i
n
t
(
'
M
o
d
e
l
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
{
0
:
0
.
4
f
}
'
.
 
f
o
r
m
a
t
(
a
c
c
u
r
a
c
y
_
s
c
o
r
e
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
_
t
e
s
t
)
)
)
```

<pre>
M
o
d
e
l
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
0
.
8
4
8
4

</pre>
y
_
t
e
s
t
가
 
테
스
트
 
세
트
에
서
의
 
실
제
 
클
래
스
 
레
이
블
을
 
나
타
내
며
,
 
y
_
p
r
e
d
_
t
e
s
t
는
 
모
델
이
 
테
스
트
 
세
트
에
 
대
해
 
예
측
한
 
클
래
스
 
레
이
블
을
 
나
타
냅
니
다
.
 
이
 
두
 
값
은
 
모
델
이
 
얼
마
나
 
정
확
하
게
 
분
류
를
 
수
행
했
는
지
를
 
평
가
하
기
 
위
해
 
비
교
되
고
,
 
이
를
 
통
해
 
모
델
의
 
성
능
을
 
평
가
할
 
수
 
있
습
니
다
.


#
#
#
 
C
o
m
p
a
r
e
 
t
h
e
 
t
r
a
i
n
-
s
e
t
 
a
n
d
 
t
e
s
t
-
s
e
t
 
a
c
c
u
r
a
c
y






이
제
 
과
적
합
을
 
확
인
하
기
 
위
해
 
학
습
 
세
트
와
 
테
스
트
 
세
트
 
정
확
도
를
 
비
교
해
보
겠
습
니
다
.



```python
y
_
p
r
e
d
_
t
r
a
i
n
 
=
 
l
o
g
r
e
g
.
p
r
e
d
i
c
t
(
X
_
t
r
a
i
n
)


y
_
p
r
e
d
_
t
r
a
i
n
```

<pre>
a
r
r
a
y
(
[
0
,
 
0
,
 
0
,
 
.
.
.
,
 
0
,
 
0
,
 
0
]
)
</pre>

```python
p
r
i
n
t
(
'
T
r
a
i
n
i
n
g
-
s
e
t
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
{
0
:
0
.
4
f
}
'
.
 
f
o
r
m
a
t
(
a
c
c
u
r
a
c
y
_
s
c
o
r
e
(
y
_
t
r
a
i
n
,
 
y
_
p
r
e
d
_
t
r
a
i
n
)
)
)
```

<pre>
T
r
a
i
n
i
n
g
-
s
e
t
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
0
.
8
4
8
8

</pre>
#
#
#
 
C
h
e
c
k
 
f
o
r
 
o
v
e
r
f
i
t
t
i
n
g
 
a
n
d
 
u
n
d
e
r
f
i
t
t
i
n
g



```python
#
 
p
r
i
n
t
 
t
h
e
 
s
c
o
r
e
s
 
o
n
 
t
r
a
i
n
i
n
g
 
a
n
d
 
t
e
s
t
 
s
e
t


p
r
i
n
t
(
'
T
r
a
i
n
i
n
g
 
s
e
t
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
l
o
g
r
e
g
.
s
c
o
r
e
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)
)
)


p
r
i
n
t
(
'
T
e
s
t
 
s
e
t
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
l
o
g
r
e
g
.
s
c
o
r
e
(
X
_
t
e
s
t
,
 
y
_
t
e
s
t
)
)
)
```

<pre>
T
r
a
i
n
i
n
g
 
s
e
t
 
s
c
o
r
e
:
 
0
.
8
4
8
8

T
e
s
t
 
s
e
t
 
s
c
o
r
e
:
 
0
.
8
4
8
4

</pre>
훈
련
 
세
트
의
 
정
확
도
 
점
수
는
 
0
.
8
4
8
8
이
고
 
테
스
트
 
세
트
의
 
정
확
도
는
 
0
.
8
4
8
4
입
니
다
.
 
이
 
두
 
값
은
 
매
우
 
비
슷
합
니
다
.
 
따
라
서
 
과
적
합
 
문
제
는
 
없
습
니
다
.




로
지
스
틱
 
회
귀
에
서
 
C
 
값
의
 
기
본
값
은
 
1
입
니
다
.
 
이
 
값
은
 
훈
련
 
세
트
와
 
테
스
트
 
세
트
 
모
두
 
약
 
8
5
%
의
 
정
확
도
로
 
좋
은
 
성
능
을
 
제
공
합
니
다
.
 
그
러
나
 
훈
련
 
세
트
와
 
테
스
트
 
세
트
 
모
두
에
서
 
모
델
의
 
성
능
이
 
매
우
 
유
사
하
다
는
 
것
은
 
과
소
적
합
의
 
가
능
성
이
 
높
습
니
다
.




따
라
서
 
C
 
값
을
 
증
가
시
켜
 
더
 
유
연
한
 
모
델
을
 
적
합
시
키
려
고
 
합
니
다
.



```python
#
 
f
i
t
 
t
h
e
 
L
o
g
s
i
t
i
c
 
R
e
g
r
e
s
s
i
o
n
 
m
o
d
e
l
 
w
i
t
h
 
C
=
1
0
0


#
 
i
n
s
t
a
n
t
i
a
t
e
 
t
h
e
 
m
o
d
e
l

l
o
g
r
e
g
1
0
0
 
=
 
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
1
0
0
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
)



#
 
f
i
t
 
t
h
e
 
m
o
d
e
l

l
o
g
r
e
g
1
0
0
.
f
i
t
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)
```

<pre>
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
1
0
0
,
 
c
l
a
s
s
_
w
e
i
g
h
t
=
N
o
n
e
,
 
d
u
a
l
=
F
a
l
s
e
,
 
f
i
t
_
i
n
t
e
r
c
e
p
t
=
T
r
u
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
e
r
c
e
p
t
_
s
c
a
l
i
n
g
=
1
,
 
l
1
_
r
a
t
i
o
=
N
o
n
e
,
 
m
a
x
_
i
t
e
r
=
1
0
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
m
u
l
t
i
_
c
l
a
s
s
=
'
w
a
r
n
'
,
 
n
_
j
o
b
s
=
N
o
n
e
,
 
p
e
n
a
l
t
y
=
'
l
2
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
t
o
l
=
0
.
0
0
0
1
,
 
v
e
r
b
o
s
e
=
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
w
a
r
m
_
s
t
a
r
t
=
F
a
l
s
e
)
</pre>

```python
#
 
p
r
i
n
t
 
t
h
e
 
s
c
o
r
e
s
 
o
n
 
t
r
a
i
n
i
n
g
 
a
n
d
 
t
e
s
t
 
s
e
t


p
r
i
n
t
(
'
T
r
a
i
n
i
n
g
 
s
e
t
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
l
o
g
r
e
g
1
0
0
.
s
c
o
r
e
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)
)
)


p
r
i
n
t
(
'
T
e
s
t
 
s
e
t
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
l
o
g
r
e
g
1
0
0
.
s
c
o
r
e
(
X
_
t
e
s
t
,
 
y
_
t
e
s
t
)
)
)
```

<pre>
T
r
a
i
n
i
n
g
 
s
e
t
 
s
c
o
r
e
:
 
0
.
8
4
8
9

T
e
s
t
 
s
e
t
 
s
c
o
r
e
:
 
0
.
8
4
9
1

</pre>
이
전
 
모
델
에
서
 
C
=
1
 
값
을
 
사
용
했
을
 
때
 
학
습
 
데
이
터
와
 
테
스
트
 
데
이
터
 
모
두
 
약
 
8
5
%
의
 
정
확
도
를
 
보
였
습
니
다
.
 
그
러
나
 
이
 
두
 
값
이
 
매
우
 
유
사
하
다
는
 
것
은
 
과
소
적
합
(
u
n
d
e
r
f
i
t
t
i
n
g
)
의
 
가
능
성
이
 
있
다
는
 
것
을
 
의
미
합
니
다
.
 
따
라
서
 
C
 
값
을
 
높
여
 
더
 
복
잡
한
 
모
델
을
 
적
합
시
키
고
,
 
성
능
을
 
비
교
해
보
았
습
니
다
.
 
C
=
1
0
0
일
 
때
 
테
스
트
 
데
이
터
 
정
확
도
가
 
더
 
높
게
 
나
오
는
 
것
을
 
확
인
할
 
수
 
있
으
며
,
 
약
간
의
 
학
습
 
데
이
터
 
정
확
도
 
상
승
도
 
보
입
니
다
.
 
이
를
 
통
해
 
더
 
복
잡
한
 
모
델
이
 
더
 
좋
은
 
성
능
을
 
보
일
 
것
으
로
 
결
론
지
었
습
니
다
.


이
제
 
C
=
1
 
기
본
값
보
다
 
더
 
규
제
된
 
모
델
을
 
사
용
하
여
 
조
사
해
 
보
겠
습
니
다
.
 
C
를
 
0
.
0
1
로
 
설
정
합
니
다
.



```python
#
 
f
i
t
 
t
h
e
 
L
o
g
s
i
t
i
c
 
R
e
g
r
e
s
s
i
o
n
 
m
o
d
e
l
 
w
i
t
h
 
C
=
0
0
1


#
 
i
n
s
t
a
n
t
i
a
t
e
 
t
h
e
 
m
o
d
e
l

l
o
g
r
e
g
0
0
1
 
=
 
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
0
.
0
1
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
)



#
 
f
i
t
 
t
h
e
 
m
o
d
e
l

l
o
g
r
e
g
0
0
1
.
f
i
t
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)
```

<pre>
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
0
.
0
1
,
 
c
l
a
s
s
_
w
e
i
g
h
t
=
N
o
n
e
,
 
d
u
a
l
=
F
a
l
s
e
,
 
f
i
t
_
i
n
t
e
r
c
e
p
t
=
T
r
u
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
e
r
c
e
p
t
_
s
c
a
l
i
n
g
=
1
,
 
l
1
_
r
a
t
i
o
=
N
o
n
e
,
 
m
a
x
_
i
t
e
r
=
1
0
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
m
u
l
t
i
_
c
l
a
s
s
=
'
w
a
r
n
'
,
 
n
_
j
o
b
s
=
N
o
n
e
,
 
p
e
n
a
l
t
y
=
'
l
2
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
t
o
l
=
0
.
0
0
0
1
,
 
v
e
r
b
o
s
e
=
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
w
a
r
m
_
s
t
a
r
t
=
F
a
l
s
e
)
</pre>

```python
#
 
p
r
i
n
t
 
t
h
e
 
s
c
o
r
e
s
 
o
n
 
t
r
a
i
n
i
n
g
 
a
n
d
 
t
e
s
t
 
s
e
t


p
r
i
n
t
(
'
T
r
a
i
n
i
n
g
 
s
e
t
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
l
o
g
r
e
g
0
0
1
.
s
c
o
r
e
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)
)
)


p
r
i
n
t
(
'
T
e
s
t
 
s
e
t
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
l
o
g
r
e
g
0
0
1
.
s
c
o
r
e
(
X
_
t
e
s
t
,
 
y
_
t
e
s
t
)
)
)
```

<pre>
T
r
a
i
n
i
n
g
 
s
e
t
 
s
c
o
r
e
:
 
0
.
8
4
2
7

T
e
s
t
 
s
e
t
 
s
c
o
r
e
:
 
0
.
8
4
1
8

</pre>
C
 
값
을
 
0
.
0
1
로
 
설
정
하
여
 
더
 
규
제
된
 
모
델
을
 
사
용
하
면
,
 
기
본
 
매
개
변
수
에
 
비
해
 
훈
련
 
및
 
테
스
트
 
세
트
 
정
확
도
가
 
모
두
 
낮
아
집
니
다
.


#
#
#
 
C
o
m
p
a
r
e
 
m
o
d
e
l
 
a
c
c
u
r
a
c
y
 
w
i
t
h
 
n
u
l
l
 
a
c
c
u
r
a
c
y






위
에
서
 
언
급
한
 
것
처
럼
,
 
모
델
의
 
정
확
도
는
 
0
.
8
5
0
1
입
니
다
.
 
그
러
나
,
 
위
의
 
정
확
도
만
으
로
는
 
모
델
이
 
얼
마
나
 
좋
은
지
를
 
평
가
할
 
수
 
없
습
니
다
.
 
우
리
는
 
널
(
n
u
l
l
)
 
정
확
도
와
 
비
교
해
야
 
합
니
다
.
 
널
 
정
확
도
는
 
항
상
 
가
장
 
빈
번
한
 
클
래
스
를
 
예
측
함
으
로
써
 
달
성
할
 
수
 
있
는
 
정
확
도
입
니
다
.




그
러
므
로
,
 
먼
저
 
테
스
트
 
세
트
에
서
 
클
래
스
 
분
포
를
 
확
인
해
야
 
합
니
다
.



```python
#
 
c
h
e
c
k
 
c
l
a
s
s
 
d
i
s
t
r
i
b
u
t
i
o
n
 
i
n
 
t
e
s
t
 
s
e
t


#
 
y
_
t
e
s
t
.
v
a
l
u
e
_
c
o
u
n
t
s
(
)
```


```python
#
 
c
h
e
c
k
 
n
u
l
l
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e


n
u
l
l
_
a
c
c
u
r
a
c
y
 
=
 
(
2
2
0
6
7
/
(
2
2
0
6
7
+
6
3
7
2
)
)


p
r
i
n
t
(
'
N
u
l
l
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
{
0
:
0
.
4
f
}
'
.
 
f
o
r
m
a
t
(
n
u
l
l
_
a
c
c
u
r
a
c
y
)
)
```

<pre>
N
u
l
l
 
a
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
0
.
7
7
5
9

</pre>
예
측
 
모
델
의
 
정
확
도
 
점
수
가
 
0
.
8
5
0
1
이
고
,
 
N
u
l
l
 
정
확
도
 
점
수
는
 
0
.
7
7
5
9
입
니
다
.
 
따
라
서
 
우
리
는
 
로
지
스
틱
 
회
귀
 
모
델
이
 
클
래
스
 
레
이
블
을
 
예
측
하
는
 
데
 
아
주
 
잘
 
수
행
되
고
 
있
다
고
 
결
론
 
짓
을
 
수
 
있
습
니
다
.


위
의
 
분
석
을
 
기
반
으
로
 
우
리
는
 
분
류
 
모
델
의
 
정
확
도
가
 
매
우
 
높
다
는
 
결
론
을
 
내
릴
 
수
 
있
습
니
다
.
 
모
델
은
 
클
래
스
 
레
이
블
을
 
예
측
하
는
 
데
 
매
우
 
잘
하
고
 
있
습
니
다
.




그
러
나
 
이
는
 
값
의
 
분
포
에
 
대
한
 
정
보
를
 
제
공
하
지
 
않
으
며
,
 
분
류
기
가
 
만
드
는
 
오
류
 
유
형
에
 
대
한
 
정
보
도
 
제
공
하
지
 
않
습
니
다
.




이
를
 
해
결
하
기
 
위
해
 
우
리
에
게
는
 
C
o
n
f
u
s
i
o
n
 
M
a
t
r
i
x
라
는
 
도
구
가
 
있
습
니
다
.


#
 
*
*
1
5
.
 
C
o
n
f
u
s
i
o
n
 
m
a
t
r
i
x
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
5
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)






분
류
 
모
델
 
성
능
을
 
평
가
하
는
 
경
우
 
네
 
가
지
 
결
과
가
 
가
능
합
니
다
.
 
이
 
네
 
가
지
 
결
과
는
 
아
래
와
 
같
이
 
설
명
됩
니
다
.




T
r
u
e
 
P
o
s
i
t
i
v
e
s
 
(
T
P
)
 
-
 
T
r
u
e
 
P
o
s
i
t
i
v
e
s
는
 
관
측
치
가
 
특
정
 
클
래
스
에
 
속
할
 
것
으
로
 
예
측
하
고
,
 
관
측
치
가
 
실
제
로
 
그
 
클
래
스
에
 
속
한
 
경
우
입
니
다
.




T
r
u
e
 
N
e
g
a
t
i
v
e
s
 
(
T
N
)
 
-
 
T
r
u
e
 
N
e
g
a
t
i
v
e
s
는
 
관
측
치
가
 
특
정
 
클
래
스
에
 
속
하
지
 
않
을
 
것
으
로
 
예
측
하
고
,
 
관
측
치
가
 
실
제
로
 
그
 
클
래
스
에
 
속
하
지
 
않
는
 
경
우
입
니
다
.




F
a
l
s
e
 
P
o
s
i
t
i
v
e
s
 
(
F
P
)
 
-
 
F
a
l
s
e
 
P
o
s
i
t
i
v
e
s
는
 
관
측
치
가
 
특
정
 
클
래
스
에
 
속
할
 
것
으
로
 
예
측
하
지
만
,
 
관
측
치
가
 
실
제
로
 
그
 
클
래
스
에
 
속
하
지
 
않
은
 
경
우
입
니
다
.
 
이
러
한
 
유
형
의
 
오
류
를
 
T
y
p
e
 
I
 
오
류
라
고
 
합
니
다
.




F
a
l
s
e
 
N
e
g
a
t
i
v
e
s
 
(
F
N
)
 
-
 
F
a
l
s
e
 
N
e
g
a
t
i
v
e
s
는
 
관
측
치
가
 
특
정
 
클
래
스
에
 
속
하
지
 
않
을
 
것
으
로
 
예
측
하
지
만
,
 
관
측
치
가
 
실
제
로
 
그
 
클
래
스
에
 
속
하
는
 
경
우
입
니
다
.
 
이
는
 
매
우
 
심
각
한
 
오
류
이
며
 
T
y
p
e
 
I
I
 
오
류
라
고
 
합
니
다
.





```python
#
 
P
r
i
n
t
 
t
h
e
 
C
o
n
f
u
s
i
o
n
 
M
a
t
r
i
x
 
a
n
d
 
s
l
i
c
e
 
i
t
 
i
n
t
o
 
f
o
u
r
 
p
i
e
c
e
s


f
r
o
m
 
s
k
l
e
a
r
n
.
m
e
t
r
i
c
s
 
i
m
p
o
r
t
 
c
o
n
f
u
s
i
o
n
_
m
a
t
r
i
x


c
m
 
=
 
c
o
n
f
u
s
i
o
n
_
m
a
t
r
i
x
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
_
t
e
s
t
)


p
r
i
n
t
(
'
C
o
n
f
u
s
i
o
n
 
m
a
t
r
i
x
\
n
\
n
'
,
 
c
m
)


p
r
i
n
t
(
'
\
n
T
r
u
e
 
P
o
s
i
t
i
v
e
s
(
T
P
)
 
=
 
'
,
 
c
m
[
0
,
0
]
)


p
r
i
n
t
(
'
\
n
T
r
u
e
 
N
e
g
a
t
i
v
e
s
(
T
N
)
 
=
 
'
,
 
c
m
[
1
,
1
]
)


p
r
i
n
t
(
'
\
n
F
a
l
s
e
 
P
o
s
i
t
i
v
e
s
(
F
P
)
 
=
 
'
,
 
c
m
[
0
,
1
]
)


p
r
i
n
t
(
'
\
n
F
a
l
s
e
 
N
e
g
a
t
i
v
e
s
(
F
N
)
 
=
 
'
,
 
c
m
[
1
,
0
]
)
```

<pre>
C
o
n
f
u
s
i
o
n
 
m
a
t
r
i
x


 
[
[
2
1
5
4
3
 
 
1
1
8
3
]

 
[
 
3
2
2
7
 
 
3
1
3
9
]
]


T
r
u
e
 
P
o
s
i
t
i
v
e
s
(
T
P
)
 
=
 
 
2
1
5
4
3


T
r
u
e
 
N
e
g
a
t
i
v
e
s
(
T
N
)
 
=
 
 
3
1
3
9


F
a
l
s
e
 
P
o
s
i
t
i
v
e
s
(
F
P
)
 
=
 
 
1
1
8
3


F
a
l
s
e
 
N
e
g
a
t
i
v
e
s
(
F
N
)
 
=
 
 
3
2
2
7

</pre>
이
 
행
렬
에
서
 
`
2
0
8
9
2
 
+
 
3
2
8
5
 
=
 
2
4
1
7
7
 
c
o
r
r
e
c
t
 
p
r
e
d
i
c
t
i
o
n
s
`
 
와
 
`
3
0
8
7
 
+
 
1
1
7
5
 
=
 
4
2
6
2
 
i
n
c
o
r
r
e
c
t
 
p
r
e
d
i
c
t
i
o
n
s
`
임
을
 
알
 
수
 
있
습
니
다
.
.








-
 
`
T
r
u
e
 
P
o
s
i
t
i
v
e
s
`
 
(
A
c
t
u
a
l
 
P
o
s
i
t
i
v
e
:
1
 
a
n
d
 
P
r
e
d
i
c
t
 
P
o
s
i
t
i
v
e
:
1
)
 
-
 
2
0
8
9
2






-
 
`
T
r
u
e
 
N
e
g
a
t
i
v
e
s
`
 
(
A
c
t
u
a
l
 
N
e
g
a
t
i
v
e
:
0
 
a
n
d
 
P
r
e
d
i
c
t
 
N
e
g
a
t
i
v
e
:
0
)
 
-
 
3
2
8
5






-
 
`
F
a
l
s
e
 
P
o
s
i
t
i
v
e
s
`
 
(
A
c
t
u
a
l
 
N
e
g
a
t
i
v
e
:
0
 
b
u
t
 
P
r
e
d
i
c
t
 
P
o
s
i
t
i
v
e
:
1
)
 
-
 
1
1
7
5
 
`
(
T
y
p
e
 
I
 
e
r
r
o
r
)
`






-
 
`
F
a
l
s
e
 
N
e
g
a
t
i
v
e
s
`
 
(
A
c
t
u
a
l
 
P
o
s
i
t
i
v
e
:
1
 
b
u
t
 
P
r
e
d
i
c
t
 
N
e
g
a
t
i
v
e
:
0
)
 
-
 
3
0
8
7
 
`
(
T
y
p
e
 
I
I
 
e
r
r
o
r
)
`



```python
#
 
v
i
s
u
a
l
i
z
e
 
c
o
n
f
u
s
i
o
n
 
m
a
t
r
i
x
 
w
i
t
h
 
s
e
a
b
o
r
n
 
h
e
a
t
m
a
p


c
m
_
m
a
t
r
i
x
 
=
 
p
d
.
D
a
t
a
F
r
a
m
e
(
d
a
t
a
=
c
m
,
 
c
o
l
u
m
n
s
=
[
'
A
c
t
u
a
l
 
P
o
s
i
t
i
v
e
:
1
'
,
 
'
A
c
t
u
a
l
 
N
e
g
a
t
i
v
e
:
0
'
]
,
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
d
e
x
=
[
'
P
r
e
d
i
c
t
 
P
o
s
i
t
i
v
e
:
1
'
,
 
'
P
r
e
d
i
c
t
 
N
e
g
a
t
i
v
e
:
0
'
]
)


s
n
s
.
h
e
a
t
m
a
p
(
c
m
_
m
a
t
r
i
x
,
 
a
n
n
o
t
=
T
r
u
e
,
 
f
m
t
=
'
d
'
,
 
c
m
a
p
=
'
Y
l
G
n
B
u
'
)
```

<pre>
<
m
a
t
p
l
o
t
l
i
b
.
a
x
e
s
.
_
s
u
b
p
l
o
t
s
.
A
x
e
s
S
u
b
p
l
o
t
 
a
t
 
0
x
7
d
b
5
7
d
8
e
e
9
4
0
>
</pre>
<pre>
<
F
i
g
u
r
e
 
s
i
z
e
 
4
3
2
x
2
8
8
 
w
i
t
h
 
2
 
A
x
e
s
>
</pre>
#
 
*
*
1
6
.
 
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
m
e
t
r
i
c
e
s
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
6
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)


#
#
 
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
R
e
p
o
r
t






분
류
 
보
고
서
(
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
r
e
p
o
r
t
)
는
 
분
류
 
모
델
의
 
성
능
을
 
평
가
하
는
 
또
 
다
른
 
방
법
입
니
다
.
 
모
델
의
 
정
밀
도
,
 
재
현
율
,
 
f
1
-
s
c
o
r
e
 
및
 
지
원
도
 
점
수
를
 
표
시
합
니
다
.



```python
f
r
o
m
 
s
k
l
e
a
r
n
.
m
e
t
r
i
c
s
 
i
m
p
o
r
t
 
c
l
a
s
s
i
f
i
c
a
t
i
o
n
_
r
e
p
o
r
t


p
r
i
n
t
(
c
l
a
s
s
i
f
i
c
a
t
i
o
n
_
r
e
p
o
r
t
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
_
t
e
s
t
)
)
```

<pre>
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
r
e
c
i
s
i
o
n
 
 
 
 
r
e
c
a
l
l
 
 
f
1
-
s
c
o
r
e
 
 
 
s
u
p
p
o
r
t


 
 
 
 
 
 
 
 
 
 
 
0
 
 
 
 
 
 
 
0
.
8
7
 
 
 
 
 
 
0
.
9
5
 
 
 
 
 
 
0
.
9
1
 
 
 
 
 
2
2
7
2
6

 
 
 
 
 
 
 
 
 
 
 
1
 
 
 
 
 
 
 
0
.
7
3
 
 
 
 
 
 
0
.
4
9
 
 
 
 
 
 
0
.
5
9
 
 
 
 
 
 
6
3
6
6


 
 
 
 
a
c
c
u
r
a
c
y
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
8
5
 
 
 
 
 
2
9
0
9
2

 
 
 
m
a
c
r
o
 
a
v
g
 
 
 
 
 
 
 
0
.
8
0
 
 
 
 
 
 
0
.
7
2
 
 
 
 
 
 
0
.
7
5
 
 
 
 
 
2
9
0
9
2

w
e
i
g
h
t
e
d
 
a
v
g
 
 
 
 
 
 
 
0
.
8
4
 
 
 
 
 
 
0
.
8
5
 
 
 
 
 
 
0
.
8
4
 
 
 
 
 
2
9
0
9
2


</pre>
#
#
 
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
a
c
c
u
r
a
c
y



```python
T
P
 
=
 
c
m
[
0
,
0
]

T
N
 
=
 
c
m
[
1
,
1
]

F
P
 
=
 
c
m
[
0
,
1
]

F
N
 
=
 
c
m
[
1
,
0
]
```


```python
#
 
p
r
i
n
t
 
c
l
a
s
s
i
f
i
c
a
t
i
o
n
 
a
c
c
u
r
a
c
y


c
l
a
s
s
i
f
i
c
a
t
i
o
n
_
a
c
c
u
r
a
c
y
 
=
 
(
T
P
 
+
 
T
N
)
 
/
 
f
l
o
a
t
(
T
P
 
+
 
T
N
 
+
 
F
P
 
+
 
F
N
)


p
r
i
n
t
(
'
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
a
c
c
u
r
a
c
y
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
c
l
a
s
s
i
f
i
c
a
t
i
o
n
_
a
c
c
u
r
a
c
y
)
)

```

<pre>
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
a
c
c
u
r
a
c
y
 
:
 
0
.
8
4
8
4

</pre>
#
#
 
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
e
r
r
o
r



```python
#
 
p
r
i
n
t
 
c
l
a
s
s
i
f
i
c
a
t
i
o
n
 
e
r
r
o
r


c
l
a
s
s
i
f
i
c
a
t
i
o
n
_
e
r
r
o
r
 
=
 
(
F
P
 
+
 
F
N
)
 
/
 
f
l
o
a
t
(
T
P
 
+
 
T
N
 
+
 
F
P
 
+
 
F
N
)


p
r
i
n
t
(
'
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
e
r
r
o
r
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
c
l
a
s
s
i
f
i
c
a
t
i
o
n
_
e
r
r
o
r
)
)

```

<pre>
C
l
a
s
s
i
f
i
c
a
t
i
o
n
 
e
r
r
o
r
 
:
 
0
.
1
5
1
6

</pre>
#
#
 
P
r
e
c
i
s
i
o
n






*
*
정
밀
도
(
P
r
e
c
i
s
i
o
n
)
*
*
는
 
예
측
한
 
양
성
 
클
래
스
 
샘
플
 
중
 
실
제
 
양
성
 
클
래
스
 
샘
플
의
 
비
율
입
니
다
.
 
즉
,
 
참
 
양
성
(
T
P
)
 
샘
플
 
수
를
 
예
측
한
 
양
성
(
T
P
 
+
 
F
P
)
 
샘
플
 
수
로
 
나
눈
 
값
입
니
다
.




따
라
서
 
정
밀
도
는
 
양
성
 
클
래
스
보
다
는
 
음
성
 
클
래
스
보
다
 
더
 
관
심
이
 
있
는
 
결
과
입
니
다
.




수
학
적
으
로
는
 
정
밀
도
는
 
T
P
 
/
 
(
T
P
 
+
 
F
P
)
의
 
비
율
로
 
정
의
됩
니
다
.









```python
#
 
p
r
i
n
t
 
p
r
e
c
i
s
i
o
n
 
s
c
o
r
e


p
r
e
c
i
s
i
o
n
 
=
 
T
P
 
/
 
f
l
o
a
t
(
T
P
 
+
 
F
P
)



p
r
i
n
t
(
'
P
r
e
c
i
s
i
o
n
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
p
r
e
c
i
s
i
o
n
)
)

```

<pre>
P
r
e
c
i
s
i
o
n
 
:
 
0
.
9
4
7
9

</pre>
#
#
 
R
e
c
a
l
l






*
*
재
현
율
(
R
e
c
a
l
l
)
*
*
은
 
실
제
 
양
성
 
클
래
스
에
 
속
한
 
샘
플
 
중
에
서
 
정
확
하
게
 
예
측
된
 
샘
플
의
 
비
율
을
 
뜻
합
니
다
.




즉
,
 
T
P
(
T
r
u
e
 
P
o
s
i
t
i
v
e
)
의
 
비
율
로
 
정
의
할
 
수
 
있
으
며
,
 
진
짜
 
양
성
(
T
P
)
과
 
거
짓
 
음
성
(
F
N
)
의
 
합
인
 
(
T
P
 
+
 
F
N
)
으
로
 
나
눈
 
값
입
니
다
.




민
감
도
(
S
e
n
s
i
t
i
v
i
t
y
)
라
고
도
 
불
립
니
다
.











```python
r
e
c
a
l
l
 
=
 
T
P
 
/
 
f
l
o
a
t
(
T
P
 
+
 
F
N
)


p
r
i
n
t
(
'
R
e
c
a
l
l
 
o
r
 
S
e
n
s
i
t
i
v
i
t
y
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
r
e
c
a
l
l
)
)
```

<pre>
R
e
c
a
l
l
 
o
r
 
S
e
n
s
i
t
i
v
i
t
y
 
:
 
0
.
8
6
9
7

</pre>
#
#
 
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e






*
*
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
*
*
 
i
s
 
s
y
n
o
n
y
m
o
u
s
 
w
i
t
h
 
*
*
R
e
c
a
l
l
*
*
.





```python
t
r
u
e
_
p
o
s
i
t
i
v
e
_
r
a
t
e
 
=
 
T
P
 
/
 
f
l
o
a
t
(
T
P
 
+
 
F
N
)



p
r
i
n
t
(
'
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
t
r
u
e
_
p
o
s
i
t
i
v
e
_
r
a
t
e
)
)
```

<pre>
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
:
 
0
.
8
6
9
7

</pre>
#
#
 
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e



```python
f
a
l
s
e
_
p
o
s
i
t
i
v
e
_
r
a
t
e
 
=
 
F
P
 
/
 
f
l
o
a
t
(
F
P
 
+
 
T
N
)



p
r
i
n
t
(
'
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
f
a
l
s
e
_
p
o
s
i
t
i
v
e
_
r
a
t
e
)
)
```

<pre>
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
:
 
0
.
2
7
3
7

</pre>
#
#
 
S
p
e
c
i
f
i
c
i
t
y



```python
s
p
e
c
i
f
i
c
i
t
y
 
=
 
T
N
 
/
 
(
T
N
 
+
 
F
P
)


p
r
i
n
t
(
'
S
p
e
c
i
f
i
c
i
t
y
 
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
s
p
e
c
i
f
i
c
i
t
y
)
)
```

<pre>
S
p
e
c
i
f
i
c
i
t
y
 
:
 
0
.
7
2
6
3

</pre>
#
#
 
f
1
-
s
c
o
r
e






f
1
-
s
c
o
r
e
는
 
정
밀
도
와
 
재
현
율
의
 
가
중
 
조
화
 
평
균
입
니
다
.
 
최
적
의
 
f
1
-
s
c
o
r
e
는
 
1
.
0
이
고
,
 
최
악
은
 
0
.
0
입
니
다
.
 
f
1
-
s
c
o
r
e
는
 
정
밀
도
와
 
재
현
율
의
 
조
화
 
평
균
이
므
로
,
 
정
확
도
 
측
정
값
보
다
 
항
상
 
낮
습
니
다
.
 
가
중
치
 
평
균
 
f
1
-
s
c
o
r
e
를
 
사
용
하
여
 
분
류
 
모
델
을
 
비
교
해
야
 
하
며
,
 
전
체
적
인
 
정
확
도
 
측
정
값
보
다
 
유
용
합
니
다
.






#
#
 
S
u
p
p
o
r
t






S
u
p
p
o
r
t
는
 
데
이
터
셋
에
서
 
해
당
 
클
래
스
가
 
실
제
로
 
발
생
한
 
횟
수
를
 
의
미
합
니
다
.


#
 
*
*
1
7
.
 
A
d
j
u
s
t
i
n
g
 
t
h
e
 
t
h
r
e
s
h
o
l
d
 
l
e
v
e
l
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
7
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
#
 
p
r
i
n
t
 
t
h
e
 
f
i
r
s
t
 
1
0
 
p
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s
 
o
f
 
t
w
o
 
c
l
a
s
s
e
s
-
 
0
 
a
n
d
 
1


y
_
p
r
e
d
_
p
r
o
b
 
=
 
l
o
g
r
e
g
.
p
r
e
d
i
c
t
_
p
r
o
b
a
(
X
_
t
e
s
t
)
[
0
:
1
0
]


y
_
p
r
e
d
_
p
r
o
b
```

<pre>
a
r
r
a
y
(
[
[
0
.
8
3
2
1
8
0
1
2
,
 
0
.
1
6
7
8
1
9
8
8
]
,

 
 
 
 
 
 
 
[
0
.
7
4
5
4
7
8
9
7
,
 
0
.
2
5
4
5
2
1
0
3
]
,

 
 
 
 
 
 
 
[
0
.
7
9
8
6
4
8
9
9
,
 
0
.
2
0
1
3
5
1
0
1
]
,

 
 
 
 
 
 
 
[
0
.
5
8
5
0
9
2
1
3
,
 
0
.
4
1
4
9
0
7
8
7
]
,

 
 
 
 
 
 
 
[
0
.
9
2
1
6
5
7
8
4
,
 
0
.
0
7
8
3
4
2
1
6
]
,

 
 
 
 
 
 
 
[
0
.
9
5
6
2
5
8
7
9
,
 
0
.
0
4
3
7
4
1
2
1
]
,

 
 
 
 
 
 
 
[
0
.
5
7
8
8
1
8
8
8
,
 
0
.
4
2
1
1
8
1
1
2
]
,

 
 
 
 
 
 
 
[
0
.
5
0
2
9
3
9
1
6
,
 
0
.
4
9
7
0
6
0
8
4
]
,

 
 
 
 
 
 
 
[
0
.
8
0
2
8
1
9
4
3
,
 
0
.
1
9
7
1
8
0
5
7
]
,

 
 
 
 
 
 
 
[
0
.
7
2
3
4
0
9
4
6
,
 
0
.
2
7
6
5
9
0
5
4
]
]
)
</pre>
#
#
#
 
O
b
s
e
r
v
a
t
i
o
n
s






-
 
각
 
행
마
다
의
 
숫
자
들
은
 
1
로
 
합
쳐
집
니
다
.


-
 
2
개
의
 
열
은
 
0
과
 
1
의
 
2
개
의
 
클
래
스
를
 
나
타
냅
니
다
.




 
 
 
 
-
 
클
래
스
 
0
 
-
 
내
일
 
비
가
 
오
지
 
않
을
 
확
률
에
 
대
한
 
예
측
 
확
률
입
니
다
.




 
 
 
 
-
 
클
래
스
 
1
 
-
 
내
일
 
비
가
 
올
 
확
률
에
 
대
한
 
예
측
 
확
률
입
니
다
.




-
 
예
측
된
 
확
률
의
 
중
요
성




 
 
 
 
-
 
우
리
는
 
비
가
 
올
 
확
률
이
나
 
오
지
 
않
을
 
확
률
에
 
따
라
 
데
이
터
를
 
순
위
대
로
 
나
열
할
 
수
 
있
습
니
다
.




-
 
p
r
e
d
i
c
t
_
p
r
o
b
a
 
과
정




 
 
 
 
-
 
확
률
을
 
예
측
합
니
다
.




 
 
 
 
-
 
가
장
 
높
은
 
확
률
의
 
클
래
스
를
 
선
택
합
니
다
.




-
 
분
류
 
임
계
값




 
 
 
 
-
 
분
류
 
임
계
값
은
 
0
.
5
입
니
다
.




 
 
 
 
-
 
클
래
스
 
1
 
-
 
확
률
이
 
0
.
5
보
다
 
크
면
 
비
가
 
올
 
확
률
로
 
예
측
됩
니
다
.




 
 
 
 
-
 
클
래
스
 
0
 
-
 
확
률
이
 
0
.
5
보
다
 
작
으
면
 
비
가
 
오
지
 
않
을
 
확
률
로
 
예
측
됩
니
다
.
 
 


 
 
 
 





```python
#
 
s
t
o
r
e
 
t
h
e
 
p
r
o
b
a
b
i
l
i
t
i
e
s
 
i
n
 
d
a
t
a
f
r
a
m
e


y
_
p
r
e
d
_
p
r
o
b
_
d
f
 
=
 
p
d
.
D
a
t
a
F
r
a
m
e
(
d
a
t
a
=
y
_
p
r
e
d
_
p
r
o
b
,
 
c
o
l
u
m
n
s
=
[
'
P
r
o
b
 
o
f
 
-
 
N
o
 
r
a
i
n
 
t
o
m
o
r
r
o
w
 
(
0
)
'
,
 
'
P
r
o
b
 
o
f
 
-
 
R
a
i
n
 
t
o
m
o
r
r
o
w
 
(
1
)
'
]
)


y
_
p
r
e
d
_
p
r
o
b
_
d
f
```

<pre>
 
 
 
P
r
o
b
 
o
f
 
-
 
N
o
 
r
a
i
n
 
t
o
m
o
r
r
o
w
 
(
0
)
 
 
P
r
o
b
 
o
f
 
-
 
R
a
i
n
 
t
o
m
o
r
r
o
w
 
(
1
)

0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
8
3
2
1
8
0
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
1
6
7
8
2
0

1
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
7
4
5
4
7
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
2
5
4
5
2
1

2
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
7
9
8
6
4
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
2
0
1
3
5
1

3
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
5
8
5
0
9
2
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
4
1
4
9
0
8

4
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
9
2
1
6
5
8
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
7
8
3
4
2

5
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
9
5
6
2
5
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
0
4
3
7
4
1

6
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
5
7
8
8
1
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
4
2
1
1
8
1

7
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
5
0
2
9
3
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
4
9
7
0
6
1

8
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
8
0
2
8
1
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
1
9
7
1
8
1

9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
7
2
3
4
0
9
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
0
.
2
7
6
5
9
1
</pre>

```python
#
 
p
r
i
n
t
 
t
h
e
 
f
i
r
s
t
 
1
0
 
p
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s
 
f
o
r
 
c
l
a
s
s
 
1
 
-
 
P
r
o
b
a
b
i
l
i
t
y
 
o
f
 
r
a
i
n


l
o
g
r
e
g
.
p
r
e
d
i
c
t
_
p
r
o
b
a
(
X
_
t
e
s
t
)
[
0
:
1
0
,
 
1
]
```

<pre>
a
r
r
a
y
(
[
0
.
1
6
7
8
1
9
8
8
,
 
0
.
2
5
4
5
2
1
0
3
,
 
0
.
2
0
1
3
5
1
0
1
,
 
0
.
4
1
4
9
0
7
8
7
,
 
0
.
0
7
8
3
4
2
1
6
,

 
 
 
 
 
 
 
0
.
0
4
3
7
4
1
2
1
,
 
0
.
4
2
1
1
8
1
1
2
,
 
0
.
4
9
7
0
6
0
8
4
,
 
0
.
1
9
7
1
8
0
5
7
,
 
0
.
2
7
6
5
9
0
5
4
]
)
</pre>

```python
#
 
s
t
o
r
e
 
t
h
e
 
p
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s
 
f
o
r
 
c
l
a
s
s
 
1
 
-
 
P
r
o
b
a
b
i
l
i
t
y
 
o
f
 
r
a
i
n


y
_
p
r
e
d
1
 
=
 
l
o
g
r
e
g
.
p
r
e
d
i
c
t
_
p
r
o
b
a
(
X
_
t
e
s
t
)
[
:
,
 
1
]
```


```python
#
 
p
l
o
t
 
h
i
s
t
o
g
r
a
m
 
o
f
 
p
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s



#
 
a
d
j
u
s
t
 
t
h
e
 
f
o
n
t
 
s
i
z
e
 

p
l
t
.
r
c
P
a
r
a
m
s
[
'
f
o
n
t
.
s
i
z
e
'
]
 
=
 
1
2



#
 
p
l
o
t
 
h
i
s
t
o
g
r
a
m
 
w
i
t
h
 
1
0
 
b
i
n
s

p
l
t
.
h
i
s
t
(
y
_
p
r
e
d
1
,
 
b
i
n
s
 
=
 
1
0
)



#
 
s
e
t
 
t
h
e
 
t
i
t
l
e
 
o
f
 
p
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s

p
l
t
.
t
i
t
l
e
(
'
H
i
s
t
o
g
r
a
m
 
o
f
 
p
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s
 
o
f
 
r
a
i
n
'
)



#
 
s
e
t
 
t
h
e
 
x
-
a
x
i
s
 
l
i
m
i
t

p
l
t
.
x
l
i
m
(
0
,
1
)



#
 
s
e
t
 
t
h
e
 
t
i
t
l
e

p
l
t
.
x
l
a
b
e
l
(
'
P
r
e
d
i
c
t
e
d
 
p
r
o
b
a
b
i
l
i
t
i
e
s
 
o
f
 
r
a
i
n
'
)

p
l
t
.
y
l
a
b
e
l
(
'
F
r
e
q
u
e
n
c
y
'
)
```

<pre>
T
e
x
t
(
0
,
 
0
.
5
,
 
'
F
r
e
q
u
e
n
c
y
'
)
</pre>
<pre>
<
F
i
g
u
r
e
 
s
i
z
e
 
4
3
2
x
2
8
8
 
w
i
t
h
 
1
 
A
x
e
s
>
</pre>
#
#
#
 
O
b
s
e
r
v
a
t
i
o
n
s






-
 
위
의
 
히
스
토
그
램
은
 
매
우
 
양
의
 
왜
도
(
s
k
e
w
e
d
)
를
 
가
진
 
것
으
로
 
나
타
납
니
다
.


-
 
첫
 
번
째
 
열
은
 
약
 
0
.
0
에
서
 
0
.
1
 
사
이
의
 
확
률
을
 
가
진
 
약
 
1
5
,
0
0
0
개
의
 
관
측
치
가
 
있
음
을
 
알
려
줍
니
다
.


-
 
확
률
이
 
0
.
5
보
다
 
큰
 
작
은
 
수
의
 
관
측
치
가
 
있
습
니
다
.


-
 
따
라
서
 
이
 
작
은
 
수
의
 
관
측
치
는
 
내
일
 
비
가
 
올
 
것
이
라
고
 
예
측
합
니
다
.


-
 
대
다
수
의
 
관
측
치
는
 
내
일
 
비
가
 
오
지
 
않
을
 
것
으
로
 
예
측
합
니
다
.


#
#
#
 
L
o
w
e
r
 
t
h
e
 
t
h
r
e
s
h
o
l
d


아
래
 
코
드
는
 
이
론
상
 
옳
지
만
 
필
자
도
 
알
 
수
 
없
는
 
이
유
로
 
오
류
가
 
발
생
하
여
 
주
석
 
처
리
합
니
다
.




예
측
컨
데
 
y
_
t
e
s
t
에
서
 
오
류
가
 
발
생
했
을
 
것
이
지
만
 
과
정
이
 
너
무
 
복
잡
할
 
것
 
같
아
서
 
이
후
에
 
처
리
하
도
록
 
합
니
다
.



```python
#
 
f
r
o
m
 
s
k
l
e
a
r
n
.
p
r
e
p
r
o
c
e
s
s
i
n
g
 
i
m
p
o
r
t
 
L
a
b
e
l
E
n
c
o
d
e
r


#
 
#
 
L
a
b
e
l
E
n
c
o
d
e
r
를
 
사
용
하
여
 
y
_
t
r
a
i
n
과
 
y
_
t
e
s
t
 
레
이
블
을
 
숫
자
형
으
로
 
변
환

#
 
l
e
 
=
 
L
a
b
e
l
E
n
c
o
d
e
r
(
)

#
 
y
_
t
r
a
i
n
 
=
 
l
e
.
f
i
t
_
t
r
a
n
s
f
o
r
m
(
y
_
t
r
a
i
n
[
'
e
n
c
'
]
)

#
 
y
_
t
e
s
t
 
=
 
l
e
.
t
r
a
n
s
f
o
r
m
(
y
_
t
e
s
t
[
'
e
n
c
'
]
)


#
 
f
o
r
 
i
 
i
n
 
r
a
n
g
e
(
1
,
5
)
:

 
 
 
 

#
 
 
 
 
 
c
m
1
=
0

 
 
 
 

#
 
 
 
 
 
y
_
p
r
e
d
1
 
=
 
l
o
g
r
e
g
.
p
r
e
d
i
c
t
_
p
r
o
b
a
(
X
_
t
e
s
t
)
[
:
,
1
]

 
 
 
 

#
 
 
 
 
 
y
_
p
r
e
d
1
 
=
 
y
_
p
r
e
d
1
.
r
e
s
h
a
p
e
(
-
1
,
1
)

 
 
 
 

#
 
 
 
 
 
y
_
p
r
e
d
2
 
=
 
b
i
n
a
r
i
z
e
(
y
_
p
r
e
d
1
,
 
i
/
1
0
)

 
 
 
 

#
 
 
 
 
 
y
_
p
r
e
d
2
 
=
 
n
p
.
w
h
e
r
e
(
y
_
p
r
e
d
2
 
=
=
 
1
,
 
'
Y
e
s
'
,
 
'
N
o
'
)

 
 
 
 

#
 
 
 
 
 
c
m
1
 
=
 
c
o
n
f
u
s
i
o
n
_
m
a
t
r
i
x
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
2
)

 
 
 
 
 
 
 
 

#
 
 
 
 
 
p
r
i
n
t
 
(
'
W
i
t
h
'
,
i
/
1
0
,
'
t
h
r
e
s
h
o
l
d
 
t
h
e
 
C
o
n
f
u
s
i
o
n
 
M
a
t
r
i
x
 
i
s
 
'
,
'
\
n
\
n
'
,
c
m
1
,
'
\
n
\
n
'
,

 
 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
 
'
w
i
t
h
'
,
c
m
1
[
0
,
0
]
+
c
m
1
[
1
,
1
]
,
'
c
o
r
r
e
c
t
 
p
r
e
d
i
c
t
i
o
n
s
,
 
'
,
 
'
\
n
\
n
'
,
 

 
 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
 
c
m
1
[
0
,
1
]
,
'
T
y
p
e
 
I
 
e
r
r
o
r
s
(
 
F
a
l
s
e
 
P
o
s
i
t
i
v
e
s
)
,
 
'
,
'
\
n
\
n
'
,

 
 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
 
c
m
1
[
1
,
0
]
,
'
T
y
p
e
 
I
I
 
e
r
r
o
r
s
(
 
F
a
l
s
e
 
N
e
g
a
t
i
v
e
s
)
,
 
'
,
'
\
n
\
n
'
,

 
 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
'
A
c
c
u
r
a
c
y
 
s
c
o
r
e
:
 
'
,
 
(
a
c
c
u
r
a
c
y
_
s
c
o
r
e
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
2
)
)
,
 
'
\
n
\
n
'
,

 
 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
'
S
e
n
s
i
t
i
v
i
t
y
:
 
'
,
c
m
1
[
1
,
1
]
/
(
f
l
o
a
t
(
c
m
1
[
1
,
1
]
+
c
m
1
[
1
,
0
]
)
)
,
 
'
\
n
\
n
'
,

 
 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
'
S
p
e
c
i
f
i
c
i
t
y
:
 
'
,
c
m
1
[
0
,
0
]
/
(
f
l
o
a
t
(
c
m
1
[
0
,
0
]
+
c
m
1
[
0
,
1
]
)
)
,
'
\
n
\
n
'
,

 
 
 
 
 
 
 
 
 
 

#
 
 
 
 
 
 
 
 
 
 
 
 
 
'
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
=
'
,
 
'
\
n
\
n
'
)
```

#
#
#
 
C
o
m
m
e
n
t
s






-
 
이
진
 
분
류
 
문
제
에
서
는
,
 
예
측
된
 
확
률
을
 
클
래
스
 
예
측
으
로
 
변
환
하
기
 
위
해
 
기
본
적
으
로
 
0
.
5
의
 
임
계
값
이
 
사
용
됩
니
다
.


-
 
임
계
값
은
 
민
감
도
 
또
는
 
특
이
도
를
 
높
이
기
 
위
해
 
조
정
될
 
수
 
있
습
니
다
.


-
 
민
감
도
와
 
특
이
도
는
 
서
로
 
역
관
계
를
 
가
집
니
다
.
 
한
 
쪽
을
 
높
이
면
 
다
른
 
쪽
은
 
반
드
시
 
낮
아
집
니
다
.


-
 
임
계
값
을
 
높
이
면
 
정
확
도
가
 
증
가
하
는
 
것
을
 
확
인
할
 
수
 
있
습
니
다
.


-
 
임
계
값
을
 
조
정
하
는
 
것
은
 
모
델
 
구
축
 
과
정
에
서
 
마
지
막
 
단
계
 
중
 
하
나
여
야
 
합
니
다
.


#
 
*
*
1
8
.
 
R
O
C
 
-
 
A
U
C
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
8
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)








#
#
 
R
O
C
 
C
u
r
v
e






분
류
 
모
델
의
 
성
능
을
 
시
각
적
으
로
 
측
정
하
는
 
또
 
다
른
 
도
구
는
 
R
O
C
 
C
u
r
v
e
입
니
다
.
 
R
O
C
 
C
u
r
v
e
는
 
R
e
c
e
i
v
e
r
 
O
p
e
r
a
t
i
n
g
 
C
h
a
r
a
c
t
e
r
i
s
t
i
c
 
C
u
r
v
e
의
 
약
자
로
,
 
다
양
한
 
분
류
 
임
계
값
에
서
 
분
류
 
모
델
의
 
성
능
을
 
보
여
주
는
 
그
래
프
입
니
다
.




R
O
C
 
C
u
r
v
e
는
 
다
양
한
 
임
계
값
에
서
 
*
*
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
(
T
P
R
)
*
*
와
 
*
*
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
(
F
P
R
)
*
*
를
 
플
롯
합
니
다
.




*
*
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
(
T
P
R
)
*
*
는
 
R
e
c
a
l
l
이
라
고
도
하
며
,
 
T
P
 
/
 
(
T
P
 
+
 
F
N
)
의
 
비
율
로
 
정
의
됩
니
다
.




*
*
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
(
F
P
R
)
*
*
는
 
F
P
 
/
 
(
F
P
 
+
 
T
N
)
의
 
비
율
로
 
정
의
됩
니
다
.




R
O
C
 
C
u
r
v
e
에
서
는
 
하
나
의
 
지
점
의
 
T
P
R
 
(
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
)
과
 
F
P
R
 
(
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
)
에
 
초
점
을
 
맞
춥
니
다
.
 
이
는
 
다
양
한
 
임
계
값
에
서
 
T
P
R
과
 
F
P
R
로
 
구
성
된
 
R
O
C
 
C
u
r
v
e
의
 
일
반
적
인
 
성
능
을
 
제
공
합
니
다
.
 
따
라
서
 
R
O
C
 
C
u
r
v
e
는
 
다
른
 
분
류
 
임
계
값
에
서
 
T
P
R
 
대
 
F
P
R
을
 
플
롯
합
니
다
.
 
임
계
값
을
 
낮
추
면
 
더
 
많
은
 
항
목
이
 
긍
정
으
로
 
분
류
될
 
수
 
있
습
니
다
.
 
이
는
 
T
r
u
e
 
P
o
s
i
t
i
v
e
 
(
T
P
)
와
 
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
(
F
P
)
 
모
두
를
 
증
가
시
킵
니
다
.






위
와
 
같
은
 
이
유
로
 
y
_
t
e
s
t
에
 
문
제
가
 
생
겨
 
곡
선
이
 
그
려
지
지
 
않
으
므
로
 
이
또
한
 
주
석
처
리
하
고
 
개
념
만
 
정
리
합
니
다
.



```python
#
 
#
 
p
l
o
t
 
R
O
C
 
C
u
r
v
e


#
 
f
r
o
m
 
s
k
l
e
a
r
n
.
m
e
t
r
i
c
s
 
i
m
p
o
r
t
 
r
o
c
_
c
u
r
v
e


#
 
f
p
r
,
 
t
p
r
,
 
t
h
r
e
s
h
o
l
d
s
 
=
 
r
o
c
_
c
u
r
v
e
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
1
,
 
p
o
s
_
l
a
b
e
l
 
=
 
'
Y
e
s
'
)


#
 
p
l
t
.
f
i
g
u
r
e
(
f
i
g
s
i
z
e
=
(
6
,
4
)
)


#
 
p
l
t
.
p
l
o
t
(
f
p
r
,
 
t
p
r
,
 
l
i
n
e
w
i
d
t
h
=
2
)


#
 
p
l
t
.
p
l
o
t
(
[
0
,
1
]
,
 
[
0
,
1
]
,
 
'
k
-
-
'
 
)


#
 
p
l
t
.
r
c
P
a
r
a
m
s
[
'
f
o
n
t
.
s
i
z
e
'
]
 
=
 
1
2


#
 
p
l
t
.
t
i
t
l
e
(
'
R
O
C
 
c
u
r
v
e
 
f
o
r
 
R
a
i
n
T
o
m
o
r
r
o
w
 
c
l
a
s
s
i
f
i
e
r
'
)


#
 
p
l
t
.
x
l
a
b
e
l
(
'
F
a
l
s
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
(
1
 
-
 
S
p
e
c
i
f
i
c
i
t
y
)
'
)


#
 
p
l
t
.
y
l
a
b
e
l
(
'
T
r
u
e
 
P
o
s
i
t
i
v
e
 
R
a
t
e
 
(
S
e
n
s
i
t
i
v
i
t
y
)
'
)


#
 
p
l
t
.
s
h
o
w
(
)

```

R
O
C
 
곡
선
은
 
특
정
 
맥
락
에
서
 
민
감
도
와
 
특
이
도
를
 
균
형
있
게
 
조
절
하
는
 
임
계
값
을
 
선
택
하
는
 
데
 
도
움
을
 
줍
니
다
.


#
#
 
R
O
C
-
A
U
C






*
*
R
O
C
 
A
U
C
*
*
는
 
R
e
c
e
i
v
e
r
 
O
p
e
r
a
t
i
n
g
 
C
h
a
r
a
c
t
e
r
i
s
t
i
c
 
-
 
A
r
e
a
 
U
n
d
e
r
 
C
u
r
v
e
의
 
약
어
로
,
 
분
류
 
모
델
의
 
성
능
을
 
비
교
하
는
 
기
술
입
니
다
.
 
이
 
기
술
에
서
는
 
곡
선
 
아
래
 
면
적
 
(
A
U
C
)
을
 
측
정
합
니
다
.
 
완
벽
한
 
분
류
 
모
델
은
 
R
O
C
 
A
U
C
가
 
1
이
 
되
고
,
 
완
전
한
 
랜
덤
 
분
류
 
모
델
은
 
R
O
C
 
A
U
C
가
 
0
.
5
가
 
됩
니
다
.




따
라
서
 
R
O
C
 
A
U
C
는
 
R
O
C
 
그
래
프
에
서
 
곡
선
 
아
래
에
 
있
는
 
영
역
의
 
백
분
율
입
니
다
.



```python
#
 
c
o
m
p
u
t
e
 
R
O
C
 
A
U
C


f
r
o
m
 
s
k
l
e
a
r
n
.
m
e
t
r
i
c
s
 
i
m
p
o
r
t
 
r
o
c
_
a
u
c
_
s
c
o
r
e


R
O
C
_
A
U
C
 
=
 
r
o
c
_
a
u
c
_
s
c
o
r
e
(
y
_
t
e
s
t
,
 
y
_
p
r
e
d
1
)


p
r
i
n
t
(
'
R
O
C
 
A
U
C
 
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
R
O
C
_
A
U
C
)
)
```

<pre>
R
O
C
 
A
U
C
 
:
 
0
.
8
6
7
1

</pre>
#
#
#
 
C
o
m
m
e
n
t
s






-
 
R
O
C
 
A
U
C
는
 
분
류
기
의
 
성
능
을
 
나
타
내
는
 
단
일
 
숫
자
 
요
약
값
입
니
다
.
 
값
이
 
높
을
수
록
 
분
류
기
의
 
성
능
이
 
좋
습
니
다
.




-
 
우
리
 
모
델
의
 
R
O
C
 
A
U
C
 
값
이
 
1
에
 
가
까
워
지
므
로
,
 
우
리
의
 
분
류
기
가
 
내
일
 
비
가
 
올
지
 
여
부
를
 
예
측
하
는
 
데
에
 
잘
 
작
동
한
다
는
 
결
론
을
 
내
릴
 
수
 
있
습
니
다
.



```python
#
 
c
a
l
c
u
l
a
t
e
 
c
r
o
s
s
-
v
a
l
i
d
a
t
e
d
 
R
O
C
 
A
U
C
 


f
r
o
m
 
s
k
l
e
a
r
n
.
m
o
d
e
l
_
s
e
l
e
c
t
i
o
n
 
i
m
p
o
r
t
 
c
r
o
s
s
_
v
a
l
_
s
c
o
r
e


C
r
o
s
s
_
v
a
l
i
d
a
t
e
d
_
R
O
C
_
A
U
C
 
=
 
c
r
o
s
s
_
v
a
l
_
s
c
o
r
e
(
l
o
g
r
e
g
,
 
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
,
 
c
v
=
5
,
 
s
c
o
r
i
n
g
=
'
r
o
c
_
a
u
c
'
)
.
m
e
a
n
(
)


p
r
i
n
t
(
'
C
r
o
s
s
 
v
a
l
i
d
a
t
e
d
 
R
O
C
 
A
U
C
 
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
C
r
o
s
s
_
v
a
l
i
d
a
t
e
d
_
R
O
C
_
A
U
C
)
)
```

<pre>
C
r
o
s
s
 
v
a
l
i
d
a
t
e
d
 
R
O
C
 
A
U
C
 
:
 
0
.
8
6
7
5

</pre>
#
 
*
*
1
9
.
 
k
-
F
o
l
d
 
C
r
o
s
s
 
V
a
l
i
d
a
t
i
o
n
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
1
9
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
#
 
A
p
p
l
y
i
n
g
 
5
-
F
o
l
d
 
C
r
o
s
s
 
V
a
l
i
d
a
t
i
o
n


f
r
o
m
 
s
k
l
e
a
r
n
.
m
o
d
e
l
_
s
e
l
e
c
t
i
o
n
 
i
m
p
o
r
t
 
c
r
o
s
s
_
v
a
l
_
s
c
o
r
e


s
c
o
r
e
s
 
=
 
c
r
o
s
s
_
v
a
l
_
s
c
o
r
e
(
l
o
g
r
e
g
,
 
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
,
 
c
v
 
=
 
5
,
 
s
c
o
r
i
n
g
=
'
a
c
c
u
r
a
c
y
'
)


p
r
i
n
t
(
'
C
r
o
s
s
-
v
a
l
i
d
a
t
i
o
n
 
s
c
o
r
e
s
:
{
}
'
.
f
o
r
m
a
t
(
s
c
o
r
e
s
)
)
```

<pre>
C
r
o
s
s
-
v
a
l
i
d
a
t
i
o
n
 
s
c
o
r
e
s
:
[
0
.
8
4
8
0
3
4
3
7
 
0
.
8
4
9
3
5
9
8
 
 
0
.
8
4
9
3
9
6
3
 
 
0
.
8
4
5
0
1
3
5
3
 
0
.
8
4
8
7
9
4
7
4
]

</pre>
교
차
 
검
증
 
정
확
도
를
 
요
약
하
기
 
위
해
 
평
균
을
 
계
산
할
 
수
 
있
습
니
다
.



```python
#
 
c
o
m
p
u
t
e
 
A
v
e
r
a
g
e
 
c
r
o
s
s
-
v
a
l
i
d
a
t
i
o
n
 
s
c
o
r
e


p
r
i
n
t
(
'
A
v
e
r
a
g
e
 
c
r
o
s
s
-
v
a
l
i
d
a
t
i
o
n
 
s
c
o
r
e
:
 
{
:
.
4
f
}
'
.
f
o
r
m
a
t
(
s
c
o
r
e
s
.
m
e
a
n
(
)
)
)
```

<pre>
A
v
e
r
a
g
e
 
c
r
o
s
s
-
v
a
l
i
d
a
t
i
o
n
 
s
c
o
r
e
:
 
0
.
8
4
8
1

</pre>
우
리
의
 
원
래
 
모
델
 
점
수
는
 
0
.
8
4
7
6
입
니
다
.
 
평
균
 
교
차
 
검
증
 
점
수
는
 
0
.
8
4
7
4
입
니
다
.
 
따
라
서
 
교
차
 
검
증
은
 
성
능
 
향
상
을
 
가
져
오
지
 
않
는
다
고
 
결
론
 
짓
을
 
수
 
있
습
니
다
.


#
 
*
*
2
0
.
 
H
y
p
e
r
p
a
r
a
m
e
t
e
r
 
O
p
t
i
m
i
z
a
t
i
o
n
 
u
s
i
n
g
 
G
r
i
d
S
e
a
r
c
h
 
C
V
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
2
0
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)



```python
f
r
o
m
 
s
k
l
e
a
r
n
.
m
o
d
e
l
_
s
e
l
e
c
t
i
o
n
 
i
m
p
o
r
t
 
G
r
i
d
S
e
a
r
c
h
C
V



p
a
r
a
m
e
t
e
r
s
 
=
 
[
{
'
p
e
n
a
l
t
y
'
:
[
'
l
1
'
,
'
l
2
'
]
}
,
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
{
'
C
'
:
[
1
,
 
1
0
,
 
1
0
0
,
 
1
0
0
0
]
}
]




g
r
i
d
_
s
e
a
r
c
h
 
=
 
G
r
i
d
S
e
a
r
c
h
C
V
(
e
s
t
i
m
a
t
o
r
 
=
 
l
o
g
r
e
g
,
 
 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
p
a
r
a
m
_
g
r
i
d
 
=
 
p
a
r
a
m
e
t
e
r
s
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
s
c
o
r
i
n
g
 
=
 
'
a
c
c
u
r
a
c
y
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
c
v
 
=
 
5
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
v
e
r
b
o
s
e
=
0
)



g
r
i
d
_
s
e
a
r
c
h
.
f
i
t
(
X
_
t
r
a
i
n
,
 
y
_
t
r
a
i
n
)

```

<pre>
G
r
i
d
S
e
a
r
c
h
C
V
(
c
v
=
5
,
 
e
r
r
o
r
_
s
c
o
r
e
=
'
r
a
i
s
e
-
d
e
p
r
e
c
a
t
i
n
g
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
e
s
t
i
m
a
t
o
r
=
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
1
.
0
,
 
c
l
a
s
s
_
w
e
i
g
h
t
=
N
o
n
e
,
 
d
u
a
l
=
F
a
l
s
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
f
i
t
_
i
n
t
e
r
c
e
p
t
=
T
r
u
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
e
r
c
e
p
t
_
s
c
a
l
i
n
g
=
1
,
 
l
1
_
r
a
t
i
o
=
N
o
n
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
m
a
x
_
i
t
e
r
=
1
0
0
,
 
m
u
l
t
i
_
c
l
a
s
s
=
'
w
a
r
n
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
n
_
j
o
b
s
=
N
o
n
e
,
 
p
e
n
a
l
t
y
=
'
l
2
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
t
o
l
=
0
.
0
0
0
1
,
 
v
e
r
b
o
s
e
=
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
w
a
r
m
_
s
t
a
r
t
=
F
a
l
s
e
)
,

 
 
 
 
 
 
 
 
 
 
 
 
 
i
i
d
=
'
w
a
r
n
'
,
 
n
_
j
o
b
s
=
N
o
n
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
p
a
r
a
m
_
g
r
i
d
=
[
{
'
p
e
n
a
l
t
y
'
:
 
[
'
l
1
'
,
 
'
l
2
'
]
}
,
 
{
'
C
'
:
 
[
1
,
 
1
0
,
 
1
0
0
,
 
1
0
0
0
]
}
]
,

 
 
 
 
 
 
 
 
 
 
 
 
 
p
r
e
_
d
i
s
p
a
t
c
h
=
'
2
*
n
_
j
o
b
s
'
,
 
r
e
f
i
t
=
T
r
u
e
,
 
r
e
t
u
r
n
_
t
r
a
i
n
_
s
c
o
r
e
=
F
a
l
s
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
s
c
o
r
i
n
g
=
'
a
c
c
u
r
a
c
y
'
,
 
v
e
r
b
o
s
e
=
0
)
</pre>

```python
#
 
e
x
a
m
i
n
e
 
t
h
e
 
b
e
s
t
 
m
o
d
e
l


#
 
b
e
s
t
 
s
c
o
r
e
 
a
c
h
i
e
v
e
d
 
d
u
r
i
n
g
 
t
h
e
 
G
r
i
d
S
e
a
r
c
h
C
V

p
r
i
n
t
(
'
G
r
i
d
S
e
a
r
c
h
 
C
V
 
b
e
s
t
 
s
c
o
r
e
 
:
 
{
:
.
4
f
}
\
n
\
n
'
.
f
o
r
m
a
t
(
g
r
i
d
_
s
e
a
r
c
h
.
b
e
s
t
_
s
c
o
r
e
_
)
)


#
 
p
r
i
n
t
 
p
a
r
a
m
e
t
e
r
s
 
t
h
a
t
 
g
i
v
e
 
t
h
e
 
b
e
s
t
 
r
e
s
u
l
t
s

p
r
i
n
t
(
'
P
a
r
a
m
e
t
e
r
s
 
t
h
a
t
 
g
i
v
e
 
t
h
e
 
b
e
s
t
 
r
e
s
u
l
t
s
 
:
'
,
'
\
n
\
n
'
,
 
(
g
r
i
d
_
s
e
a
r
c
h
.
b
e
s
t
_
p
a
r
a
m
s
_
)
)


#
 
p
r
i
n
t
 
e
s
t
i
m
a
t
o
r
 
t
h
a
t
 
w
a
s
 
c
h
o
s
e
n
 
b
y
 
t
h
e
 
G
r
i
d
S
e
a
r
c
h

p
r
i
n
t
(
'
\
n
\
n
E
s
t
i
m
a
t
o
r
 
t
h
a
t
 
w
a
s
 
c
h
o
s
e
n
 
b
y
 
t
h
e
 
s
e
a
r
c
h
 
:
'
,
'
\
n
\
n
'
,
 
(
g
r
i
d
_
s
e
a
r
c
h
.
b
e
s
t
_
e
s
t
i
m
a
t
o
r
_
)
)
```

<pre>
G
r
i
d
S
e
a
r
c
h
 
C
V
 
b
e
s
t
 
s
c
o
r
e
 
:
 
0
.
8
4
8
3



P
a
r
a
m
e
t
e
r
s
 
t
h
a
t
 
g
i
v
e
 
t
h
e
 
b
e
s
t
 
r
e
s
u
l
t
s
 
:
 


 
{
'
p
e
n
a
l
t
y
'
:
 
'
l
1
'
}



E
s
t
i
m
a
t
o
r
 
t
h
a
t
 
w
a
s
 
c
h
o
s
e
n
 
b
y
 
t
h
e
 
s
e
a
r
c
h
 
:
 


 
L
o
g
i
s
t
i
c
R
e
g
r
e
s
s
i
o
n
(
C
=
1
.
0
,
 
c
l
a
s
s
_
w
e
i
g
h
t
=
N
o
n
e
,
 
d
u
a
l
=
F
a
l
s
e
,
 
f
i
t
_
i
n
t
e
r
c
e
p
t
=
T
r
u
e
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
i
n
t
e
r
c
e
p
t
_
s
c
a
l
i
n
g
=
1
,
 
l
1
_
r
a
t
i
o
=
N
o
n
e
,
 
m
a
x
_
i
t
e
r
=
1
0
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
m
u
l
t
i
_
c
l
a
s
s
=
'
w
a
r
n
'
,
 
n
_
j
o
b
s
=
N
o
n
e
,
 
p
e
n
a
l
t
y
=
'
l
1
'
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
r
a
n
d
o
m
_
s
t
a
t
e
=
0
,
 
s
o
l
v
e
r
=
'
l
i
b
l
i
n
e
a
r
'
,
 
t
o
l
=
0
.
0
0
0
1
,
 
v
e
r
b
o
s
e
=
0
,

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
w
a
r
m
_
s
t
a
r
t
=
F
a
l
s
e
)

</pre>

```python
#
 
c
a
l
c
u
l
a
t
e
 
G
r
i
d
S
e
a
r
c
h
 
C
V
 
s
c
o
r
e
 
o
n
 
t
e
s
t
 
s
e
t


p
r
i
n
t
(
'
G
r
i
d
S
e
a
r
c
h
 
C
V
 
s
c
o
r
e
 
o
n
 
t
e
s
t
 
s
e
t
:
 
{
0
:
0
.
4
f
}
'
.
f
o
r
m
a
t
(
g
r
i
d
_
s
e
a
r
c
h
.
s
c
o
r
e
(
X
_
t
e
s
t
,
 
y
_
t
e
s
t
)
)
)
```

<pre>
G
r
i
d
S
e
a
r
c
h
 
C
V
 
s
c
o
r
e
 
o
n
 
t
e
s
t
 
s
e
t
:
 
0
.
8
4
8
8

</pre>
#
#
#
 
C
o
m
m
e
n
t
s






원
래
 
모
델
의
 
테
스
트
 
정
확
도
는
 
0
.
8
4
8
3
이
고
,
 
G
r
i
d
S
e
a
r
c
h
 
C
V
 
정
확
도
는
 
0
.
8
4
8
8
입
니
다
.
 
이
를
 
통
해
 
우
리
는
 
G
r
i
d
S
e
a
r
c
h
 
C
V
가
 
이
 
모
델
에
서
 
성
능
을
 
개
선
시
켰
음
을
 
알
 
수
 
있
습
니
다
.


#
 
*
*
2
1
.
 
R
e
s
u
l
t
s
 
a
n
d
 
c
o
n
c
l
u
s
i
o
n
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
2
1
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)


1
.
 
로
지
스
틱
 
회
귀
 
모
델
의
 
정
확
도
 
점
수
는
 
0
.
8
4
8
3
입
니
다
.
 
따
라
서
 
모
델
은
 
오
늘
 
오
스
트
레
일
리
아
에
서
 
비
가
 
올
 
것
인
지
 
아
닌
지
 
예
측
하
는
 
데
 
매
우
 
잘
 
작
동
합
니
다
.




2
.
 
적
은
 
수
의
 
관
측
치
들
이
 
내
일
 
비
가
 
올
 
것
이
라
고
 
예
측
하
고
,
 
대
부
분
의
 
관
측
치
들
은
 
내
일
 
비
가
 
오
지
 
않
을
 
것
이
라
고
 
예
측
합
니
다
.




3
.
 
모
델
은
 
과
적
합
의
 
징
후
가
 
없
습
니
다
.




4
.
 
C
 
값
의
 
증
가
는
 
테
스
트
 
집
합
의
 
정
확
도
와
 
약
간
 
증
가
된
 
학
습
 
집
합
의
 
정
확
도
를
 
초
래
합
니
다
.
 
따
라
서
 
더
 
복
잡
한
 
모
델
이
 
더
 
나
은
 
성
능
을
 
발
휘
할
 
것
으
로
 
결
론
 
짓
을
 
수
 
있
습
니
다
.




5
.
 
임
계
값
을
 
높
이
면
 
정
확
도
가
 
높
아
집
니
다
.




6
.
 
모
델
의
 
R
O
C
 
A
U
C
는
 
1
에
 
가
까
워
지
므
로
,
 
모
델
은
 
내
일
 
비
가
 
올
지
 
여
부
를
 
예
측
하
는
 
데
 
우
수
한
 
성
능
을
 
발
휘
한
다
는
 
결
론
을
 
내
릴
 
수
 
있
습
니
다
.




7
.
 
원
래
 
모
델
의
 
정
확
도
 
점
수
는
 
0
.
8
4
8
3
이
고
,
 
R
F
E
C
V
 
후
 
정
확
도
 
점
수
는
 
0
.
8
4
8
8
입
니
다
.
 
따
라
서
 
거
의
 
동
일
한
 
정
확
도
를
 
얻
지
만
 
f
e
a
t
u
r
e
의
 
수
는
 
줄
어
듭
니
다
.




8
.
 
원
래
 
모
델
에
서
 
F
P
 
=
 
1
1
7
5
이
고
,
 
F
P
1
 
=
 
1
1
7
4
입
니
다
.
 
따
라
서
 
거
짓
 
양
성
의
 
수
가
 
거
의
 
동
일
합
니
다
.
 
또
한
 
F
N
 
=
 
3
0
8
7
이
고
,
 
F
N
1
 
=
 
3
0
9
1
입
니
다
.
 
따
라
서
 
거
짓
 
음
성
의
 
수
가
 
약
간
 
더
 
높
습
니
다
.




9
.
 
원
래
 
모
델
 
점
수
는
 
0
.
8
4
7
6
입
니
다
.
 
평
균
 
교
차
 
검
증
 
점
수
는
 
0
.
8
4
7
4
입
니
다
.
 
따
라
서
 
교
차
 
검
증
은
 
성
능
 
향
상
을
 
가
져
오
지
 
않
는
 
것
으
로
 
결
론
짓
을
 
수
 
있
습
니
다
.




1
0
.
 
원
래
 
모
델
의
 
테
스
트
 
정
확
도
는
 
0
.
8
5
0
1
이
고
,
 
G
r
i
d
S
e
a
r
c
h
 
C
V
의
 
정
확
도
는
 
0
.
8
5
0
7
입
니
다
.
 
이
 
모
델
에
 
대
해
 
G
r
i
d
S
e
a
r
c
h
 
C
V
가
 
성
능
을
 
향
상
시
켰
음
을
 
알
 
수
 
있
습
니
다
.




#
 
*
*
2
2
.
 
R
e
f
e
r
e
n
c
e
s
*
*
 
<
a
 
c
l
a
s
s
=
"
a
n
c
h
o
r
"
 
i
d
=
"
2
2
"
>
<
/
a
>






[
T
a
b
l
e
 
o
f
 
C
o
n
t
e
n
t
s
]
(
#
0
.
1
)








T
h
e
 
w
o
r
k
 
d
o
n
e
 
i
n
 
t
h
i
s
 
p
r
o
j
e
c
t
 
i
s
 
i
n
s
p
i
r
e
d
 
f
r
o
m
 
f
o
l
l
o
w
i
n
g
 
b
o
o
k
s
 
a
n
d
 
w
e
b
s
i
t
e
s
:
-






1
.
 
H
a
n
d
s
 
o
n
 
M
a
c
h
i
n
e
 
L
e
a
r
n
i
n
g
 
w
i
t
h
 
S
c
i
k
i
t
-
L
e
a
r
n
 
a
n
d
 
T
e
n
s
o
r
f
l
o
w
 
b
y
 
A
u
r
e
́
l
i
e
́
n
 
G
e
́
r
o
n




2
.
 
I
n
t
r
o
d
u
c
t
i
o
n
 
t
o
 
M
a
c
h
i
n
e
 
L
e
a
r
n
i
n
g
 
w
i
t
h
 
P
y
t
h
o
n
 
b
y
 
A
n
d
r
e
a
s
 
C
.
 
M
u
̈
l
l
e
r
 
a
n
d
 
S
a
r
a
h
 
G
u
i
d
o




3
.
 
U
d
e
m
y
 
c
o
u
r
s
e
 
–
 
M
a
c
h
i
n
e
 
L
e
a
r
n
i
n
g
 
–
 
A
 
Z
 
b
y
 
K
i
r
i
l
l
 
E
r
e
m
e
n
k
o
 
a
n
d
 
H
a
d
e
l
i
n
 
d
e
 
P
o
n
t
e
v
e
s




4
.
 
U
d
e
m
y
 
c
o
u
r
s
e
 
–
 
F
e
a
t
u
r
e
 
E
n
g
i
n
e
e
r
i
n
g
 
f
o
r
 
M
a
c
h
i
n
e
 
L
e
a
r
n
i
n
g
 
b
y
 
S
o
l
e
d
a
d
 
G
a
l
l
i




5
.
 
U
d
e
m
y
 
c
o
u
r
s
e
 
–
 
F
e
a
t
u
r
e
 
S
e
l
e
c
t
i
o
n
 
f
o
r
 
M
a
c
h
i
n
e
 
L
e
a
r
n
i
n
g
 
b
y
 
S
o
l
e
d
a
d
 
G
a
l
l
i




6
.
 
h
t
t
p
s
:
/
/
e
n
.
w
i
k
i
p
e
d
i
a
.
o
r
g
/
w
i
k
i
/
L
o
g
i
s
t
i
c
_
r
e
g
r
e
s
s
i
o
n




7
.
 
h
t
t
p
s
:
/
/
m
l
-
c
h
e
a
t
s
h
e
e
t
.
r
e
a
d
t
h
e
d
o
c
s
.
i
o
/
e
n
/
l
a
t
e
s
t
/
l
o
g
i
s
t
i
c
_
r
e
g
r
e
s
s
i
o
n
.
h
t
m
l




8
.
 
h
t
t
p
s
:
/
/
e
n
.
w
i
k
i
p
e
d
i
a
.
o
r
g
/
w
i
k
i
/
S
i
g
m
o
i
d
_
f
u
n
c
t
i
o
n




9
.
 
h
t
t
p
s
:
/
/
w
w
w
.
s
t
a
t
i
s
t
i
c
s
s
o
l
u
t
i
o
n
s
.
c
o
m
/
a
s
s
u
m
p
t
i
o
n
s
-
o
f
-
l
o
g
i
s
t
i
c
-
r
e
g
r
e
s
s
i
o
n
/




1
0
.
 
h
t
t
p
s
:
/
/
w
w
w
.
k
a
g
g
l
e
.
c
o
m
/
m
n
a
s
s
r
i
b
/
t
i
t
a
n
i
c
-
l
o
g
i
s
t
i
c
-
r
e
g
r
e
s
s
i
o
n
-
w
i
t
h
-
p
y
t
h
o
n




1
1
.
 
h
t
t
p
s
:
/
/
w
w
w
.
k
a
g
g
l
e
.
c
o
m
/
n
e
i
s
h
a
/
h
e
a
r
t
-
d
i
s
e
a
s
e
-
p
r
e
d
i
c
t
i
o
n
-
u
s
i
n
g
-
l
o
g
i
s
t
i
c
-
r
e
g
r
e
s
s
i
o
n




1
2
.
 
h
t
t
p
s
:
/
/
w
w
w
.
r
i
t
c
h
i
e
n
g
.
c
o
m
/
m
a
c
h
i
n
e
-
l
e
a
r
n
i
n
g
-
e
v
a
l
u
a
t
e
-
c
l
a
s
s
i
f
i
c
a
t
i
o
n
-
m
o
d
e
l
/




[
G
o
 
t
o
 
T
o
p
]
(
#
0
)

