#Numpy -3 / 다차원 배열 생성하기 2

## 1. Numpy.empty
- 초기화 없이 주어진 형태와 타입으로 새로운 배열을 반환한다.

```python
import numpy as np
np.empty((2,3)) // 괄호안에 숫자는 각 2열과 3행을 의미한다.
np.empty_like(A) // "A"어레이 의 형태만 그대로 가지고 오고 초기화 없이 새로운 배열을 반환한다.
```
## 2. Numpy.zeros
empty와 비슷하지만 초기화를 0으로 해주는 함수이다. 데이터 타입을 명시하지 않으면 실수형 데이터로 생성된다. 정수(0)로 만들 시에는 데이터 타입을 명시해야한다.

```python
np.zeros_like(A) // "A" 어레이의 형태만 그대로 가지고 오고 0 값으로 초기화한다. 선형대수에서 유용함
```python
```
## 3. Numpy.ones
zeros와 유사하지만 값을 1로 설정해 초기화한다.

## 4.Numpy.identity
- 단위 행렬을 identity metrics라고 한다.
- 정시가 행렬이면서 대각선이 1인 행렬을 의미하고 정수로 만들시에는 데이터 타입을 명시해야한다.

```python
np.identity('size') // 괄호안에는 사이즈를 넣어준다
```
참고) numpy.eye
identity와 유사하다. identity와는 달리 eye는 행과 열의 값을 다르게 입력할 수 있고, 마지막 값을 이용해 대각선의 위치조정도 가능하다.
## 5. Numpy.full
ones와 유사하지만 값을 10으로 설정해 초기화한다. ones를 사용하고 10을 곱해주면 동일한 기능을 하기 때문에 ones를 더 많이 사용하고 full은 잘 사용하지 않는다.