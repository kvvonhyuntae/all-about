# Pandas -1 / 데이터 구조(Series, DataFrame)
## pandas의 특징
- Numpy를 내부적으로 활용하기 때문에 Nump의 특징을 그대로 가진다.
- 데이터 분석에 특화된 데이터 구조를 제공하고 다양한 데이터 분석 함수를 제공한다.
- 데이터 베이스에 쉽게 연결이 가능하다.
<span style="color:orange"><br>help(pd.함수)를 이용해 pandas의 도움말을 확인할 수 있다.</br></span>

## 1. pandas 데이터 구조
### 1)Series
-1차원 배열 자료 구조
- DataFrame에서 행은 시리즈를 의미한다.
- 일반적으로 s 또는 sr이라고 이름 붙인다.
<br> Series는 value와 index를 가진다.</br>

<br> 아래와 같이 생성한다.</br>

```phthon
s = pd.Series([3, -5, 7, 4]) #인덱스 없이 생성

s = pd.Series([3, -5, 7, 4], index = ['a', 'b', 'c', 'd']) #인덱스 추가
s.index #

s['a'] #인덱스 명으로 조회 #추천

s['0'] #인덱스 순서로 조회
```
- pandas의 Series는 python의 Dictionary와 유사하다. 때문에 딕셔너리를 통해 Series를 생성하는것이 가능하다.
- 딕셔너리에서 key값을 이용해 value를 조회하듯 Series에서도 index를 이용해 value를 조회할 수 있다.
- 딕셔너리는 key에 순서가 없지만 Pandas Series의 index는 순서가 있다. 때문에 Series는 index의 순서를 통해서도 vlaue 조회가 가능하다.
- Series의 요소는 index명 또는 index의 순서를 통해 인덱싱할 수 있다.
```python
s['a']      # index명으로 조회
s[0]        # index순서로 조회
```
참고) index가 문자열에 저장된 숫자일 경우
- Series의 요소를 조회하는데 혼돈이 올 수 있으니, 숫자 index를 원할경우 문자가 아닌 정수형으로 inxdex를 지정해야한다.
<br> + 1이 아닌 0부터 index를 지정합시다 </br>
```python
sr = pd.Series([1, 2, 3, 4], index=['1', '2', '3', '4'])
sr['1']     # index명으로 접근
sr[1]       # index순서로 접근
```

### 2)DataFrame
- 2차원 자료 구조
- 표 형식이고 엑셀과 유사하다
- 테이블 데이터라고도 한다.
- Series가 합쳐진 형태이다.
- pd.DataFrame()을 이용해 선언하며 대소문자 주의할 것
- 중첩된 리스트나 딕셔너리를 통해 DataFrame을 생성할 수 있다.
```python
# 중첩된 리스트를 통한 데이터 생성
# 각 행을 리스트로 만들어야 함
data = [['Belgium', 'Brussels', 11190846],
        ['India', 'New Delhi', 1303171035],
        ['Brazil', 'Brasília', 207847528]]
df = pd.DataFrame(data)
df
```
- 칼럼을 추가하려면 data뒤에 'columns = ['A', 'B']'를 추가한다.
```python
# 중첩된 리스트를 통한 데이터 생성
# 각 행을 리스트로 만들어야 함
data = [['Belgium', 'Brussels', 11190846],
        ['India', 'New Delhi', 1303171035],
        ['Brazil', 'Brasília', 207847528]]
df = pd.DataFrame(data, columns=['Country', 'Capital', 'Population'])
df
```
- 데이터 프레임의 데이터는 딕셔너리로 넘겨주는것이 일반적이다. 그이유는
  1. 칼럼명을 함께 넘겨줄 수 있다.
  2. 동일한 데이터 타입끼리 함께 묶어서 넘겨줄 수 있다.

칼럼과 마찬가지로 data뒤에 index=['a', 'b']를 추가하여 인덱스도 변경할 수 있다.
```python
data = {'Country': ['Belgium', 'India', 'Brazil'],
        'Capital': ['Brussels', 'New Delhi', 'Brasília'],
        'Population': [11190846, 1303171035, 207847528]}
df_2 = pd.DataFrame(data,
                    index=['aa', 'bb', 'cc'])
df_2
```
<br> - type() = 타입을 알려준다</br>
<br> df.index = 데이터의 속성을 알려준다.</br>
<br> df.columns = 콜롬값을 출력한다.</br>
<br> df.dtypes = 데이터의 타입을 출력한다. </br>
<br> df.info = 위에 모든 값을 출력한다. </br>

**혹은 특정한 칼럼을 인덱스로 사용할 수 있다. // 여러 인덱스도 가능**
```python
df_index_with_country = df.set_index('Country')
df_index_with_country 

df_index_with_country_and_capital = df.set_index(['Country', 'Capital'])
df_index_with_country_and_capital
```
