---
title: "유튜브 리뷰 - 코딩의 실 아샬(03/19) "
excerpt: "코딩을 하기 전에 할 일"
classes: wide
categories:
 - youtube review
tags:
 - Clean code
 - 아샬
last_modified_at: 2020-03-19
---



## [코딩을 하기 전에 할 일](https://youtu.be/N4FV788fNiQ)

* 코딩을 하기 전에 충분히 계획을 세우고 하자.
* 어떤 문제를 해결하려 하는가? (요구사항을 명확하게 하자)
  * 내가 만드려는 프로그램이 어떤 프로그램인지 명확하게 해야 내가 의도한 프로그램을 만들 수 있다.
* 요구사항을 명확하게 했으면 그다음은 명세를 명확하게 하자
  * 의도한 프로그램이 타이머 라고 한다면, min을 받을치 sec을 받을지 고민해보는 식으로
  * 명세에 대한 여러 예제(테스트 코드)를 만들어 본다.
  * 명세에 적힌대로 작동하지 않는 것들을 버그라고 한다.
* 이제 명세에 따라서 설계를 한다.
  * 이전 단계들이 명확하게 해야하는 단계라면 설계는 간단하게
* 코딩을 하면서 잘못된 설계가 있는지 인지하고 설계를 수정하고 코드도 수정한다. 또 기능을 추가하면서 또 설계를 수정하고, 수정한 설계에 따라 코드도 수정하는 과정을 계속 반복한다.
  * 이 과정에서 요구사항과 명세를 명확하게 해놨다면, 설계나 코드가 바뀌어도 안전하게 대처할 수 있다.

* 이제 프로그램을 만드는 과정에서 여러가지 피드백을 통해 배움을 얻는다. 잘못된것이 있으면 찾아서 고치면서 배울 수 있다.



* 요구사항과 명세를 명확하게 해야한다 라는 말에서 TDD 생각이 났다.. 작은 요구사항부터 시작해서 그것에 대한 명세(주어진 인자값 등?)를 제시하고 그 요구사항만 충족하는 설계와 코드를 작성하고 요구사항을 조금씩 추가하면서 재설계와 코드 리팩토링을 통해 최종적으로 만들고자 하는것을 만들수있다.. 이런 느낌