---
title: "[Reading Book]Refactoring(2)"
excerpt: "4장 테스트 만들기"
classes: wide
categories:
 - Book
tags:
 - clean code
 - refactoring
last_modified_at: 2020-04-28
---



# 4장 테스트 만들기

리팩토링을 하고자 할 때 테스트는 없어서는 안 될 필수조건이다. 잘 짜여진 테스트는 프로그래밍을 빠르게 한다.

### 4.1 자체 테스트 코드의 가치

* 대부분의 프로그래머들은 코드를 작성하는 시간보다 디버깅 등 코드를 보는 시간이 더 많다.
* 코드의 결과를 콘솔에 출력하여 확인하는 테스트 대신, 컴퓨터가 그 테스트를 스스로 하도록 할 수 있다. 기대하는 결과를 테스트 코드에 넣고 실제로 그렇게 나오는지 비교하는것이다.
  * 🙋‍♂️ 처음 읽었을 때 이게 뭔소린가 했는데.. 그냥 내가 JUnit쓰는것처럼 실제값과 기댓값 확인하는거 얘기하는것이다.
* 자체 테스트 코드를 작성하는 것은 테스트 뿐만 아니라 강력한 버그 탐지기이다.
* 테스트 작성을 배운적이 없거나 생각해보지 않았다거나, 테스트 수작업이 지루한 이유 등 때문에 테스트를 하지 않는다. 그러나 자동으로 테스트를 확인하다면 테스트 작성이 재미있을 수 있다.
  * 🙋‍♂️ 매우 동의한다. 나는 '테스트'라는 용어로 쓰지않고 그냥 실행돌려서 콘솔로 확인해보고 내가 예상한 결과값이 나오지 않았을 때 디버깅 포인트를 잡고 디버깅으로 확인하거나 print 메서드로 출력값을 확인했었다. 그런데 JUnit이라는 강력한 테스트 프레임워크를 사용한 이후로는 테스트 작성을 안하면 뭔가 불안하다. 내가 작성하는 코드가 맞는지 확인하기 위해서는 테스트가 반드시 필요하다. 또한 디버깅을 할 때도 어느 지점에서 오류가 난건지 예측이 쉽게 가능하다.
* 테스트를 작성하기 좋은 시점은 프로그래밍을 시작하기 전이다. 
  * 기능을 추가하기 전에 테스트 부터 작성하여 기능을 추가하기 위해서 무엇을 해야할지 명확히 정할 수 있다. 
  * 기능 구현보다 인터페이스에 집중할 수 있다.
  * 코드 작성을 완료할 명확한 지점(테스트를 통과하는 지점)을 갖게된다.

### 4.2 JUnit 테스트 프레임워크

* 🙋‍♂️ 이책 판수가 2000년대 초반이다. 지금은 2020년인데 JUnit5를 사용한다.. 그래서 대부분 아는 얘기이고 바뀐 내용도 어느정도 있어서 그냥 내가 중요하다고 생각하는 부분만 작성한다.
* 테스트는 빨라야 한다. 리팩토링을 할 때는 작업하고 있는 코드만 테스트를 실행시켜야 한다.
* **단위 테스트와 기능 테스트**
  * 단위 테스트는 범위가 매우 한정적이다. 각각 테스트 클래스는 하나의 패키지 내에서 작동한다. 다른 패키지에 대한 인터페이스는 테스트 하지만 그 이상은 잘 작동하는 것으로 간주한다.
  * 기능 테스트는 소프트웨어 전체가 제대로 작동하는지를 확인한다. 기능 테스트는 사용자에게 확실한 품질을 제공하지만 프로그래머의 생산성은 고려하지 않는다.
  * 소프트웨어에서 버그를 발견한 경우 적어도 **두 가지** 조치를 취해야한다.
    * 버그를 드러낼 수 있는 단위 테스트를 작성한다.
    * 버그가 있는 코드를 수정한다.
  * 단위 테스트는 버그를 찾아내는데 도움을 줄 뿐 아니라, 비슷한 버그가 나오지 못하도록 돕는다.

### 4.3 테스트 추가하기

* 테스트는 문제가 생길만한 곳에 집중되어야 한다. 너무 많은 테스트를 작성하려다 보면 오히려 소홀해질 수 있기 때문이다.
* 테스트를 할 떄 경계 조건을 잘 확인해야한다. 무언가가 잘못 되었을 때는 경계 조건을 생각하고 테스트를 경계 조건에 집중해야한다.
* 테스트에 살을 붙여 나가면서 클래스의 인터페이스에 대한 이해를 돕고, 에러가 발생하는 조건과 경계 조건에 대해 생각하는 것을 돕는다.
  * 🙋‍♂️ 확실히 예외를 생각하는데 도움을 주는것은 그동안 문제를 풀면서 느꼈다. 그러나 아직은 객체에 대한 이해를 돕는 범위까진 가지 못했다. 이것은 내가 객체지향 패턴에 대해 더 공부를 해야할것 같다.
* 테스트 코드가 모든 버그를 잡을 수는 없다. 그러나 그 걱정 때문에 대부분의 버그를 확실하게 잡을 수 있는 테스트를 만들지 않는것은 큰 손해이다.



##### 좋은 버그 탐지기를 만들고 자주 실행시켜라. 테스트는 어느 개발에서나 훌륭한 도구이고, 리팩토링을 위한 필수조건이다.
