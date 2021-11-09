#10장 클래스 

- 클래스는 작아야 한다.
- 클래스는 책임이 명확해야 한다.

> 클래스 체계
- 클래스 내에 변수, 메서드 작성 순서
  - static public 상수
  - static private 변수
  - 비공개 인스턴스 변수
  - 공개 함수
  - 비공개 함수 (자신을 호출하는 공개 함수 직후)
  - 공개 함수
  - 비공개 함수 (자신을 호출하는 공개 함수 직후)
  - ...

> 단일 책임 원칙 (SRP)
- 클래스는 책임이 하나여야 한다.

> 응집도 (Cohesion)
- 일반적으로 메서드가 변수를 더 많이 사용할수록 메서드와 클래스는 응집도가 더 높다.
- 모든 인스턴스 변수를 메서드마다 사용하는 클래스는 응집도가 가장 높다. 
- 응집도가 높다는 말은 클래스에 속한 메서드와 변수가 서로 의존하며 논리적인 단위로 묶인다는 의미이다.

> SRP와 OCP 지원한 설계 예시
- 나중에 update Sql 의 추가가 필요하면 Sql 추상 클래스를 상속받기만 하면되므로, SRP와 OCP를 지원한다.

```java
abstract public class Sql {
    public Sql(String table, Column[] columns);
    abstract public String generate();
}

public class CreateSql extends Sql {
    public CreateSql(String table, Column[] columns);
    @Override
    public String generate();
}

public class SelectSql extends Sql {
    public CreateSql(String table, Column[] columns);
    @Override
    public String generate();
}

public static void main(String[] args) {
    Sql selectSql = new CreateSql();
    Sql updateSql = new UpdateSql();
} 
```

