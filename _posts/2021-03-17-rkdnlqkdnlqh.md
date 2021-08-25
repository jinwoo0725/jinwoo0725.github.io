---
layout: single
title: "Q1, Q2 jw"
---

[문제 상황]  
가위, 바위, 보 게임을 만들어 봅시다. 게임 제작 조건이 다음과 같을 때 출력 결과와 같이 진  
행되도록 프로그램을 작성해 보시오.  
  
<처리 조건>  
§ 가위는 's', 바위는 'r', 보는 'p'로 표현한다. § 컴퓨터는 리스트 com=['s', 'r', 'r', 's', 'p' ]를 가지 있  
으며, 게임이 시작될 때 리스트에서 차례대로 한 개의 값을 할당받는다. 마지막 값까지 할  
당하고 나면 다시 처음 값부터 할당한다. § 사용자는 직접's/r/p' 중에 하나를 입력한다. 이것은 별도의 함수 game()로 구현한다.  
§ 게임 한번 당 판정은 '비겼다/이겼다/졌다'로 나타낸다. 이것은 별도의 함수 win(u, c)으로  
구현한다. § 승리한 게임의 수를 사용자와 컴퓨터가 별도로 보관했다가 게임을 종료할 때 승자를 알린다.

[문제 해결]  
~~~python
def game():
  global u
  global c
  u = input("가위:s/바위:r/보:p ==>")
  c = com[a]

def win(u, c):
  global w, l
  if ( u == 's' and c == 'r' ) or ( u == 'r' and c == 'p' ) or ( u == 'p' and c == 's' ):
    print("졌다")
    l += 1
  elif u == c:
    print("비겼다")
  else:
    print("이겼다")
    w += 1
    

Running = True
a = 0
w = 0
l = 0
com=['s', 'r', 'r', 's', 'p' ]

while Running:
  a = a % 5
  game()
  win(u,c)
  run = input("한 게임 더 할까요(y/n)?")
  if run == 'n':
    Running = False
    if w > l:
      print("사용자 승리!")
    elif l > w:
      print("컴퓨터 승리!")
    else:
      print("무승부")
  else:
    a = a + 1   

~~~
[결과]  
~~~
가위:s/바위:r/보:p ==>s
비겼다
한 게임 더 할까요(y/n)?y
가위:s/바위:r/보:p ==>s
졌다
한 게임 더 할까요(y/n)?y
가위:s/바위:r/보:p ==>p
이겼다
한 게임 더 할까요(y/n)?y
가위:s/바위:r/보:p ==>r
이겼다
한 게임 더 할까요(y/n)?y
가위:s/바위:r/보:p ==>r
졌다
한 게임 더 할까요(y/n)?y
가위:s/바위:r/보:p ==>r
이겼다
한 게임 더 할까요(y/n)?n
사용자 승리!
~~~
