# 12. 124나라

124 나라가 있습니다. 124 나라에서는 10진법이 아닌 다음과 같은 자신들만의 규칙으로 수를 표현합니다.

1. 124 나라에는 자연수만 존재합니다.
2. 124 나라에는 모든 수를 표현할 때 1, 2, 4만 사용합니다.

예를 들어서 124 나라에서 사용하는 숫자는 다음과 같이 변환됩니다.

자연수 n이 매개변수로 주어질 때, n을 124 나라에서 사용하는 숫자로 바꾼 값을 return 하도록 solution 함수를 완성해 주세요.

![image](https://user-images.githubusercontent.com/76805070/149283350-a4ded074-3a98-45bc-83b8-8d4323420ceb.png)

### 제한사항

- n은 500,000,000이하의 자연수 입니다.

---

### 입출력 예

![image](https://user-images.githubusercontent.com/76805070/149283324-1e4a28c6-df1d-4293-b37b-0b6012286d8e.png)

```python
import math
def solution(n):
    
    answer = []
    Start =n 
    cnt = 0
    S = 3
    
    if(n<4):
        return str(pow(2,n-1))
    
    while(Start>0):
        Start -= S
        S *= 3
        cnt +=1
    
    for i in range(cnt):
        k = n%3
        if(k==0):
            k = 3
        answer.append(str(pow(2,k-1)))
        n -= k
        n = n//3
    answer.reverse()
        
    answer = ''.join(answer)
    return answer
```

### 풀이

- 먼저 n을 나타낼 수 있는 자리수를 구한다
- 124 인 세수로 나타내기 때문에 3진법과 유사하다
- 먼저 3으로 나눈 나머지를 통해 각 자리를 구하고 나머지가 0일 때는 각자리가 0 일 수 없기때문에 3으로 바꾸어준다.
- 이후 n을 3 으로 나누어 주면서 진행을 한다.
