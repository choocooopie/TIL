# [Kotlin] 코틀린 기초 문법 총정리
오현석 2025.05.29  
코틀린 문법을 한번에 총정리하기.(복습용)
***
## 1. 변수
### var : 변경 가능한 변수값  

### var : 변경 가능한 변수값
```kotlin
main(){
  var a: Int = 123 // 자료형 선언시 -> 변수: type
  print(a)
}
```
```kotlin
fun main(){
  val b: Int = 1232
  b = 3 // 중간에 값을 못바꾸기 때문에 에러발생
  print(b)
}
```
### ? : 변수의 값이 null일 수 있다는 것을 표시(?를 표시 하지 않으면 선언시 null이 불가능)  
```kotlin
fun main(){
    val a: Int? = null
    print(a)
}
// 출력 : null
```

## 2. 형변환  
### 코틀린에서는 to변수()를 통해 형변환 가능  

### 코틀린은 *암시적 형변환을 지원하지 않음  
<details>
  <summary>*암시적 형변환이란</summary>
예를 들어 자바에서는 다음과 같은 코드가 허용된다.

```java
int a = 10;
double b = a;
```
자바에서는 작은 크기의 데이터 타입(int)이 더 큰 크기의 데이터 타입(long)으로 자동 변환된다. 개발자가 특별히 형변환을 지정하지 않았지만, 컴파일러가 자동으로 처리해주는 것이다.  
  
반면 코틀린에서는 이러한 암시적 형변환을 허용하지 않는다.  

```kotlin
// Kotlin 코드
val number: Int = 10
val bigNumber: Long = number // 컴파일 오류!
val bigNumber: Long = number.toLong() // 명시적 변환 필요
```  
이러한 접근 방식은 코틀린의 "안전 우선(Safety First)" 철학을 반영하는 좋은 예이다.
</details>  

```kotlin
fun main(){
    var a: Int = 123
    var b: String = a.toString()
    print(b)
}
```  

## 3. 배열  
### 배열에서 type은 생략 가능함
```kotlin
fun main(){
    // int형으로 1 2 3 4 배열 생성
    var intArr: Array<Int> = arrayOf(1, 2, 3, 4)
    // type 생략 가능
    var intArr2 = arrayOfNulls<Int>(5)
    // Any는 데이터 타입의 최상위(어느 데이터든 다 들어갈 수 있음)
    var anyArr: Array<Any> = arrayOf(1, "qwe", 3.2, 4)
    println(intArr[0])
    println(intArr2[1])
    println(anyArr[1])
}

출력
1
null
qwe
```    
*배열은 0의 첫번째 요소임. 0 ,1 ,2 ,3... 순서*

