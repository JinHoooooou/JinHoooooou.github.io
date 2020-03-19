---
title: "유튜브 리뷰 - 코딩의 실 아샬(03/12) "
excerpt: "코드를 컴퓨터가 아니라 머리로 실행하면 어떻게 될까?"

categories:
 - Blog
tags:
 - Git
 - Youtube
 - Review
last_modified_at: 2020-03-12
---



## [코드를 컴퓨터가 아니라 머리로 실행하면 어떻게 될까?](https://youtu.be/hq5AiaLsZFM)

* 코드를 보고 결과값을 예측할 수 있는가?
  * 그냥 프로그램 실행하면 확인 할 수 있는데?
  * 예측 해야한다.
* 영상에서 얘기하고자 하는것은 예측할 수 있어야한다!
  * 우리가 혹은 남이 작성한 코드를 봤을 때 가지고 있는 가정, 요구사항, 순서, 환경, 결과 등을 추론할 수 있어야한다.
  * 모든 코드가 우리가 예측하기 좋은 코드인가?
    * 에측하기 좋은 코드는 인자를 무엇을 주었을때 어떤 결과값이 나온다, 어떤 환경이 주어졌을때 어떤 결과가나온다. 등을 쉽게 추론 할 수 있는 코드가 읽기 좋고 예측하기 좋은 코드이다.
  * 한번에 추론하기 복잡한 문제들도 있다. 그런경우는 좀 더 작은 단위로 쪼개서 추론한다.
    * 작은 단위로 쪼개는 방법은 단위 테스트이다. 



* 얼마전에 본 '디버거를 안 쓰는 개발자가 있다고?'에서 나온 얘기랑 비슷한 얘기이다.
* 중단점을 걸고 step단위로 파고들어서 문제를 파악하고 해결하는것보다, 논리적으로 구조적으로 문제를 파악할 수 있는 코드가 읽기 쉬운코드이다라고 말하는것 같다. 그것을 뒷받침하는것이 바로 단위 테스트이다.
* 이 분 영상 많은 부분이 단위 테스트에 대한 얘기를 하시는데, 얼마전에 내가 푼 코드워즈 문제들을 다시 확인하려고 문제들을 볼 때 테스트 코드를 먼저 보니 어떤 문제였는지 파악이 가능했다. 그 때 테스트 코드를 잘 작성 해 놓으면 전체적인 overview가 된다는 것을 느꼈다.