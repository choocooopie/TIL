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

## 4. 함수  
### 기본형 함수  
```kotlin
fun main(){
    print(add(1,2,3))
}

// 함수의 기본형 fun 함수이름(매개변수: type): 리턴 타입
fun add(a: Int, b: Int, c: Int): Int{
    return a + b + c;
}

출력:
6
```  
### 단일 표현식 함수  
```kotlin
fun main(){
    print(add(1,2,3))
}
// int a,b,c를 더하므로 반환형 타입이 int라 추론 가능
fun add(a: Int, b: Int, c: Int) = a + b + c

출력:
6
```  
### 문자열의 경우  
```kotlin
fun main() {
    print(add("Hello", ", ", "World!"))
}

fun add(a: String, b: String, c: String): String{
    return a + b + c
}

출력:
Hello, World!
```  

## 5. 조건문  
### if : 다른 언어와 동일함  
```kotlin
fun main(){
    var a = 7
    if(a > 6){
        println(a)
    } else{
        print("exit")
    }
}

출력:
7
```  
### is : 데이터 타입 비교  
```kotlin
fun main(){
    var a: Any = 1

    if(a is Int){
        println("int")
    }

    if(a is String){
        println("string")
    }
}

출력:
int
```  
*회원가입 시 전화번호 기입 할 때 입력 받은 값이 숫자인지 문자인지 구분시켜 재입력 시킬 수 있음*  
### when : switch문이랑 비슷한 기능  
```kotlin
// 동작 실행
fun main(){
    exWhen(2)
}
fun exWhen(a: Any){
    when(a){
        1 -> print(a)
        "qwe" -> print(a)
        else -> print(a)
    }
}

출력:
2
```  
```kotlin
// 값 설정
fun main(){
    exWhen(2)
}
fun exWhen(a: Any){
    var b =
        when(a) {
            1 -> a
            "qwe" -> a
            else -> a
        }
    print(b)
}

출력:
2
```  
*b 값 안에 when문 전체가 들어가서 입력되는 것*  

## 7. 흐름 제어  
### break, continue : 다른 언어와 동일함  
```kotlin
// 값 설정
fun main(){
    for(i in 0..5){
        if(i == 2){
            break;
        }
        print(i)
        print("")
    }

    println()

    for(i in 0..5){
        if(i == 2){
            continue;
        }
        print(i)
        print("")
    }
}

출력:
01
012345
```  
### @label : 반복문에 라벨이름@을 달고 break, continue문에 @라벨이름을 달면 break, continue가 라벨이름으로 가 실행  
<details>
  <summary>*코틀린 논리 연산자 정리</summary>

**1. 논리 연산자(Logical Operators)**

| 연산자  | 이름     | 설명                           | 예시                    |
|------|--------|------------------------------|-----------------------|
| `&&` | AND(논리곱) | 두 조건이 모두 true일 때만 true 반환    | `if (x > 0 && y > 0)` |
| `ㅣㅣ` | OR(논리합) | 두 조건 중 하나라도 true이면 true 반환 | `if (x > 0 ㅣㅣ y > 0)` |
| `!`  | NOT(부정) | true를 false로, false를 true로 변환 | `if (!isDone)`        |

**2. 비트 연산자(Bitwise Operators)**

비트 연산자는 정수형 값의 비트를 조작할 때 사용합니다. 코틀린에서는 Java와 달리 비트 연산자를 특수 기호가 아닌 중위 함수 표기법으로 제공합니다.

| 연산자 | 이름 | 설명 | 예시 |
| --- | --- | --- | --- |
| `and` | Bitwise AND | 두 비트가 모두 1일 때만 1 반환 | `val result = a and b` |
| `or` | Bitwise OR | 두 비트 중 하나라도 1이면 1 반환 | `val result = a or b` |
| `xor` | Bitwise XOR | 두 비트가 다를 때만 1 반환 | `val result = a xor b` |
| `inv` | Bitwise Inversion | 모든 비트를 반전(0→1, 1→0) | `val result = a.inv()` |
| `shl` | Signed Left Shift | 지정된 비트 수만큼 왼쪽으로 이동 | `val result = a shl n` |
| `shr` | Signed Right Shift | 지정된 비트 수만큼 오른쪽으로 이동 (부호 유지) | `val result = a shr n` |
| `ushr` | Unsigned Right Shift | 지정된 비트 수만큼 오른쪽으로 이동 (0으로 채움) | `val result = a ushr n` |

**3. 특수 연산자 및 표현식**

코틀린에서는 추가적인 특수 연산자와 표현식을 제공합니다.

| 연산자/표현식 | 이름 | 설명 | 예시 |
| --- | --- | --- | --- |
| `?.` | Safe Call | null 가능성이 있는 객체의 속성이나 메서드 안전하게 호출 | `val length = str?.length` |
| `?:` | Elvis 연산자 | 좌변이 null이 아니면 좌변 값 반환, null이면 우변 값 반환 | `val name = str ?: "Unknown"` |
| `!!` | Not-null assertion | null 가능성이 있는 값을 강제로 non-null로 취급 (null이면 예외 발생) | `val length = str!!.length` |
| `..` | Range | 범위 생성 | `for (i in 1..5)` |
| `in` | Contains/Membership | 값이 범위나 컬렉션에 포함되어 있는지 확인 | `if (x in 1..10)` |
| `!in` | Not Contains | 값이 범위나 컬렉션에 포함되어 있지 않은지 확인 | `if (x !in 1..10)` |
| `is` | Type Check | 객체가 특정 타입인지 확인 | `if (obj is String)` |
| `!is` | Not Type Check | 객체가 특정 타입이 아닌지 확인 | `if (obj !is String)` |

</details>  

```kotlin
// 값 설정
fun main(){
    qwe@for(i in 0..10){
        for(j in 0..10){
            if(i ==0 && j == 3){
                break@qwe
            }
            println("$i, $j")
        }
    }
}

출력:
0, 0
0, 1
0, 2
```

## 8. 클래스  
### 기본형
클래스 형태는 class 클래스 이름(속성 이름: type)  
자바랑 다르게 코틀린은 생성자를 따로 만들어 주지 않아도 된다.  
객체를 생성할 때 속성 따라 값을 입력해주면 된다.  
```kotlin
// 값 설정
fun main(){
    var a = Prs("awd", 23)

    println("${a.birth} ${a.name}")
    a.introduce()
}

class Prs(var name:String, val birth:Int){
    fun introduce(){
        println("$name $birth")
    }
}

출력:
23 awd
        awd 23
```  
### 