# Numpy -2 / 다차원 배열 생성하기

직접 원소를 입력할때는 **np.array('None')처럼 사용한다.

```python
boolArray = np.array([True, False, True, True, False])
boolArray
```

##Number 데이터
1. 정수형
- 정수형의 default data type은 'int64' 이지만 운영 체제에 따라 다를 수 있다.
- 아래처럼 표시한다.

```python
intArray = np.array([[1,2], [3,4]])
boolArray
``` 

2. 부호없는 정수형 
- 부호가 있는지 없는지 알 수 없기 때문에 데이터 타입을 반드시 명시해야 한다. 데이터 타입은 정수형처럼 명시하고 넘파이 어레이 속 파이썬 리스트 뒤에 ** , dtype='unit' ** 이런식으로 표시한다.

3. 실수형
- 실수형의 default data type은 'float64'이다.
- 파이썬 리스트 속 정수를 입력한 뒤 데이터 타입만 float으로 변경하는 것은 잘못된 방법이다.
<br> 위에 방법보다는 아래처럼 하는 것이 국룰

```python
floatArray3 = np.array[[1., 2.],[3., 4.]]
```

참고) 정수형에서 실수형으로 형변환 과정은 데이터 손실이 일어나지 않아 문제될 부분이 없지만 반대의 경우(실수를 정수로 변환할 경우)는 문제가 발생할 수 있다.

4. 복소수형
- 정수을 만들듯 복소수를 입력하면 된다. 하지만 실전에서는 거의 쓰이지 않아 참고만 할 것
- 복수수의 default data type은 'complex128'이다.
- 
```python
complexArray = np.array[[1+1j, 2+2j, 3+3j, 4+4j, 5+5j]
```

## 파일에서 데이터를 입력 받아 다차원 배열 생성하기
- np.genfrom.txt()를 이용하여 파일에 저장된 데이터를 입력 받아 다차원 배열을 생성 할 수 있다.
다만 많이 사용하지는 않는다. 그 이유는 넘파이 어레이는 동일한 데이터 타입만 가져올 수 있는데 
대부분 데이터 파일에는 하나의 데이터 타입만 있는게 아니라 정수, 실수, 문자열이 섞여있다. 
따라서 파일에서 데이터를 읽어올때는 **Pandas의 reac_csv() 혹은 read_excel()**을 주로 사용한다.