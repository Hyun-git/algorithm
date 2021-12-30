## 2. 단어변환 BFS

두 개의 단어 begin, target과 단어의 집합 words가 있습니다. 아래와 같은 규칙을 이용하여 begin에서 target으로 변환하는 가장 짧은 변환 과정을 찾으려고 합니다.

`1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.`<br>
`2. words에 있는 단어로만 변환할 수 있습니다.`

예를 들어 begin이 "hit", target가 "cog", words가 `["hot","dot","dog","lot","log","cog"]`라면 `"hit" -> "hot" -> "dot" -> "dog" -> "cog"`와 같이 4단계를 거쳐 변환할 수 있습니다.

두 개의 단어 begin, target과 단어의 집합 words가 매개변수로 주어질 때, 최소 몇 단계의 과정을 거쳐 begin을 target으로 변환할 수 있는지 return 하도록 solution 함수를 작성해주세요.

### 제한사항

- 각 단어는 알파벳 소문자로만 이루어져 있습니다.
- 각 단어의 길이는 3 이상 10 이하이며 모든 단어의 길이는 같습니다.
- words에는 3개 이상 50개 이하의 단어가 있으며 중복되는 단어는 없습니다.
- begin과 target은 같지 않습니다.
- 변환할 수 없는 경우에는 0를 return 합니다.

### 입출력 예
- begin: hit
- target: dog
- words:["hot", "dot", "dog", "lot", "log", "cog"]
- output: 4

### 입출력 예 설명

예제 #1문제에 나온 예와 같습니다.

예제 #2target인 "cog"는 words 안에 없기 때문에 변환할 수 없습니다.

## 풀이

```python
def solution(begin, target, words):
if(target not in words):
return 0
queue = [[begin,0]]
mapp = [begin]
```

```python
while(queue):
    temp = queue.pop(0)
    now = temp[0]
    rounds = temp[1]
    if(now == target):
        break

    for i in range(len(words)):
        same = 0
        for k in range(len(begin)):
            if(words[i][k] == now[k]):
                same += 1
        if(same == len(begin) - 1 and words[i] not in mapp):
            mapp.append(words[i])
            queue.append([words[i],rounds+1])

answer = rounds
return answer
```
```
- queue 에 현재단어, 횟수를 집어 넣고 Target 단어가 될 때까지 한글자씩 바꾸는 BFS를 진행
- 한글자만 다르다는것을 체크해야하고, 왔던 단어는 다시 안돌아가게 mapp을 통해 방문 표시를 한다.
```
