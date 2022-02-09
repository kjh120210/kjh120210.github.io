---
title: "Python 스터디 3주차"
last_modified_at: 2022-0-09T18:49:00-05:00
categories:
  - Python
tags:
  - Python
  - Study
toc: true
toc_label: "파이썬 스터디"
toc_iocn: #
toc_sticky: true

---


## SW
### 1206번
<p><strong><span style="color:#000000">※ SW Expert 아카데미의 문제를 무단 복제하는 것을 금지합니다.</span></strong><br>
<span style="color:#000000">강변에 빌딩들이 옆으로 빽빽하게 밀집한 지역이 있다
이곳에서는 빌딩들이 너무 좌우로 밀집하여, 강에 대한 조망은 모든 세대에서 좋지만 왼쪽 또는 오른쪽 창문을 열었을 때 바로 앞에 옆 건물이 보이는 경우가 허다하였다.
그래서 이 지역에서는 왼쪽과 오른쪽으로 창문을 열었을 때, 양쪽 모두 거리 2 이상의 공간이 확보될 때 조망권이 확보된다고 말한다.<br>

빌딩들에 대한 정보가 주어질 때, 조망권이 확보된 세대의 수를 반환하는 프로그램을 작성하시오.

아래와 같이 강변에 8채의 빌딩이 있을 때, 연두색으로 색칠된 여섯 세대에서는 좌우로 2칸 이상의 공백이 존재하므로 조망권이 확보된다. 따라서 답은 6이 된다.</span></p>

<span style="color:#000000">A와 B로 표시된 세대의 경우는 왼쪽 조망은 2칸 이상 확보가 되었지만 오른쪽 조망은 한 칸 밖에 확보가 되지 않으므로 조망권을 확보하지 못하였다.
C의 경우는 반대로 오른쪽 조망은 2칸이 확보가 되었지만 왼쪽 조망이 한 칸 밖에 확보되지 않았다.

<strong>[제약 사항]</strong>
가로 길이는 항상 1000이하로 주어진다.
맨 왼쪽 두 칸과 맨 오른쪽 두 칸에는 건물이 지어지지 않는다. (예시에서 빨간색 땅 부분)
각 빌딩의 높이는 최대 255이다.
&nbsp;
<strong>[입력]</strong>
입력 파일의 첫 번째 줄에는 테스트케이스의 길이가 주어진다. 그 바로 다음 줄에 테스트 케이스가 주어진다.
총 10개의 테스트케이스가 주어진다.
&nbsp;<br>

```python
for i in range(1, 11):
    N = int(input())
    s = list(map(int, input().split()))
    num = 0
    
    for j in range(2, N-2):
        view_1 = s[j] - s[j-1]
        view_2 = s[j] - s[j-2]
        view_3 = s[j] - s[j+1]
        view_4 = s[j] - s[j+2]
        
        if view_1 > 0 and view_2 > 0 and view_3 > 0 and view_4 > 0:
            num += min(view_1, view_2, view_3, view_4)

    print(f'#{i} {num}')
```
### 1926번

3 6 9 게임을 프로그램으로 제작중이다. 게임 규칙은 다음과 같다.

1. 숫자 1부터 순서대로 차례대로 말하되, “3” “6” “9” 가 들어가 있는 수는 말하지 않는다.
  <strong>1 2 3 4 5 6 7 8 9…</strong>

2. "3" "6" "9"가 들어가 있는 수를 말하지 않는대신, 박수를 친다. 이 때, 박수는 해당 숫자가 들어간 개수만큼 쳐야 한다.  
예를 들어 숫자 35의 경우 박수 한 번, 숫자 36의 경우 박수를 두번 쳐야 한다.
 
입력으로 정수 N 이 주어졌을 때, 1~N 까지의 숫자를
게임 규칙에 맞게 출력하는 프로그램을 작성하라.
박수를 치는 부분은 숫자 대신, 박수 횟수에 맞게 “-“ 를 출력한다.
여기서 주의해야 할 것은 박수 한 번 칠 때는 - 이며, 박수를 두 번 칠 때는 - - 가 아닌 -- 이다. 


