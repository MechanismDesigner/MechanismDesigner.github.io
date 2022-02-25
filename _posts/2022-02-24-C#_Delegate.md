---
layout: single
title:  "C# 기타 문법 : Delegate(대리자)"
---





# 🧾**Delegate**

[TOC]

## 0️⃣Delegate(대리자) 개념

💬 들어가기 앞서 "버튼이 눌렸을 때 호출되는 ButtonPressed() 메서드"를 예로 들자. 

```c#
static void ButtonPressed(/*호출 할 메서드들의 인자들*/)
{
    TestMethod1(); // 호출 할 메서드1
    TestMethod2(); // 호출 할 메서드2
    TestMethod3(); // 호출 할 메서드3
    // ...
}
```

💬 여기서 대리자를 이용하면, 호출 할 메서드들을 **래핑**해 대리자로 대신 호출할 수 있다.

​    *📑래핑 : "묶는다, 담는다, 연결하다 등" 으로 이해하면 된다.* 

```c#
static void ButtonPressed(OnClicked clicked/*<- 대리자 : 대리자를 인자로 넘겨줌.*/)
{
    clicked();// 대리자를 호출.  메서드1, 메서드2, 메서드3 가 차례대로 호출
}
```



## 1️⃣Delegate(대리자) 선언 & 체인

💬 대리자를 선언해보자.

```c#
public delegate int OnClicked(); // OnClicked 델리게이트(대리자) 선언!
OnClicked clicked; 			  // 델리게이트(대리자) 변수를 꼭 선언 해줘야된다.
```

📘 리턴값이 int형, 인자값이 없는 메서드를 OnClicked에 **래핑**할 수 있다. 



## 2️⃣Delegate(대리자) 래핑

💬 대리자에 메서드를 래핑해보자.

```c#
OnClicked clicked = new OnClicked(TestMethod1); // 방법 1 - TestMethod1을 clicked에 래핑
clicked += TestMethod2;							// 방법 2 - 체인만들기 TestMethod1 + TestMethod2
clicked -= TestMethod2;							// 방법 3 - 체인 제거
clicked = TestMethod3;							// 방법 4 - clicked에 TestMethod3만 래핑
```

📘 대리자에 여러 메서드를 래핑할 수 있다. 이렇게 대리자를 통해 여러개를 래핑한 메서드들의 호출 목록을 **체인**이라고 한다. 여기서는 대리자를 통해 호출 목록을 만들었으니 **델리게이트 체인**이라고 부른다.

📘 대리자를 호출시켜 여러 메서드를 호출할 수 있다. 이렇게 여러 메서드를 호출하는 걸 **멀티캐스트**라고 한다. 여기서는 대리자를 통해 여러 메서드를 호출했으니 **멀티캐스트 대리자**라고 한다.



## 3️⃣Delegate(대리자) 호출(활용)

💬 대리자를 호출해보자.





📣 몰라도 지장없는 TMI (MicrosoftDoc출저)

1. C / C++의 함수포인터처럼 메서드를 안전하게 캡슐화하는 형식이다.
2. 함수포인터와 달리 대리자는 개체 지향적이고 형식이 안전하며 보안이 유지된다.
