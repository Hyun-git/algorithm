# 5. 카펫

### **문제 설명**

Leo는 카펫을 사러 갔다가 아래 그림과 같이 중앙에는 노란색으로 칠해져 있고 테두리 1줄은 갈색으로 칠해져 있는 격자 모양 카펫을 봤습니다.

![https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/b1ebb809-f333-4df2-bc81-02682900dc2d/carpet.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/b1ebb809-f333-4df2-bc81-02682900dc2d/carpet.png)

Leo는 집으로 돌아와서 아까 본 카펫의 노란색과 갈색으로 색칠된 격자의 개수는 기억했지만, 전체 카펫의 크기는 기억하지 못했습니다.

Leo가 본 카펫에서 갈색 격자의 수 brown, 노란색 격자의 수 yellow가 매개변수로 주어질 때 카펫의 가로, 세로 크기를 순서대로 배열에 담아 return 하도록 solution 함수를 작성해주세요.

### 제한사항

- 갈색 격자의 수 brown은 8 이상 5,000 이하인 자연수입니다.
- 노란색 격자의 수 yellow는 1 이상 2,000,000 이하인 자연수입니다.
- 카펫의 가로 길이는 세로 길이와 같거나, 세로 길이보다 깁니다.

### 입출력 예
#### 1
  - brown: 10
  - yellow: 2
  - return: [4,3]
#### 2
  - brown : 8
  - yellow: 1
  - return:[3,3]
#### 3
  - brown: 24
  - yellow : 24
  - return : [8,6]


```python
def solution(brown, yellow):
	answer = []
	multi = []
	carpetSize = brown + yellow
	untill = carpetSize ** 0.5
	untill = int(untill) + 1
	
	for i in range(1, untill):
	    if(carpetSize % i == 0):
	        multi.append([i,carpetSize//i])
	
	for i in range(len(multi)):
	    if(multi[i][0] * 2 + multi[i][1]*2 - 4 == brown ):
	        answer = [multi[i][1],multi[i][0]]
	
	return answer
```
### 풀이
- brown 과 yellow 를 더해서 나올 수 있는 카펫의 크기를 찾는다. ⇒ 약수를 찾기
- 약수는 1~ 루트n 까지 나누어서 나머지가 0이되는 곱을 찾으면된다.
- 그중에 테두리의 크기가 brown 의 크기와 같은 것을 찾아서 반환하면 된다.
