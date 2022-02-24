---
layout: single
title:  "C# 기타 문법 : Delegate(대리자)"
---



# Delegate(대리자)

1. ★ delegate



```c#
 static void ButtonPressed(OnClicked clickedFunc/* 함수 자체를 인자로 넘겨줌.*/)
{
    clickedFunc();// 인자 함수를 호출.
}

static int TestDele()
{
    Console.WriteLine("델리게이트 테스트");
    return 0;
}

static int TestDele2()
{
    Console.WriteLine("델리게이트 테스트2");
    return 0;
}

static void Main(string[] args)
{
    // delegate1
    ButtonPressed(TestDele);

    // delegate2 체인기능
    OnClicked clicked = new OnClicked(TestDele);
    clicked += TestDele2;
    ButtonPressed(clicked);
}
```
}