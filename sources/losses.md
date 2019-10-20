
## 손실 함수의 사용

손실 함수(목적 함수 또는 최적화 스코어 함수)는 하나의 모델을 컴파일하기 위해 필요한 두 개의 매개 변수 중 하나입니다.

```python
model.compile(loss='mean_squared_error', optimizer='sgd')
```

```python
from keras import losses

model.compile(loss=losses.mean_squared_error, optimizer='sgd')
```

기존의 손실 함수를 매개 변수로 전달하거나 TensorFlow/Theano의 심볼릭 함수<sub>symbolic function</sub>를 매개 변수로 전달할 수 있습니다. 심볼릭 함수는 다음의 두 인자를 받아 각각의 데이터 포인트에 대한 스칼라를 반환합니다.

- __y_true__: 정답 레이블. TensorFlow/Theano 텐서.
- __y_pred__: 예측값. y_true와 같은 크기<sub>shape</sub>의 TensorFlow/Theano 텐서.

실제로 최적화되는 값은 모든 데이터 포인트 범위 안에서 출력된 값의 평균값입니다.

손실함수의 예시는 [여기](https://github.com/keras-team/keras/blob/master/keras/losses.py)에서 확인할 수 있습니다.

## 사용 가능한 손실 함수

### mean_squared_error


```python
keras.losses.mean_squared_error(y_true, y_pred)
```

----

### mean_absolute_error


```python
keras.losses.mean_absolute_error(y_true, y_pred)
```

----

### mean_absolute_percentage_error


```python
keras.losses.mean_absolute_percentage_error(y_true, y_pred)
```

----

### mean_squared_logarithmic_error


```python
keras.losses.mean_squared_logarithmic_error(y_true, y_pred)
```

----

### squared_hinge


```python
keras.losses.squared_hinge(y_true, y_pred)
```

----

### hinge


```python
keras.losses.hinge(y_true, y_pred)
```

----

### categorical_hinge


```python
keras.losses.categorical_hinge(y_true, y_pred)
```

----

### logcosh


```python
keras.losses.logcosh(y_true, y_pred)
```


예측 오차의 하이퍼볼릭 코사인 로그값.

`log(cosh(x))`는 작은 `x`값에 대하여 `(x ** 2) / 2`, 큰 `x`값에 대하여
 `abs(x) - log(2)`와 거의 같은 값을 가집니다. 다시 말해 `logcosh`는 대부분 
평균 제곱 오차와 비슷한 양상을 보이지만, 가끔 발생하는 완전히 부정확한 예측의 영향을 크게
받지는 않습니다.

__Arguments__

- __y_true__: 정답 타겟의 텐서.
- __y_pred__: 예측 타겟의 텐서.

__Returns__

샘플당 하나의 스칼라 손실값을 가지는 텐서
    
----

### categorical_crossentropy


```python
keras.losses.categorical_crossentropy(y_true, y_pred)
```

----

### sparse_categorical_crossentropy


```python
keras.losses.sparse_categorical_crossentropy(y_true, y_pred)
```

----

### binary_crossentropy


```python
keras.losses.binary_crossentropy(y_true, y_pred)
```

----

### kullback_leibler_divergence


```python
keras.losses.kullback_leibler_divergence(y_true, y_pred)
```

----

### poisson


```python
keras.losses.poisson(y_true, y_pred)
```

----

### cosine_proximity


```python
keras.losses.cosine_proximity(y_true, y_pred)
```


----

### is_categorical_crossentropy

```python
kearas.losses.is_categorical_crossentropy(loss)
```


----
**Note**: 손실 함수 `categorical_crossentropy`의 경우 사용되는 타겟들은 범주 형식(categorical format)을 따라야 합니다.예를 들어 10개의 클래스(범주)를 가지고 있다면, 각 샘플의 목표값은 샘플 클래스에 해당하는 인덱스의 1을 제외하고 모두 0인 10차원 벡터가 되어야 합니다.
Keras의 기능인 `to_categorical`을 통해 정수형 타겟(*integer target*)을 범주형 타겟(*categorical target*)으로 변환할 수 있습니다.

```python
from keras.utils import to_categorical

categorical_labels = to_categorical(int_labels, num_classes=None)
```
