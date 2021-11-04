## 7장 오류처리 ##

#### 메소드 return 으로 빈 arrayList 를 내보내고 싶을 때 ####
```java
return Collections.emptyList();
```

#### 메소드 시작부분에 null 체크를 해주는게 좋을까? ####

- public, protected 라면 해주는게 좋을 듯?
- private 라면 안해줘도 될 듯?
- 메소드 caller 보다는 callee 에서 null 체크를 해주는게 깔끔 할 듯

#### Exception Wrapper 클래스 ####
- 실제로 외부 API를 사용할 때는 감싸기 기법이 최선이다.
- 외부 API를 감싸면 외부 라이브러리와 프로그램 사이에서 의존성이 크게 줄어든다.
- (어댑터 패턴 참고)

#### null 을 반환하지 마라? ####
- 메소드를 만들 때 null 을 반환하지 않도록 컨벤션을 잡으면, 메소드 만들 때 초반에 null 체크 코드를 안 넣어도 되지 않을까?
- 그래도, 방어적으로 하려면 null 을 반환하지도 않고, 초반에 null 체크도 하도록 메소드를 만들면 좋을 것 같다.
- 예를들어, queryDsl 의 fetch() 는 null 을 반환하지 않으므로 그대로 return 하고, 
- fetchOne() 은 Optional 로 리턴하도록 컨벤션을 잡아도 좋을 듯