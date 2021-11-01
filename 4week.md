## :cactus:  제어문

[TOC]

### :heavy_check_mark: 목표

- 자바가 제공하는 제어문을 학습하세용

  

### :heavy_check_mark: 학습할 것

---

#### - 선택문

> Decision-making Statement ; 선택문
>
> - if-then문
>
>   - 지정한 조건이 만족할 시에 블록안에 있는 코드가 실행됨. if-then문 안에 코드가 한줄이라면, {} 생략 가능
>
>   ```java
>   if (조건식) {
>   	조건이 참일 경우 실행되는 코드;
>   }
>   ```
>
> - if-then-else
>
>   - if-then은 참일 경우만 실행이 됐다면, if-then-else는 거짓에도 실행할 수 있음
>
>   ```java
>   if (조건식) {
>   	참일 경우;
>   }else{
>   	거짓일 경우;
>   }
>   ```
>
>   - 여러 조건에는 else if 사용
>
> - switch
>
>   - switch문은 if-then과 if-then-else문과 다르게 변수에 대해 평가를 하고, 이를 분기할 수 있음
>   - 평가 당하는 변수는 원시형 타입(int,byte,char...)일 수도 있고, Enum형 혹은 String, Wrapper(Integer, Byte, Character...) 클래스도 가능함
>
>   ```java
>   switch(변수) {
>   	case 값 A:
>   		변수가 값 A에 해당하는 경우;
>   		break;
>   	case 값 B: 변수가 값 B에 해당하는 경우;
>   		break;
>   	default: 어떠한 값에도 해당하지 않는 경우;
>   		break;
>   }
>   ```

- ref : https://juntcom.tistory.com/118



#### - 반복문

> Looping Statement ; 반복문
>
> - for
>
>   - 프로그래머가 설정한 조건이 만족될 때까지 지정한 코드블럭이 계속해서 수행됨
>
>   ```java
>   for (초기식;조건식;증감식){
>   	반복될 코드;
>   }
>   ```
>
>   - JDK 5.0 이상부터 배열 혹은 컬렉션 순회시, 다음과 같이 for문 사용 가능
>
>   ```java
>   for(타입 변수명 : 배열/컬렉션) {
>   	반복될 코드;
>   }
>   ```
>
> - for each 스타일 for문
>
>   - 어떤 컬렉션이든 순회할 수 있음
>   - for문보다는 for-each 사용, for-each문은 반복자나 인덱스 변수를 제거해 오류 가능성을 줄임
>
>   ```java
>   int[] nums = {1,2,3,4,5};
>   for (int num : nums) {
>   	System.out.println(num);
>   }
>   ```
>
> - While
>
>   - 특정 조건이 참일 경우, 지정한 코드 블럭이 계속해서 수행되는 구문
>
>   ```java
>   while(조건식) {
>   	조건식이 참일 경우 반복되는 코드;
>   }
>   ```
>
> - do-while
>
>   - while문이 조건식을 판별하고 코드를 수행했다면, do-while문은 먼저 코드블럭을 수행할 조건을 판별함
>
>   ```java
>   do {
>   	조건식이 참일 경우 반복되는 코드;
>   }whlie(조건식);
>   ```

- ref : https://juntcom.tistory.com/118



---

### :heavy_check_mark: 과제 (옵션)

#### - 과제0. JUnit 5 학습

#### - 과제 1. live-study 대시 보드 만드는 코드 작성

#### - 과제 2. LinkedList 구현

#### - 과제 3. Stack 구현

#### - 과제 4. 앞서 만든 ListNode를 사용해서 Stack 구현

#### - 과제 5. Queue 구현