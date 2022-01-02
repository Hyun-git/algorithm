2022/01/02
# 해쉬

- ![hash](https://user-images.githubusercontent.com/76805070/147869361-fb0b5e97-e894-4fa7-8c39-6d13c2f52357.png)


### 참조
 - https://velog.io/@hanif/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%ED%95%B4%EC%8B%9C
 - https://coding-sojin2.tistory.com/entry/%ED%95%B4%EC%8B%9C-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-hash-algorithm

### 해시
 - 검색을 빠르게 할 수 있는 자료구조이다.
 - key value가 있고 Key 값이 인덱스로서 정보를 저장한다.

### 해시 함수
 - 긴 Key 값을 일정 크기의 hash로 변환하는 역할을 한다.
 - 이 변환 과정을 **해싱** 이라고 한다.
 - 서로 다른 Key 값이 같은 해시값을 가지면 **충돌**이라고 한다.

### 해시 테이블
 - 해시 함수를 통해 키를 해시값으로 바꾸고, 이를 통해 value를 키와 함께 저장하는 자료구조를 말한다.
 - Key -> HashFunction -> values

### 장점
 - 중복을 제거할 수 있다.
 - 인덱스를 통한 접근이기 때문에 삽입과 삭제등의 연산이 빠르다.
### 단점
 - 공간 복잡도가 커진다.
 - 충돌이 발생할 수 있다. --> 충돌시에는 모든 정보를 찾아야 하기에 O(n)이 될 수 있다.
 - 순서가 있는 배열에는 어울리지 않음.

