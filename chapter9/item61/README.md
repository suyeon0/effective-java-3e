`일반적인 프로그래밍 원칙 (9장)`

# [ITEM61] 박싱된 기본 타입보다는 기본 타입을 사용하라

---
## 기본타입 VS 참조타입

(1) 기본 타입은 값만 가지고 있으나, 박싱 타입은 식별성을 갖는다
  * 박싱된 기본 타입의 두 인스턴스는 값이 같아도 서로 다르다고 식별될 수 있다
    #### 따라서 "박싱된 기본 타입에 == 연산자를 사용하면 오류가 일어난다"

(2) 기본 타입의 값은 언제나 유효하지만, 박싱된 기본타입은 null 을 가질 수 있다

(3) 기본 타입이 박싱된 기본 탕비보다 시간과 메모리 사용면에서 더 효율적이다.

---
## 기본타입과 참조타입 비교 연산

* 참조 타입은 equals 를 사용한다
  * Boxed primitive 또는 Wrapper class(Integer) 끼리 비교 하는 경우, == 연산자는 각 객체의 주소 값을 비교 하게 된다.
    
* 비교 대상 중 하나라도 기본 타입이 있다면 박싱된 기본 타입의 박싱이 자동으로 풀린다.

* 언박싱 과정에서 NPE 를 던질 수 있다
```java
public class Test {
    static Integer i;
    
    public static void main(String[] args){
        if (i == 42) { // NPE 발생 !
            System.out.println("test");
        }
    }
}
```

https://marobiana.tistory.com/130

---

## 박싱된 기본타입이 쓰여야 하는 경우
(1) 컬렉션의 원소, 키, 값으로 쓴다
* 이건 컬렉션이 기본 타입을 담을 수 없으므로 어쩔 수 없는 부분!

(2) 매개변수화 타입이나 매개변수화 메서드의 타입 매개변수
* ex. ThreadLocal<Integer>

(3) 리플렉션을 통해 메서드 호출할 때


---

## 결론
기본 타입과 박싱된 기본 타입 중 하나를 선택해야 한다면 가능하면 기본 타입을 사용하자