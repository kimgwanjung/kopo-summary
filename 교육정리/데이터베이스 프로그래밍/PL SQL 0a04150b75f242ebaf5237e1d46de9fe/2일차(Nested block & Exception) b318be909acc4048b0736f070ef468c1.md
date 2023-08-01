# 2일차(Nested block & Exception)

## NULL

<aside>
👉🏻 프로그램 개발시 변수 선언후 초기화 하지 않는 경우나 NULL값이 존재하는 경우 연산(논리연산,비교연산)시 예상치 못하는 결과 발생 가능

</aside>

```sql
SET SERVEROUTPUT ON
DECLARE
V_NUM1 NUMBER(4,2); -- 변수선언
V_NUM2 NUMBER(4,2) := 30; -- 변수 선언 AND 초기값 할당
BEGIN
IF (V_NUM1 > 1 AND V_NUM2 < 31) THEN -- NULL AND TRUE 
DBMS_OUTPUT.PUT_LINE('(V_NUM1 > 1 AND V_NUM2 < 31) IS TRUE '); 
ELSIF NOT (V_NUM1 > 1 AND V_NUM2 < 31) THEN
DBMS_OUTPUT.PUT_LINE('(V_NUM1 > 1 AND V_NUM2 < 31) IS FALSE '); 
ELSE 
DBMS_OUTPUT.PUT_LINE(' NOT TRUE, NOT FALSE... ???? '); 
END IF;
END;
/
```

![Untitled](2%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1(Nested%20block%20&%20Exception)%20b318be909acc4048b0736f070ef468c1/Untitled.png)

## **Nested block & Transaction**

Nested : 중첩된 포개진

### Nested block

중첩된 Block으로 Block 안에 또 다른 Block이 내포된 구조

목적 : 1. 예외처리 2. 모듈화

```sql
SET SERVEROUTPUT ON
<<MAIN_BLK>>
DECLARE
V_DNAME VARCHAR2(14);
V_DEPTNO NUMBER(2);
V_LOC VARCHAR2(13);
BEGIN
V_DEPTNO := 77;
V_DNAME := ‘Global variable’;
V_LOC := 'Main_Block';
<<LOCAL_BLOCK_1>>
DECLARE
V_DNAME VARCHAR2(14);
V_DEPTNO NUMBER(2);
BEGIN
V_DEPTNO := 88;
V_DNAME := 'Local variable1';
V_LOC := 'Nested_Block1’;
INSERT INTO DEPT 
VALUES(V_DEPTNO,MAIN_BLK.V_DNAME,V_LOC);
END LOAL_BLOCK_1;
```

![Untitled](2%E1%84%8B%E1%85%B5%E1%86%AF%E1%84%8E%E1%85%A1(Nested%20block%20&%20Exception)%20b318be909acc4048b0736f070ef468c1/Untitled%201.png)