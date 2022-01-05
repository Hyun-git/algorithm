# 8. 조이스틱

조이스틱으로 알파벳 이름을 완성하세요. 맨 처음엔 A로만 이루어져 있습니다.ex) 완성해야 하는 이름이 세 글자면 AAA, 네 글자면 AAAA

조이스틱을 각 방향으로 움직이면 아래와 같습니다.

`▲ - 다음 알파벳
▼ - 이전 알파벳 (A에서 아래쪽으로 이동하면 Z로)
◀ - 커서를 왼쪽으로 이동 (첫 번째 위치에서 왼쪽으로 이동하면 마지막 문자에 커서)
▶ - 커서를 오른쪽으로 이동`

예를 들어 아래의 방법으로 "JAZ"를 만들 수 있습니다.

- `첫 번째 위치에서 조이스틱을 위로 9번 조작하여 J를 완성합니다.
- 조이스틱을 왼쪽으로 1번 조작하여 커서를 마지막 문자 위치로 이동시킵니다.
- 마지막 위치에서 조이스틱을 아래로 1번 조작하여 Z를 완성합니다.
따라서 11번 이동시켜 "JAZ"를 만들 수 있고, 이때가 최소 이동입니다.`

만들고자 하는 이름 name이 매개변수로 주어질 때, 이름에 대해 조이스틱 조작 횟수의 최솟값을 return 하도록 solution 함수를 만드세요.

### 제한 사항

- name은 알파벳 대문자로만 이루어져 있습니다.
- name의 길이는 1 이상 20 이하입니다.

### 입출력 예

<img width="167" alt="image" src="https://user-images.githubusercontent.com/76805070/148228725-e8f9f552-1c20-41e6-9561-69322a874d22.png">
```python
def solution(name):
	name = list(map(ord,name))
	orgin = [ord("A") for i in range(len(name))]
	same = [0 for i in range(len(name))]
	same[0] = 1
	movecount = [(len(name)+1) for i in range(len(name))]
	now = 0
	move = 0
	for i in range(len(name)):

    temp = name[i] - orgin[i]
    if(temp>12):
        move+= 26-temp
    else:
        move+= temp

    if(name[i] == orgin[i]):
        same[i] = 1
    if(same[i] == 0):
        if(i > len(name)//2 ):
            movecount[i] = len(name) -i
        else:
            movecount[i] = i

while(1):
    movemin = movecount.index(min(movecount))
    now = movemin
    same[movemin] = 1
    move += movecount[movemin]

    movecount = [(len(name)+1) for i in range(len(name))]

    if(0 not in same):
        break

    for i in range(len(name)):
        if(same[i] == 0):
            if(abs(i-now) > len(name)//2 ):
                movecount[i] = len(name) - abs(i-now)
            else:
                movecount[i] = abs(i-now)

answer = move
return answer
```
