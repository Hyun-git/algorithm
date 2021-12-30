## 1. 타겟넘버

  n개의 음이 아닌 정수가 있습니다. 이 수를 적절히 더하거나 빼서 타겟 넘버를 만들려고 합니다. 예를 들어 [1, 1, 1, 1, 1]로 숫자 3을 만들려면 다음 다섯 방법을 쓸 수 있습니다.

- 1+1+1+1+1 = 3
- +1-1+1+1+1 = 3
- +1+1-1+1+1 = 3
- +1+1+1-1+1 = 3
- +1+1+1+1-1 = 3

 사용할 수 있는 숫자가 담긴 배열 numbers, 타겟 넘버 target이 매개변수로 주어질 때 숫자를 적절히 더하고 빼서 타겟 넘버를 만드는 방법의 수를 return 하도록 solution 함수를 작성해주세요.

### 제한사항

- 주어지는 숫자의 개수는 2개 이상 20개 이하입니다.
- 각 숫자는 1 이상 50 이하인 자연수입니다.
- 타겟 넘버는 1 이상 1000 이하인 자연수입니다.

### 입출력 예 
  - 수:[1,1,1,1,1] 
  - 타겟: 3 
  - 출력: 5

  ### 코드
```python
def solution(numbers, target):
    
    arr = [0]
    
    for i in range(len(numbers)):
        arr1 =[]
        for k in range(len(arr)):
            arr1.append(arr[k]+numbers[i])
            arr1.append(arr[k]-numbers[i])
        arr1,arr =arr,arr1
    answer = arr.count(target)

    return answer
 ```
### 해설
 모든 경우의 수를 생각해야하기 때문에 BFS로 모드 경우를 탐색하고 답이 맞는것만 COUNT 해주면 됨.
 위에서는 arr에 모든 경우의 수가 입력이 되고 그중 target에 맞는 답만 카운트 해줌
 
 pop을 이용해서도 했지만 시간이 느려서 실패, pop은 안사용하는게 낫다.
 a,b = b,a 를 하면 두개가 바뀜! 리스트여도 가능

