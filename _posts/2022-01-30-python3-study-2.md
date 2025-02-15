---
title: "파이썬 스터디 2"
last_modified_at: 2022-01-30T20:45:00-05:00
categories:
  - python3
tags:
  - Baekjoon
  - SW Expert Academy
toc: true
toc_label: "파이썬 기초"
toc_iocn: #
toc_sticky: true
---
**파이참으로 풀어서 결과를 따로 넣지 않았습니다.**
# SW 
## 1966. 숫자를 정렬하자
### 문제
- 주어진 N 길이의 숫자열을 오름차순으로 정렬하여 출력하라.

### 제약사항
- N 은 5 이상 50 이하이다.

### 입력
- 가장 첫 줄에는 테스트 케이스의 개수 T가 주어지고, 그 아래로 각 테스트 케이스가 주어진다.
- 각 테스트 케이스의 첫 번째 줄에 N 이 주어지고, 다음 줄에 N 개의 숫자가 주어진다.

### 출력
- 출력의 각 줄은 '#t'로 시작하고, 공백을 한 칸 둔 다음 정답을 출력한다.
- (t는 테스트 케이스의 번호를 의미하며 1부터 시작한다.)

### 코드
```python
T = int(input())
for i in range(T):
	num = int(input())
	# 실제 코딩 테스트에서 필요할 수 있음
	# list_n = list(map(int, sys.stdin.readline().split()))
	list_n = list(map(int, input().split()))
	list_n.sort()
	print('#{} '.format(i + 1), end='')
	for j in list_n:
		print(j, end=' ')
	print()
```
<div class="notice--primary" markdown="1">
이 문제는 리스트에 sort()를 이용하는 간단한 문제입니다. 처음 `sys.stdin.readline()`으로 풀려고 했지만, SW에서는 sys 라이브러리를 결과 제출에 사용할 수 없어 input()으로 해결했습니다.
</div>


## 2050. 알파벳을 숫자로 변환
### 문제
- 알파벳으로 이루어진 문자열을 입력 받아 각 알파벳을 1부터 26까지의 숫자로 변환하여 출력하라.

### 제약사향
- 문자열의 최대 길이는 200이다.

### 입력
- 알파벳으로 이루어진 문자열이 주어진다.

### 출력
- 각 알파벳을 숫자로 변환한 결과값을 빈 칸을 두고 출력한다.

### 코드
```python
line = input()
for i in line:
	print(ord(i)-64, end=' ')
```

<div class="notice--primary" markdown="1">
이 문제는 문자를 아스키코드로 변경하여 풀었습니다.
</div>


# 백준
## 2577. 숫자의 개수
### 문제
- 세 개의 자연수 A, B, C가 주어질 때 A × B × C를 계산한 결과에 0부터 9까지 각각의 숫자가 몇 번씩 쓰였는지를 구하는 프로그램을 작성하시오.
- 예를 들어 A = 150, B = 266, C = 427 이라면 A × B × C = 150 × 266 × 427 = 17037300 이 되고, 계산한 결과 17037300 에는 0이 3번, 1이 1번, 3이 2번, 7이 2번 쓰였다.

### 입력
- 첫째 줄에 A, 둘째 줄에 B, 셋째 줄에 C가 주어진다. A, B, C는 모두 100보다 크거나 같고, 1,000보다 작은 자연수이다.

### 출력
- 첫째 줄에는 A × B × C의 결과에 0 이 몇 번 쓰였는지 출력한다. 마찬가지로 둘째 줄부터 열 번째 줄까지 A × B × C의 결과에 1부터 9까지의 숫자가 각각 몇 번 쓰였는지 차례로 한 줄에 하나씩 출력한다.
```python
n1 = int(input())
n2 = int(input())
n3 = int(input())
dic = {i : 0 for i in range(10)}
m = n1 * n2 * n3
for i in str(m):
	dic[int(i)] += 1
for key, value in dic.items():
	print(value)
```

