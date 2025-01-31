---
layout: single
title:  "Java 예외처리 #1"
---
## 예외처리 Exception handing
- **에러(Error)** : 프로그램 코드에 의해서 수습될 수 없는 심각한 오류
- **예외(Exception)** : 프로그램 코드에 의해서 수습될 수 있는 다소 미약한 오류

자바에서는 실행 시 발생할 수 있는 오류(Exception과 Error)를 클래스로 정의하였다.  

<img width="293" alt="Exception-image-01" src="https://user-images.githubusercontent.com/97990285/154825519-21368238-015d-4598-8d81-3c268d9bf365.png">

**RuntimeException클래스**들은 주로 프로그래머의 실수에 의해서 발생될 수 있는 예외들로,  
자바의 프로그래밍 요소들과 관계가 깊다.  
그 외의 **Exception클래스**들은 주로 외부의 영향으로 발생하는 있는 걸들로서,  
프로그램의 사용자들의 동작에 의해서 발생하는 경우가 많다.  
<br>

### 예외처리하기 try-catch문
> **정의** - 프로그램 실행 시 발생할 수 있는 예외에 대비한 코드를 작성하는 것  
> **목적** - 프로그램의 비정상 종료를 막고, 정상적인 실행상태를 유지하는 것  
<br>

#### try-catch문에서의 흐름
> ▶**try블럭 내에서 예외가 발생한 경우,**  
> 1. 발생한 예외와 일치하는 catch블럭이 있는지 확인한다.  
> 2. 일치하는 catch블럭을 찾게 되면, 그 catch블럭 내의 문장들을 수해하고 전체 try-catch문을  
>   빠져나가서 그 다음 문장을 계속해서 수행한다. 만일 일치하는 catch블럭을 찾지 못하면, 예외는 처리되지 못한다.   
> 
> ▶**try블럭 내에서 예외가 발생하지 않은 경우,**  
> 1. catch블럭을 거치지 않고 전체 try-catch문을 빠져나가서 수행을 계속한다.  

try블럭에서 예외가 발생하면, 예외가 발생한 위치 이후에 있는 try블럭의 문장들은 수행되지 않으므로,  
try블럭에 포함시킬 코드의 범위를 잘 선택해야한다.  
<br>

#### catch블럭의 동작
첫 번째 catch블럭부터 차례로 내려가면서 catch블럭의 괄호()내에 선언된 참조변수의 종류와  
생성된 예외클래스의 인스턴스에 instanceof연산자를 이용해서 검사하게 되는데,  
검사결과가 true인 catch블럭을 만날 때까지 검사는 계속된다.  
검사결과가 true인 catch블럭을 찾게 되면 블럭에 있는 문장들을 모두 수행한 후에  
try-catch문을 빠져나가고 예외는 처리되지만, 검사결과가 true인 catch블럭이 하나도 없으면  
예외는 처리되지 않는다.  

- printStackTrace() : 예외발생 당시의 호출스택(Call Stack)에 있었던 메서드의 정보와 예외 메시지를 화면에 출력한다.
- getMessage() : 발생한 예외클래스의 인스턴스에 저장된 메시지를 얻을 수 있다.  

```java
try{
  Exception e = new Exception("고의로 발생시켰음.");
  throw e; //고의로 발생시킴
} catch (Exception e){
  System.out.println("에러 메시지 : "+ e.getMessage());
  e.printStackTrace();
}
System.out.println("프로그램이 정상 종료 되었습니다.");
```  
Exception 인스턴스를 생성할 때, 생성자에 String을 넣어 주면,  
이 String이 Exception 인스턴스에 메시지로 저장된다.  
이 메시지는 getMessage()를 이용해서 얻을 수 있다. 

