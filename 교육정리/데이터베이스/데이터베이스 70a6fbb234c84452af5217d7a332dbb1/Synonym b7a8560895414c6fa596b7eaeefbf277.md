# Synonym

: 주로 참조의 목적으로 데이터를 조회하고자 할 때 동의어를 생성하여 대신 사용하는 것이 하나의 방법이 될 수 있다.

❏정의
Another name for an object

❏ 용도
① 다른 USER에 의해 소유된 TABLE을 참조할때 SCHEMA를 생략 할수 있다 → 위치 투명성
② 긴OBJECT명을 짧은 이름으로 사용할수 있다. → 코드 간결성

### ****CREATE SYNONYM의 사용****

: **CREATE SYNONYM 는 동의어를 생성해 주는 명령어**입니다.

**(1) 기본식 : 객체A에 's'라는 (전용)동의어를 생성하기 (private synonym)**

기본적으로 생성되는 것은 특정 사용자가 소유한 전용 동의어입니다.

```sql
create synonym 동의어이름s for 객체A;
```

**(2) 기본식 : 동의어를 새로 생성하거나, 같은 이름의 동의어를 대체(갱신) 하는 경우**

CREATE OR REPLACE SYNONYM 명령어를 사용하면, 같은 이름의 동의어가 있을 시 덮어쓰기 됩니다.

```sql
create or replace synonym 동의어이름s for 객체A;
```

**(3) 기본식 : 객체A에 's'라는 공용 동의어(PUBLIC SYNONYM) 생성하기**

공용 동의어를 사용할 경우, 'PUBLIC'을 붙여 줍니다. 공용 동의어는 모든 사용자가 사용할 수 있는 동의어입니다.

- **단, PUBLIC SYNONYM을 생성하려면 이에 걸맞는 권한이 GRANT 명령어로 부여된 상태여야 합니다.**

```sql
create public synonym 동의어이름s for 객체A;
```