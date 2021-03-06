---
title: "[MVC] MVC패턴1"
excerpt: "Model, View, Controller"

categories:
 - TIL
tags:
 - TIL
 - MVC
 - Java
 - Spring
last_modified_at: 2020-02-03
---



## 그냥 쓰니까 쓰고있었다.

학교에서 소프트웨어 프로젝트 과목중 Spring을 이용하여 웹 게시판을 만드는 과제가 있었다. 그 때 Spring이라는 프레임워크를 처음 접해보고, 튜토리얼을 따라가다보니 여러가지 처음 접해본것이 많았다.

Tomcat, DB, MVC패턴, xml, jsp, 등등.. 많았는데, 기초지식없이 그저 튜토리얼을 따라가다보니 나도모르게 웹 게시판이 완성되어있었다. 거기서 더 관심을 가지고 여러가지 용어들이나 배운 지식들을 정리하고 다시 개인 프로젝트에 적용해보면 확실히 도움이 되었을거같은데, 그저 과제하는 수준으로만 얕게 공부하고 나니 다 까먹었다.

그러고 반년전에 선배 두명과 프로젝트를 하게되었는데(결국 중단됐지만..) 거기서 Spring boot를 다시 사용하게 되었다. 나는 당연히 학교 프로젝트때 했으니까 알겠지하고 뛰어들었는데 진짜 모르는거 투성이었다.. 알더라도 엄청 얕은지식만 가지고있었고... 그래서 그때 다시 공부하면서 개발을 시작했는데 역시나 지금도 다 까먹었다.

까먹는걸 방지하기위해서 블로그에 정리하고 내가 또 까먹으면 내가 짠 코드들이랑 정리내용보고 리마인드하는게 좋을거같아 정리한다.



## MVC란?

위키백과에서는 MVC를 다음과 같이 설명한다.

> MVC(Model-View-Controller)는 소프트웨어 공학에서 사용되는 디자인 패턴이다. 이를 이용하여 사용자 인터페이스에서 비즈니스 로직을 분리하여 애플리케이션의 시각적 요소나 그 이면에서 실행되는 비즈니스 로직을 서로 영향 없이 고칠 수 있는 애플리케이션을 만들 수 있다.
>
> MVC에서 모델은 애플리케이션의 데이터를 나타내며, 뷰는 텍스트나 체크박스 항목같은 사용자 인터페이스 요소를 나타내고, 컨트롤러는 데이터와 비즈니스 로직 사이의 상호동작을 관리한다.
>
> >  비즈니스 로직 : 뷰에게 전달하기 전에 데이터를 가공하는 코드들
> >
> > 참고 post : https://mommoo.tistory.com/67	

내가 알고 있는 지식을 동원해서 생각해보면, 클라이언트가 어떠한 요청을 보내면, 서버에서는 해당 요청을 컨트롤러에서 받아서 모델에서 해당 요청에 대한 데이터를 가공하고 뷰로 전달하여 클라이언트에게 보여준다.

![image-20200203141434653]({{site.url}}/assets/images/2020-02-03-TIL-MVC-pattern-1-MVC.png)

* Model

  사용자가 입력한 데이터나 사용자에게 출력할 데이터를 다룬다. 

  1. Model은 사용자가 편집하길 원하는 모든 데이터를 가지고 있어야한다.
     * 웹에서 회원가입 정보를 입력한다면 이름, 아이디, 패스워드, 이메일 등등 정보를 입력할텐데 그에 대한 모든 데이터를 model이 가지고 있어야 해당 데이터를 다룰 수 있다.
  2. View나 Controller에 대한 어느 정보도 알지 말아야한다.
  3. Model의 상태에 변화가 일어나면, 통보에 대한 처리를 구현해야한다.
     * Model 상태 변화(닉네임 변경 같은)가 일어나면 이벤트를 발생시켜 Controller에 전달해야한다. 또한 Model은 재사용 가능해야한다.

* View

  텍스트, 체크박스 항목 등 사용자 인터페이스 요소를 나타낸다.

  1. Model이 가지고 있는 정보를 따로 저장해서는 안된다.
     * 화면에 텍스트를 표시하기 위해, 전달받은 모델의 정보를 View내에 따로 저장해서는 안된다.
  2. Model이나 Controller와 같이 다른 구성요소를 알지 말아야한다.
     * View는 데이터를 받으면 화면에 표시해주는 역할만 가진다.
  3. View의 상태에 변화가 일어나면, 통보에 대한 처리를 구현해야한다.

* Controller

  Model과 View를 잇는 다리역할을 한다. 즉, Model과 View 사이에 발생하는 이벤트들을 처리한다.

  1. Model과 View에 대한 정보를 알고 있어야한다.
     * Model과 View를 중재하기위해 둘에 대해서 알고 있어야한다.
  2. Model이나 View의 변화를 모니터링 해야한다.
     * Model과 View가 변하면 통보를하게 되는데 이를 모니터링하여 각 구성요소에 알려야한다.



## 왜 MVC를 사용할까??

다른 블로그들을 참조하거나 보면 결국엔 유지보수, 유연성에 대한 얘기가 항상나왔다. 사용자가 보는 페이지, 데이터처리, 그 중간역할로 구성하여 맡은 역할만 수행하게 되면 효율적이고, 유지보수, 확장성, 유연성을 가지게 된다고 봤다.

그러나 아직 나는 작은 프로젝트만 수행해왔고, 협업도 크게 해본적이 없기때문에 git을 공부했을때처럼 크게 와닿는 부분은 없다. 여러 프로젝트에 참여해보거나, 회사 실무경험을 가져보는게 확실히 도움이 될 거 같다..



### 참고자료

https://m.blog.naver.com/jhc9639/220967034588