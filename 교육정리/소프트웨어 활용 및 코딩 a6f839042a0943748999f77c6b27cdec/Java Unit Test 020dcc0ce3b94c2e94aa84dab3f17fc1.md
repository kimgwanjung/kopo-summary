# Java Unit Test

### 잘못된 개발의 완성 기준

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled.png)

→ 이것을 절반 완성 했다고 볼 수 있느냐? —> NO

### 올바른 개발의 완성 기준

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%201.png)

→ 절반을 작성했다면, 그것의 4배가 남아 있다고 본다. (품질까지 생각해야 함)

### 품질은 어떻게 향상 시킬까? → 테스트!

수동 테스트 : 인간이 하는 테스트

단위 테스트 : 1개 클래스를 테스트

통합 테스트 : 여러 개 연관된 클래스를 함께 테스트

## 단위 테스트란?

: 특정 모듈이 의도한 대로 잘 작동하는가를 테스트하는 것

잘못된 코드

```java
public class Account {
    private String owner;
    private int balance;
    
    public void Account(String owner, int balance) {
        owner = owner;
        balance = balance;
    }
    
    public void transfer(Account dest, int amount) {
        dest.setBalance(dest.getBalance() + amount);
        balance -= amount;
    }

    public String getOwner() {
        return owner;
    }

    public void setOwner(String owner) {
        this.owner = owner;
    }

    public int getBalance() {
        return balance;
    }

    public void setBalance(int balance) {
        this.balance = balance;
    }
}
```

버그를 찾아보자!

수동테스트

```java
public class Account {
    private String owner;
    private int balance;
    
    public Account(String owner, int balance) {
        this.owner = owner;
        this.balance = balance;
    }
    
    public void transfer(Account dest, int amount) {
        dest.setBalance(dest.getBalance() + amount);
        balance -= amount;
    }

    public String getOwner() {
        return owner;
    }

    public void setOwner(String owner) {
        this.owner = owner;
    }

    public int getBalance() {
        return balance;
    }

    public void setBalance(int balance) {
        this.balance = balance;
    }
    public static void main(String[] args) {
        Account account = new Account("홍길동", 30000);
        System.out.println(account);
    }

    @Override
    public String toString() {
        return "Account [owner=" + owner + ", balance=" + balance + "]";
    }
}
```

→ 테스트를 통해 생성자가 잘못 됨을 인지

### 테스트 케이스

: **가능한 모든 가능성**의 범위를 테스트하는 것이 좋은 테스트 케이스이다!!

ex) 만약에 위에 int형의 범위를 넘어가는 값을 넣어야 할 때, 테스트 필수!

```java
public static void main(String[] args) {
        Account account = new Account("홍길동", 30000);
        System.out.println(account);
        
        Account account2 = new Account("한석봉", 0);
        account2.transfer(account2, Integer.MAX_VALUE + 1);
        
        if(account2.getBalance() != 2147483648L) {
            System.out.println("getBalance() 값이 다름" + account2.getBalance());
            
        }
    }
```

→ 테스트를 통해 잘못된 부분을 찾아야 한다.

## 이러한 테스트 케이스 장점!

- 장애에 관한 **신속한 피드백**
- 개발 주기에서 **조기 장애 감지**
- 회귀에 신경 쓸 필요 없이 코드를 최적화할 수 있도록 하는 **더 안전한 코드 리팩터링**
- 기술적 문제를 최소화하는 **안정적인 개발 속도**

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%202.png)

### 테스트 케이스 중 단위 테스트가 필요한 경우

- DB
    - 스키마가 변경되는 경우
    - 모델 클래스가 변경되는 경우
- Network
    - 예측한 데이터가 제대로 들어오는지
- 데이터 검증
    - 예측한 데이터를 제대로 처리하고 있는지

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%203.png)

## 테스트 환경 준비

1 Step

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%204.png)

2 Step

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%205.png)

3 Step

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%206.png)

4 Step

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%207.png)

# JUnit(단위 테스트 용 라이브러리)

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%208.png)

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%209.png)

assertEquals를 통해 값을 테스트한다.

**잘못된 경우**

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2010.png)

**테스트 코드 작성 예**

```java
import static org.junit.Assert.*;
import org.junit.Test;
import kr.ac.kopo.Exam.Java0321_02.Account;

public class AccountTest {

    @Test
    public void test() {
        Account account = new Account("홍길동", 30000);
        assertEquals("홍길동", account.getOwner());
        assertEquals(30000, account.getBalance());
    }
    
    @Test
    public void transfer_테스트() {
        Account account = new Account("홍길동", 30000);
        Account account2 = new Account("한석봉", 0);
        
        account.transfer(account2, 10000);
        
        assertEquals(20000, account.getBalance());
        assertEquals(10000, account.getBalance());
    }
}
```

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2011.png)

잘못된 부분 확인하고 디버깅을 통해 찾는다.

### 특정 테스트가 특정 예외가 발생되어야 하는 것을 테스트 하는 법

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2012.png)

연습문제 1

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2013.png)

—>테스트를 해보자

```java
public class BankTest {
    @Test(expected = IllegalArgumentException.class)
    public void test() {
        
            Bank bank = new Bank();
            Bank bank1 = new Bank();
            String name = "ab";
            bank.setName(name);
            assertEquals(name, bank.getName()); 
            String name1 = "abcdef";
            bank1.setName(name1);
            assertEquals(name1, bank1.getName());
               
    }
}
```

연습문제2

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2014.png)

```java
public class DownCounter {
    private int count = 0;
    
    public int getCount() {
        return count;
    }

    public void setCount(int count) {
        this.count = count;
    }

    public void decrement() {
        count--;
    }
}
```

연습문제3

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2015.png)

```java
public class CounterTest {

    Counter counter = new Counter();
	// 카운트
    @Test
    public void Count() {
        assertEquals(0, counter.getCount());
    }
  // 증가 확인
    @Test
    public void Increment() {
        counter.increment();
        assertEquals(1, counter.getCount());
        counter.increment();
        assertEquals(2, counter.getCount());
    }
}
```

연습문제4

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2016.png)

```java
public class Counter {
    private int count = 0;
    
    public int getCount() {
        return count;
    }

    public void setCount(int count) {
        this.count = count;
    }

    public void count() {
        count++;
    }
}
```

```java
public class DownCounter {
    private int count = 0;
    
    public int getCount() {
        return count;
    }

    public void setCount(int count) {
        this.count = count;
    }

    public void count() {
        count--;
    }

}
```

→count로 변경한 코드

연습문제 5

![Untitled](Java%20Unit%20Test%20020dcc0ce3b94c2e94aa84dab3f17fc1/Untitled%2017.png)

```java
// Counter 인터페이스
interface Counter {
    int count();
}

// UpCounter 클래스
class UpCounter implements Counter {
    private int count;

    public UpCounter() {
        this.count = 0;
    }

    public int count() {
        this.count++;
        return this.count;
    }
}

// DownCounter 클래스
public class DownCounter implements Counter {
    private int count;

    public DownCounter(int count) {
        this.count = count;
    }

    public int count() {
        this.count--;
        return this.count;
    }
}
```