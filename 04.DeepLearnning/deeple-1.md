### softmax : mult-class에 대한 probablity를 리턴하는 함수이다.

#1. 딥러닝 모델 생성순서
##1. 모델 구조 정의
- 빈 모델 생성 : Sequential로 생성
- add 메소드를 통해 layer를 하나씩 추가
- Dense layer가 있는 경우, 첫 layer는 반드시 input_shape를 지정해야한다.

``` python
from tensorflow.keras import models
from tensorflow.keras import layers

network = models.Sequential()
network.add(layers.Dense(512, activation='relu', input_shape(28*28,)))
network.add(layers.Dense(10, activation='softmax'))

network_inpit_shape #None값은 배치값을 의미한다.
```

### 신경망이 훈련 준비를 마치기 위해서는 컴파일 단계에 포함될 세가지가 더 필요하다
- 손실 함수 : 훈련 데이터에서 신경망의 성능을 측정하는 방법으로 네트워크가 옳은 방향으로 학습될 수 있도록 도와 줍니다.
- 옵티마이저 : 입력된 데이터와 손실 함수를 기반으로 네트워크를 업데이트하는 메커니즘입니다.
- 훈련과 테스트 과정을 모니터링할 지표 : 여기에서는 정확도(정확히 분류된 이미지의 비율)만 고려

 ```python
# h[0] = X.w[0] + b[0] : 
# (1, ) = (28*28,).(28*28,) + (1,)
# 1개 출력 픽셀을 만드는 데 필요한 파라미터의 수 = (28*28 + 1)
# 512개의 출력 픽셀을 만드는 데 필요한 파라미터의 수
(28*28 + 1)*512\
#출력 401920
```

##2. 모델 컴파일 : 학습 방법을 지정
- optimizer : 학습 파리미터 업데이트 방법
- loss : 감소시켜야 할 값으로서, 이에대한 gradient를 구해 loss를 감소시키는 방향으로 학습 파리미터를 업데이트
- metrics: 모델의 성능을 평가하는 지표

```python
network.compile(optimizer='rmsprop',
	          loss='categrical_crossentropy',
	          metrics=['accuracy'])
```

* categorical crossentropy
likelihood : 우도, 그럴싸함, 모델이 얼마나 데이터를 잘 표현하고 있는지를 나타내는 지표

##3. 데이터 전처리
훈련을 시작하기전에 데이터를 네트워크 크기에 맞는 크기로 바꾸고 모든값을 0과 1사이로 스케일을 조정한다.
```python
train_images = train_images.reshape((60000, 28 * 28))
train_images = train_images.astype('float32') / 255 #MinMaxScaling

test_images = test_images.reshape((10000, 28 * 28))
test_images = test_images.astype('float32') / 255
```
<br> [0, 255] 사이의 값인 uint8 타입의 (60000, 28, 28) 크기를 가진 배열로 저장되어있는 훈련 이미지를</br>
0과 1시이의 값을 가지는 float32 타입의 (60000, 28 * 28) 크기의 배열로 변경.

또한 레이블을 범주형으로 인코딩 해야함.(뒷부분 참고)
```python
from tensorflow.keras.utils import to_categorical

train_labels = to_categorical(train_labels)
test_labels = to_categorical(test_labels)

train_labels.shape
#출력 (60000, 10)
```
```python
train_labels[:10]
#출력 array([[0., 0., 0., 0., 0., 1., 0., 0., 0., 0.],
#       [1., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
#       [0., 0., 0., 0., 1., 0., 0., 0., 0., 0.],
#       [0., 1., 0., 0., 0., 0., 0., 0., 0., 0.],
#       [0., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
#       [0., 0., 1., 0., 0., 0., 0., 0., 0., 0.],
#       [0., 1., 0., 0., 0., 0., 0., 0., 0., 0.],
#       [0., 0., 0., 1., 0., 0., 0., 0., 0., 0.],
#       [0., 1., 0., 0., 0., 0., 0., 0., 0., 0.],
#       [0., 0., 0., 0., 1., 0., 0., 0., 0., 0.]], dtype=float32)
```

## 4. 학습
케라스에서는 fit 메소드를 호출해서 훈련데이터에 모델을 학습시킨다.