[제약사항]
N은 10이상 1,000이하의 정수이다. (10 ≤ N ≤ 1,000)
 
[입력]
입력으로 정수 N 이 주어진다.

[출력]
1 ~ N까지의 숫자를 게임 규칙에 맞게 출력한다.

```python
N = int(input())

for i in range(1, N+1):
    s = str(i)
    num = s.count('3')+s.count('6')+s.count('9')

    if num != 0:
        print('-'*num, end=' ')
    else:
        print(i, end = ' ')

```

### 2007번

패턴에서 반복되는 부분을 마디라고 부른다. 문자열을 입력 받아 마디의 길이를 출력하는 프로그램을 작성하라.

[제약 사항]
각 문자열의 길이는 30이다. 마디의 최대 길이는 10이다.


[입력]
가장 첫 줄에는 테스트 케이스의 개수 T가 주어지고, 그 아래로 각 테스트 케이스가 주어진다.
각 테스트 케이스의 첫 번째 줄에는 길이가 30인 문자열이 주어진다.


[출력]
출력의 각 줄은 '#t'로 시작하고, 공백을 한 칸 둔 다음 정답을 출력한다.
(t는 테스트 케이스의 번호를 의미하며 1부터 시작한다.)

```python
T = int(input())
for i in range(T):
    s = input()
    
    for j in range(1, 10):
        if s[j] == s[0]:
            if s[j+1] == s[1]:
                print(f'#{i+1} {len(s[:j])}')
                break
```
## 백준
### 1157번
[문제]
<p>알파벳 대소문자로 된 단어가 주어지면, 이 단어에서 가장 많이 사용된 알파벳이 무엇인지 알아내는 프로그램을 작성하시오. 단, 대문자와 소문자를 구분하지 않는다.</p>

[입력]
첫째 줄에 알파벳 대소문자로 이루어진 단어가 주어진다. 주어지는 단어의 길이는 1,000,000을 넘지 않는다.

[출력]
첫째 줄에 이 단어에서 가장 많이 사용된 알파벳을 대문자로 출력한다. 단, 가장 많이 사용된 알파벳이 여러 개 존재하는 경우에는 ?를 출력한다.

```python
import sys

s = sys.stdin.readline()
print(s)
s = s[:len(s)-1]
dic_s = {i : 0 for i in set(s.upper())}
print(s)
for i in s.upper():
    dic_s[i] += 1

# key = max(dic_s, key=dic_s.get)
# num = dic_s[key]

result = [k for k, v in dic_s.items() if max(dic_s.values()) == v]

if len(result) == 1:
    print(result[0])
else:
    print('?')
   
```
### 1316번
[문제]
그룹 단어란 단어에 존재하는 모든 문자에 대해서, 각 문자가 연속해서 나타나는 경우만을 말한다. 예를 들면, ccazzzzbb는 c, a, z, b가 모두 연속해서 나타나고, kin도 k, i, n이 연속해서 나타나기 때문에 그룹 단어이지만, aabbbccb는 b가 떨어져서 나타나기 때문에 그룹 단어가 아니다.
단어 N개를 입력으로 받아 그룹 단어의 개수를 출력하는 프로그램을 작성하시오.

[입력]
첫째 줄에 단어의 개수 N이 들어온다. N은 100보다 작거나 같은 자연수이다. 둘째 줄부터 N개의 줄에 단어가 들어온다. 단어는 알파벳 소문자로만 되어있고 중복되지 않으며, 길이는 최대 100이다.

[출력]
첫째 줄에 그룹 단어의 개수를 출력한다.

