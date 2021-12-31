#Numpy -7
##1. Shape
###1)numpy.reshape
- 데이터를 변경하지 않고 배열에 새로운 모양을 부여한다.
```python
np.arange(6).reshape((3,2))
#출력 array([[0, 1],
#            [2, 3],
#            [4, 5]])
```
이렇게도 쓴다. 차원을 안낮추려면 아래처럼 해야한다.
```python
np.arange(a(2,3))
#출력 array([[0, 1, 2],
#           [3, 4, 5]])
```
### 2)numpy_ravel()
- 다차원 배열을 직선으로 펼쳐 출력해주는것
- reshape와 달리 사이즈를 따로 명시하지 않아도 된다.
```python
a = np.arange(6)
np.ravel(a)
a.ravel()
#출력 array([0, 1, 2, 3, 4, 5])
```
### 3)numpy.ndarray.flatten()
**ravel()과 flatten() 차이점**
- flatten은 객체의 매소드로만 사용 가능
- ravel()은 뷰를 반환, flatten은 복사본을 반환
- 둘다 결과는 똑같음
```python
# np.flatten(a) # Numpy 모듈 함수가 아님
a.flatten()    # ndarray 객체의 메소드로만 사용 가능
#출력 array([0, 1, 2, 3, 4, 5])
```

## 2. 연결
### 1)numpy.concatenate
서로 다른 넘파이 어레이를 하나로 연결하는것

```python
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6]])
np.concatenate((a,b), axis=0) # axis =0 이면 방향에 따라 위에서 아래로 연결한다.
#array([[1, 2],
#       [3, 4],
#       [5, 6]])
```
```python
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6]])
np.concatenate((a,b), axis=0) # axis =0 이면 방향에 따라 위에서 아래로 연결한다.
#array([[1, 2],
#       [3, 4],
#       [5, 6]])
```
- axis=1의 경우 옆으로 연결한다. 
- transpose 꼭 해줘야함
- 슬라이싱을 하지 않고 인덱싱만해서 가져올 경우 1차원이기 때문에 transpose가 안되니 주의
```python
np.concatenate((a.b.T), axis=1) 
#출력 array([[1, 2, 5],
#           [3, 4, 6]])
```
<br>참고, 한번 훑어볼것</br>
<br>https://docs.scipy.org/doc/numpy/reference/routines.array-manipulation.html#joining-arrays </br>

## 3.다차원 배열 연산
기본적인  수학 함수는 각 요소별로 동작하며 연산자를 통해 동작하거나 numpy 함수 모듈을 통해 동작한다.
<br>다차원 배열간 연산 시 shape가 맞아야 연산이 이루어진다.</br>
- 요소별 합, 차, 곱, 나눗넴의 경우 shape가 일치해야한다.
- dot의 경우 앞 배열의 열과 뒤 배열의 행의 크기가 일치해야한다.

<br> 참고 https://docs.scipy.org/doc/numpy/reference/routines.math.html </br>

```python
import numpy as np

x = np.array([[1., 2.], [3., 4.]])
y = np.array([[5., 6.], [7., 8.]])

# 요소별 합; 둘 다 다음의 배열을 만듭니다
# [[ 6.0  8.0]
#  [10.0 12.0]]
print(x + y)
print(np.add(x, y))

# 요소별 차; 둘 다 다음의 배열을 만듭니다
# [[-4.0 -4.0]
#  [-4.0 -4.0]]
print(x - y)
print(np.subtract(x, y))

# 요소별 곱; 둘 다 다음의 배열을 만듭니다
# [[ 5.0 12.0]
#  [21.0 32.0]]
print(x * y)
print(np.multiply(x, y))

# 요소별 나눗셈; 둘 다 다음의 배열을 만듭니다
# [[ 0.2         0.33333333]
#  [ 0.42857143  0.5       ]]
print(x / y)
print(np.divide(x, y))

# 요소별 제곱근; 다음의 배열을 만듭니다
# [[ 1.          1.41421356]
#  [ 1.73205081  2.        ]]
print(np.sqrt(x))
```
