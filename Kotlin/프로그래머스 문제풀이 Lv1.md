# 프로그래머스 문제풀이 Lv.0
오현석 2025.06.05  
코딩테스트 연습 > 코딩테스트 입문  
정답률 높은 순
***
## 01 나머지 구하기
정수 num1, num2가 매개변수로 주어질 때, num1를 num2로 나눈 나머지를 return 하도록 solution 함수를 완성해주세요.  
  
### 내 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int): Int {
        var answer: Int = num1 % num2
        return answer
    }
}
```  
### 모범 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = num1 % num2
}
```  
## 02 두 수의 차 구하기  
정수 num1과 num2가 주어질 때, num1에서 num2를 뺀 값을 return하도록 soltuion 함수를 완성해주세요.  

### 내 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int): Int {
        var answer: Int = num1 - num2
        return answer
    }
}
```  
### 모범 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = num1 - num2
}
```  
## 03 숫자 비교하기  
정수 num1과 num2가 매개변수로 주어집니다. 두 수가 같으면 1 다르면 -1을 retrun하도록 solution 함수를 완성해주세요.  

### 내 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int): Int {
        var answer: Int = 0
        if(num1 == num2){
            answer = 1
        } else{
            answer = -1
        }
        return answer
    }
}
```  
*answer = if(num1 == num2) 이런식으로 answer자체에 if문을 넣을 수도 있음*

### 모범 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = if(num1==num2) 1 else -1
}
```  
## 04 나이 출력
머쓱이는 선생님이 몇 년도에 태어났는지 궁금해졌습니다. 2022년 기준 선생님의 나이 age가 주어질 때, 선생님의 출생 연도를 return 하는 solution 함수를 완성해주세요  

### 내 답
```kotlin
class Solution {
    fun solution(age: Int): Int {
        var answer: Int = 0
        answer = 2023 - age
        return answer
    }
}
```  
### 모범 답
```kotlin
class Solution {
    fun solution(age: Int): Int = 2022 - (age - 1)
}

```  
## 05 두 수의 나눗셈
정수 num1과 num2가 매개변수로 주어질 때, num1을 num2로 나눈 값에 1,000을 곱한 후 정수 부분을 return 하도록 solution 함수를 완성해주세요.

### 내 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int): Int {
        var answer = num1.toDouble() / num2
        return (answer * 1000).toInt()
    }
}
*형변환을 통해 정수형과 실수형을 나누어 계산 후 출력해야함*
```  
### 모범 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int): Int {
        var answer = num1.toDouble() / num2
        return (answer * 1000).toInt()
    }
}
```  
## 06 몫 구하기
정수 num1, num2가 매개변수로 주어질 때, num1을 num2로 나눈 몫을 return 하도록 solution 함수를 완성해주세요.

### 내 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = if(num1==num2) 1 else -1
}
```  
### 모범 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = if(num1==num2) 1 else -1
}
```  
## 05 두 수의 나눗셈
정수 num1과 num2가 매개변수로 주어질 때, num1을 num2로 나눈 값에 1,000을 곱한 후 정수 부분을 return 하도록 solution 함수를 완성해주세요.

### 내 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = if(num1==num2) 1 else -1
}
```  
### 모범 답
```kotlin
class Solution {
    fun solution(num1: Int, num2: Int) = if(num1==num2) 1 else -1
}
```  