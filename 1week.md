## :cactus:  JVM은 무엇이며 자바 코드는 어떻게 실행하는 것인가

[TOC]

### :heavy_check_mark: 목표

- 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기

  

### :heavy_check_mark: 학습할 것

---

#### - JVM이란 무엇인가

> **(Java Virtual Machine, 자바 가상머신)**
>
> Java로 개발한 프로그램을 컴파일했을때 생성되는 바이트코드를 실행시키기 위한 **스택기반의 가상의 머신임**
>
> JVM은 크게 두가지 기본기능이 있음
>
> 1. **자바 프로그램이 어느 기기, 어느 운영체제 상에서도 실행될 수 있게 하는것**
>    `"Write Once, Run AnyWhere"`
>
> 2. **프로그램 메모리를 관리하고 최적화 하는 것**
>
>    `"Garbage Collection"`



#### - 컴파일 하는 방법

> 1. 개발자가 자바 소스코드(.java) 작성
>
>    - 소스코드명.java
>
>      ```java
>      public class 클래스명{
>      	public static void main(String[] str){
>      		System.out.println("Hello Java");
>      	}
>      }
>      ```
>
> 2. 자바컴파일러( javac ; JDK소속 )를 이용하여 자바 소스코드 컴파일
>
>    ```
>     javac 소스코드명.java
>    ```
>    `>>` 클래스명.class 생성



#### - 실행하는 방법

>1. java 명령어( JRE소속 )로 JVM 구동
>
>   ```
>   java 클래스명
>   ```
>
>2.  컴파일된 바이트코드를 JVM 클래스로더에 전달
>
>   - ###### 클래스로더 동작 과정
>
>     - 로드 : 클래스 파일(.class)을 가져와서 JVM 메모리에 로드
>       - Bootstrap ClassLoader
>       - Extention ClassLoader
>       - Application ClassLoader
>     - 검증 : 자바언어명세 및 JVM 명세에 명시된 대로 구성되어있는지 검사 ( => .class 파일이 유효한지 검사 )
>     - 준비 : 클래스가 필요로하는 메모리 할당
>     - 분석 : 클래스의 상수 풀 내 모든 심볼릭 레퍼런스를 다이렉트 레퍼런스로 변경
>        ( => 심볼릭(명확하게 정의되지 않은) 레퍼런스를 메서드영역에 있는 실제 레퍼런스로 교체 )
>     - 초기화 : 클래스 변수들을 적절한 값으로 초기화 ( =>static 변수의 값 할당, static 블럭이 이때 실행됨 )
>
>3. 실행엔진을 통해 실행 (인터프리터랑, JIT 컴파일러)
>
>   `>>` Hello Java

- ref : https://gyoogle.dev/blog/computer-language/Java/%EC%BB%B4%ED%8C%8C%EC%9D%BC%20%EA%B3%BC%EC%A0%95.html



#### - 바이트코드란 무엇인가

> = 중간코드
>
> JVM이 이해할 수 있는 언어, JVM이 실행하는 명령어 집합
>
> 컴파일 했을 때 생기는 .class 파일이 바이트코드로 구성됨
>
> 명령어 크기가 1바이트라 바이트코드라 불린다고..

- ref : https://kingsubin.tistory.com/248

  

#### - JIT 컴파일러란 무엇이며 어떻게 동작하는지

> **( Just-In-Time Complier, JIT 컴파일러 )**
>
> 바이트코드를 기계어로 변환해주는 친구
>
> 바이트코드 내에서 반복적으로 수행되는 부분이 있으면 JIT컴파일러가 해당부분을 캐시에 기억해뒀다가 재사용함으로써 **프로그램 실행에 걸리는 시간을 단축해줌**



#### - JVM 구성요소

> JVM구성요소는 크게 3가지로 구성됨
>
> - **클래스 로더 시스템 (Class Loader)**
>   - 클래스를 읽어오는 시스템
>   - [동작과정](#클래스로더-동작-과정)
>     - 로딩 / 연결 ( 검증,준비,분석 ) / 초기화
> - **메모리 (JVM Memory) == 런타임 데이터 영역 (Runtime Data Areas)**
>   - 메서드
>     - 모든 스레드가 공유하는 영역으로 JVM이 시작될 때 생성됨
>     - 클레스 수준(런타임 상수 풀, 필드와 메서드에 대한 정보, Static변수, 메서드의 바이트코드 등)의 정보를 저장함
>   - 힙
>     - 인스턴스 또는 객체를 저장하는 공간, 가비지컬렉션 대상
>   - 스택 (JVM Stack)
>     - LIFO(Last IN First Out)동작으로 동작하는 자료구조로써, 각 스레드마다 하나씩 존재
>     - 스택은 공유자원이 아니라 스레드에 안전함
>   - PC 레지스터
>     - 현재 실행중인 JVM 명령의 메모리 주소가 저장되며, 각 스레드마다 하나씩 존재
>   - Native Method Stack
>     - Java 외의 언어(C, C++ 등)로 작성된 네이티브코드를 위한 스택
> - **실행엔진 (Execution Engine)**
>   - 인터프리터 : 바이트코드 명령어를 한줄씩 읽어서 해석하고 실행
>   - JIT compiler : 인터프리터 방식의 단점 보완, 캐싱 방식으로 빠르게 수행

- ref : https://steady-snail.tistory.com/67

#### - JDK와 JRE의 차이

>- **JDK : (Java Development kit ) : 개발이 목적일 경우**
>
>   - JDK = JRE + tools to develop application
>
>- **JRE : (Java Runtime Enviroment) : 이미 개발된 프로그램 실행이 목적인 경우**
>   - JRE = JVM +libraries to run application
>
>
> <figure align="center">
>     <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbdyAwE%2FbtqM4zPa2T4%2F5qOskY2htyUYDxJBHTDE3K%2Fimg.png">
>     <figcaption>
>     JDK, JRE, JVM 차이
>     </figcaption>
> </figure>

- ref : https://catch-me-java.tistory.com/11?category=438116
- ref : https://howtodoinjava.com/java/basics/jdk-jre-jvm/



### :heavy_check_mark: JVM 아키텍쳐

![아키텍쳐](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb0VlMd%2FbtqAgEhsKL7%2Fv0QKQkqe38VTRurO23Tr31%2Fimg.png)

- ref : https://dzone.com/articles/jvm-architecture-explained