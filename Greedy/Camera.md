# 9. 단속카메라

고속도로를 이동하는 모든 차량이 고속도로를 이용하면서 단속용 카메라를 한 번은 만나도록 카메라를 설치하려고 합니다.

고속도로를 이동하는 차량의 경로 routes가 매개변수로 주어질 때, 모든 차량이 한 번은 단속용 카메라를 만나도록 하려면 최소 몇 대의 카메라를 설치해야 하는지를 return 하도록 solution 함수를 완성하세요.

**제한사항**

- 차량의 대수는 1대 이상 10,000대 이하입니다.
- routes에는 차량의 이동 경로가 포함되어 있으며 routes[i][0]에는 i번째 차량이 고속도로에 진입한 지점, routes[i][1]에는 i번째 차량이 고속도로에서 나간 지점이 적혀 있습니다.
- 차량의 진입/진출 지점에 카메라가 설치되어 있어도 카메라를 만난것으로 간주합니다.
- 차량의 진입 지점, 진출 지점은 -30,000 이상 30,000 이하입니다.

**입출력 예**

![image](https://user-images.githubusercontent.com/76805070/148385966-ed1a30d4-8bba-487a-8167-7d31b62febef.png)

**입출력 예 설명**

- 5 지점에 카메라를 설치하면 두 번째, 네 번째 차량이 카메라를 만납니다.
- 15 지점에 카메라를 설치하면 첫 번째, 세 번째 차량이 카메라를 만납니다.

```python
def solution(routes):
	routes.sort(key=lambda x: (x[1], -x[0]))
	answer = 0
	while(routes):
	    temp = routes.pop(0)
	    left = temp[0]
	    right = temp[1]
	    answer +=1
	
	    for i in range(len(routes)):
	        if(routes[0][0]>right or len(routes)==0):
	            break
	
	        if(routes[0][0]<=right<=routes[0][1]):
	            routes.pop(0)
	
	
	return answer
```

### 풀이

- 일단 차들을 진출 시점을 기준으로 정렬시킨다.
- 이후 가장 먼저 나가는 차의 진출시점을 기준으로 그때 통과하는 차들은 다 단속이 된다고 판단
- 단속이 된 차들은 제외시키고 다시 첫차를 기준으로 반복