```python
N = int(input())
result = N
for case in range(N):
    s = input()
    for i in range(0, len(s)-1):
        if s[i] != s[i+1]:
            word = s[i+1:]
            if word.count(s[i]) > 0:
                result -= 1
                break
print(result)
```
### 9012번
[문제]
괄호 문자열(Parenthesis String, PS)은 두 개의 괄호 기호인 ‘(’ 와 ‘)’ 만으로 구성되어 있는 문자열이다. 그 중에서 괄호의 모양이 바르게 구성된 문자열을 올바른 괄호 문자열(Valid PS, VPS)이라고 부른다. 한 쌍의 괄호 기호로 된 “( )” 문자열은 기본 VPS 이라고 부른다. 만일 x 가 VPS 라면 이것을 하나의 괄호에 넣은 새로운 문자열 “(x)”도 VPS 가 된다. 그리고 두 VPS x 와 y를 접합(concatenation)시킨 새로운 문자열 xy도 VPS 가 된다. 예를 들어 “(())()”와 “((()))” 는 VPS 이지만 “(()(”, “(())()))” , 그리고 “(()” 는 모두 VPS 가 아닌 문자열이다. 

여러분은 입력으로 주어진 괄호 문자열이 VPS 인지 아닌지를 판단해서 그 결과를 YES 와 NO 로 나타내어야 한다. 

[입력]
입력 데이터는 표준 입력을 사용한다. 입력은 T개의 테스트 데이터로 주어진다. 입력의 첫 번째 줄에는 입력 데이터의 수를 나타내는 정수 T가 주어진다. 각 테스트 데이터의 첫째 줄에는 괄호 문자열이 한 줄에 주어진다. 하나의 괄호 문자열의 길이는 2 이상 50 이하이다. 

[출력]
출력은 표준 출력을 사용한다. 만일 입력 괄호 문자열이 올바른 괄호 문자열(VPS)이면 “YES”, 아니면 “NO”를 한 줄에 하나씩 차례대로 출력해야 한다. 

```python
N = int(input())

for case in range(N):
    s = input()

    list_patten = [v for v in s]
 
    for k, i in enumerate(s):
        if i == ')':
            for j in range(k):
                if list_patten[j] == '(':
                    list_patten[j] = 'd'
                    list_patten[k] = 'd'
                    break

    if len(list_patten) == list_patten.count('d'):
        print('YES')
    else:
        print('NO')

```

### 10866번

[문제]
정수를 저장하는 덱(Deque)를 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오.

명령은 총 여덟 가지이다.

push_front X: 정수 X를 덱의 앞에 넣는다.
push_back X: 정수 X를 덱의 뒤에 넣는다.
pop_front: 덱의 가장 앞에 있는 수를 빼고, 그 수를 출력한다. 만약, 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.
pop_back: 덱의 가장 뒤에 있는 수를 빼고, 그 수를 출력한다. 만약, 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.
size: 덱에 들어있는 정수의 개수를 출력한다.
empty: 덱이 비어있으면 1을, 아니면 0을 출력한다.
front: 덱의 가장 앞에 있는 정수를 출력한다. 만약 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.
back: 덱의 가장 뒤에 있는 정수를 출력한다. 만약 덱에 들어있는 정수가 없는 경우에는 -1을 출력한다.

[입력]
첫째 줄에 주어지는 명령의 수 N (1 ≤ N ≤ 10,000)이 주어진다. 둘째 줄부터 N개의 줄에는 명령이 하나씩 주어진다. 주어지는 정수는 1보다 크거나 같고, 100,000보다 작거나 같다. 문제에 나와있지 않은 명령이 주어지는 경우는 없다.

[출력]
출력해야하는 명령이 주어질 때마다, 한 줄에 하나씩 출력한다.

```python
from collections import deque
import sys
N = int(sys.stdin.readline())
d = deque()
for case in range(N):
    cmd = list(sys.stdin.readline().split())
    
    if cmd[0] == 'push_front':
        d.appendleft(cmd[1])
    elif cmd[0] == 'push_back':
        d.append(cmd[1])
    elif cmd[0] == 'pop_front':
        if len(d) == 0:
            print(-1)
        else:
            print(d.popleft())
    elif cmd[0] == 'pop_back':
        if len(d) == 0:
            print(-1)
        else:
            print(d.pop())
    elif cmd[0] == 'size':
        print(len(d))
    elif cmd[0] == 'empty':
        if len(d) == 0:
            print(1)
        else:
            print(0)
    elif cmd[0] == 'front':
        if len(d) == 0:
            print('-1')
        else:
            print(d[0])
    elif cmd[0] == 'back':
        if len(d) == 0:
            print('-1')
        else:
            print(d[-1])
```