<div class="notice--primary" markdown="1">
이 문제의 **결과에 0 이 몇 번 쓰였는지 출력한다. 마찬가지로 둘째 줄부터 열 번째 줄까지 A × B × C의 결과에 1부터 9까지의 숫자가 각각 몇 번 쓰였는지 차례로 한 줄에 하나씩 출력**이라는 문장을 보고 딕셔너리로 풀어야겠다는 생각을 했습니다. 그래서 딕셔너리에 0~9까지를 넣고 value에 0을 넣어서 풀었습니다. 당시 딕셔너리에 0을 넣지 않아 오류가 발생하였고 이것은 문제와 예제 출력을 정확하게 보지 않아서 생긴 문제였습니다.
</div>


## 8958. OX퀴즈
### 문제
- "OOXXOXXOOO"와 같은 OX퀴즈의 결과가 있다. O는 문제를 맞은 것이고, X는 문제를 틀린 것이다. 문제를 맞은 경우 그 문제의 점수는 그 문제까지 연속된 O의 개수가 된다. 예를 들어, 10번 문제의 점수는 3이 된다.
- "OOXXOXXOOO"의 점수는 1+2+0+0+1+0+0+1+2+3 = 10점이다.
- OX퀴즈의 결과가 주어졌을 때, 점수를 구하는 프로그램을 작성하시오.

### 입력
- 첫째 줄에 테스트 케이스의 개수가 주어진다. 각 테스트 케이스는 한 줄로 이루어져 있고, 길이가 0보다 크고 80보다 작은 문자열이 주어진다. 문자열은 O와 X만으로 이루어져 있다.

### 출력
- 각 테스트 케이스마다 점수를 출력한다.

```python
t = int(input())
for i in range(t):
	num = 0
	result = 0
	line = input()
		 for j in line:
			 if j == 'O':
				num += 1
			 else:
				num = 0
			result += num
		print(result)
```

<div class="notice--primary" markdown="1">
이 문제의 핵심은 점수를 초기화해주는 것이다.
</div>

## 10828. 스택
### 문제
- 정수를 저장하는 스택을 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오. 명령은 총 다섯 가지이다.
	- push X: 정수 X를 스택에 넣는 연산이다.
	- pop: 스택에서 가장 위에 있는 정수를 빼고, 그 수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
	- size: 스택에 들어있는 정수의 개수를 출력한다.
	- empty: 스택이 비어있으면 1, 아니면 0을 출력한다.
	- top: 스택의 가장 위에 있는 정수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.

### 입력
- 첫째 줄에 주어지는 명령의 수 N (1 ≤ N ≤ 10,000)이 주어진다. 둘째 줄부터 N개의 줄에는 명령이 하나씩 주어진다. 주어지는 정수는 1보다 크거나 같고, 100,000보다 작거나 같다. 문제에 나와있지 않은 명령이 주어지는 경우는 없다.

### 출력
- 출력해야하는 명령이 주어질 때마다, 한 줄에 하나씩 출력한다.

```python
import sys
t = int(sys.stdin.readline())
stack = []
for i in range(t):
	cmd = sys.stdin.readline().split()

		if cmd[0] == 'push':
			stack.append(cmd[1])
		elif cmd[0] == 'pop':
			if len(stack) == 0:
				print(-1)
			else:
				print(stack.pop())
		elif cmd[0] == 'size':
				print(len(stack))
		elif cmd[0] == 'empty':
				if len(stack) == 0:
					print(1)
				else:
					print(0)
		elif cmd[0] == 'top':
			if len(stack) == 0:
				print(-1)
			else:
				print(stack[-1])
```

<div class="notice--primary" markdown="1">
이 문제는 리스트를 자유롭게 다룰 수 있다면 쉽게 풀 수 있는 문제입니다. 여기서 `sys.stdin.readlin()`을 사용하지 않으면 시간 초과가 되기 때문에 조심해야 합니다.
</div>
