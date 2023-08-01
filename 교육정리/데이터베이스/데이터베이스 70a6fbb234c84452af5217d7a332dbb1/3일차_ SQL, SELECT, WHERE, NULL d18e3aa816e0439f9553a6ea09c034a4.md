# 3일차_ SQL, SELECT, WHERE, NULL

### SQL의 주요특징 4가지(첫 번째 시험 문제)

1. 관계형  DBMS(RDBMS)에 접근하는 유일한 언어
2. ANSI/ISO-SQL : SQL 표준을 정립하여 여러 DBMS에서 접근할 수 있게 하는 장점
3. ENGLISH-LIKE : 영어와 유사하게 문법적인 구조 및 의미를 가지고 있다.(대-소문자 구분 X, 데이터는 대소문자를 구분한다) 
4. **비절차적 언어 : 구조적이며, 집합적, 선언적이다.

### SQL

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled.png)

### SQL 명령어(두 번째 시험 문제)

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%201.png)

→분류와 종류 모두 외우기

Merge = Update + Insert

가. QUERY(질의어)
데이터베이스에 저장된 데이터를 조회 하는 명령어
나. DML(Data Manipulation Language:데이터 처리어)
데이터베이스에 저장된 데이터를 삽입/수정/삭제 하는 명령어
다. TCL(Transaction Control Language:트랜잭션 제어어)
데이터베이스에서 발생하는 트랜잭션을 저장/취소하는 명령어
라. DDL(Data Definition Language:데이터 정의어)
데이터베이스의 논리적 구조를 정의/변경/삭제 하기 위한 명령어
마. DCL(Data Control Language:데이터 제어어)
데이터베이스에 저장된 데이터에 대한 접근 권한을 부여/회수하는 명령어

### RDBMS 이해

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%202.png)

*3.NULL 10.무결성

### RDBMS 장점

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%203.png)

### SQL Developer

: Oracle에서 무료로 제공하는 Java 기반 GUI IDE를 갖춘 SQL 개발 및 관리툴

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%204.png)

### SQL 명령어 분류와  SELECT

QUERY
① 질의어 : 데이터베이스에 저장된(테이블) 데이터를 조회 하는 명령어
② SQL

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%205.png)

—> 해석

### SELECT LIST

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%206.png)

** 기억

① SELECT EMPNO,ENAME,JOB,MGR,HIREDATE,SAL,COMM,DEPTNO FROM EMP;
② SELECT * FROM EMP;

- EMP는 8개 컬럼으로 정의 , ① ② 같은 결과 조회, * 의미는? 조회순서는?
- 좋은 방식의 SQL문은?
- 컬럼 구분자 콤마(,) , SQL 문장 종결자(;)

③ SELECT EMPNO, ENAME, HIREDATE FROM EMP;

- 원하는 컬럼만 선택하여 조회
- 데이터 타입 : EMPNO(숫자), ENAME(문자), HIREDATE(날짜)
- 데이터 정렬 방향 : 문자는 왼쪽 정렬, 숫자는 오른쪽 정렬, 날짜는 외부에는 문자처럼 정렬, 내부에는 숫자처럼 오른쪽으로 정력
- 컬럼 헤딩(Column Heading) - 대문자 표기, 데이터와 정렬 방향이 동일

④ SELECT SAL, JOB, EMPNO, ENAME FROM EMP;

- 컬럼 조회 순서 임의로 변경 가능

⑤ SELECT EMPNO, EMPNO, EMPNO, ENAME, JOB, SAL FROM EMP;

- 동일한 컬럼 여러번 조회 가능, 용도? → 응용할 날이 있다.

⑥ SELECT EMPNO, SAL, 2022, 'Happy New Year' FROM EMP;

- 홑따옴표(＇) = 단일인용부호 = single quotation mark
- 2022 : 숫자 데이터, 'Happy New Year' : 문자 데이터
- 테이블 내에 존재하지 않지만 SELECT시 임의적으로 데이터를 만들어서 조회 가능

orcle은 일반적으로 1521port 에서 listening

Client 1. ip 2.port 3.protocol 4. Service Name

### 산술 연산자와 가명, 별칭

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%207.png)

- 날짜 데이터는 연산이 가능하다.
- null에 대한 연산처리가 불가능하기에 주의**
- 의미가 명확하게 괄호를 활용해라
- Table Alias : SELF JOIN시 사용(중요)
- Column Alias : 컬럼 레이블을 의미 있는 이름으로 재정의
- as 즐겨써라(명료하다), “”는 대소문자 구분, 한글 컬럼 Alias 가능

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%208.png)

- || 결합 연산자
- ‘’ 문자 결합
- ‘” ‘ 문자내의 ‘
- sal||’00’ : sal은 숫자이고 00은 문자이다 → 문자로 바뀐다.
- Dummy Table은 function이나 calculation을 수행하기 위해 사용하는 테이블
- sysdate 현재 date를 리턴하는 함수이다. date → 날짜와 시간의 의미를 가진다.

### NULL

: 값이 정의되지 않은, 존재하지 않는 즉, 데이터가 존재하지 않는 상태이다.(결측치)

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%209.png)

![Untitled](3%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1_%20SQL,%20SELECT,%20WHERE,%20NULL%20d18e3aa816e0439f9553a6ea09c034a4/Untitled%2010.png)