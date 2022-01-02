# 4. 네트워크

### **문제 설명**

네트워크란 컴퓨터 상호 간에 정보를 교환할 수 있도록 연결된 형태를 의미합니다. 예를 들어, 컴퓨터 A와 컴퓨터 B가 직접적으로 연결되어있고, 컴퓨터 B와 컴퓨터 C가 직접적으로 연결되어 있을 때 컴퓨터 A와 컴퓨터 C도 간접적으로 연결되어 정보를 교환할 수 있습니다. 따라서 컴퓨터 A, B, C는 모두 같은 네트워크 상에 있다고 할 수 있습니다.

컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열 computers가 매개변수로 주어질 때, 네트워크의 개수를 return 하도록 solution 함수를 작성하시오.

### 제한사항

- 컴퓨터의 개수 n은 1 이상 200 이하인 자연수입니다.
- 각 컴퓨터는 0부터 `n-1`인 정수로 표현합니다.
- i번 컴퓨터와 j번 컴퓨터가 연결되어 있으면 computers[i][j]를 1로 표현합니다.
- computer[i][i]는 항상 1입니다.

### 입출력 예
 - n : 3
 - computers : [[1, 1, 0], [1, 1, 0], [0, 0, 1]]
 - retrun: 2
<br>

 - n : 3
 - computers : [[1, 1, 0], [1, 1, 1], [0, 1, 1]]
 - return : 1
### 입출력 예 설명

예제 #1

아래와 같이 2개의 네트워크가 있습니다.

![https://grepp-programmers.s3.amazonaws.com/files/ybm/5b61d6ca97/cc1e7816-b6d7-4649-98e0-e95ea2007fd7.png](https://grepp-programmers.s3.amazonaws.com/files/ybm/5b61d6ca97/cc1e7816-b6d7-4649-98e0-e95ea2007fd7.png)

예제 #2

아래와 같이 1개의 네트워크가 있습니다.

![https://grepp-programmers.s3.amazonaws.com/files/ybm/7554746da2/edb61632-59f4-4799-9154-de9ca98c9e55.png](https://grepp-programmers.s3.amazonaws.com/files/ybm/7554746da2/edb61632-59f4-4799-9154-de9ca98c9e55.png)

```python
def solution(n, computers):
mapp = [0 for i in range(n)]
queue = []
rounds = 0
while(0 in mapp):
	for i in range(n):
		if(mapp[i] == 0):
			queue.append(i)
			mapp[i] = 1
			rounds +=1
			break
	while(queue):
		now = queue.pop(0)
		for i in range(n):
			if(computers[now][i] == 1 and mapp[i] != 1):
				mapp[i] = 1
				queue.append(i)
```

```
answer = rounds
return answer
```

### 풀이

- 이중 반복문을 통해서 품
- 밖의 반복문에서는 mapp 안에 0 이있으면 방문하지 않은 노드를 출발 지점으로 설정해줌
- 안의 반복문은 BFS로 방문을 하면서 연결되어 있는 모든 노드를 방문함.
- 밖의 반복문을 돈 횟수가 네트워크의 개수
