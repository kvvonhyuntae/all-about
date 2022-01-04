 # Pandas -2 // 인덱싱, 슬라이싱, 불리언 인덱싱, 삭제
 - '[&nbsp;&nbsp;&nbsp;&nbsp;]' 대괄호 연산자를 활용해 데이터를 가져올 수 있다.
 - 간단히 사용하기는 좋지만 불규칙적이라  loc혹은 iloc를 좀 더 추천
```python
df['Country'] // 단일 칼럼 조회
df[['Country', 'Population']] // 복수 칼럼 조회, 대괄호를 두번 쓴다.
```
### **슬라이싱**
[]를 통한 슬라이싱은 행(row)에 적용된다.
- index로 슬라이싱할 때와는 달리 label로 슬라이싱하는 경우, 마지막 라벨은 포함된다. // 추천하지는 않음

## 1. 인덱싱
- loc(Label based indexing)
<br>인덱스로 로케이션을 찾는 함수</br>
```python
df.iloc[0,0] # 위치를 통한 인덱싱
df.iat[0,0] # 위치를 통한 인덱싱
#같은 역할을 한다
#출력 'Belgium'

```
- iloc(Positional indexing)
<br> 라벨을 통해 로케이션을 찾는 함수</br>
때문에 콜롬값을 반드시 명시해줘야 한다. (아래 참고)
```python
df.loc[0, 'Country'] # 라벨을 통한 인덱싱
df.at[0, 'Country'] # 라벨을 통한 인덱싱
#같은 역할을 한다
#출력 'Belgium'
```

- ix(사용 권장 X)
<br> 쓰지 말것 </br>
## 2. 슬라이싱
슬라이싱 역시 인덱싱과 같은 함수(loc, iloc)를 사용한다 (아래 참고)
```python
df.iloc[0:1,0:2] # 위치를 통한 슬라이싱 (끝은 미포함)
df.loc[0:1, 'Country':'Capital'] # 라벨을 통한 슬라이싱 (끝 포함)
```
## 3. 불리언 인덱싱
- 조건을 제시하고 조건이 True인 요소만을 조회하는 방식
- 어렵다 생각이 들면 조건 먼저 만들고 Ture 인지 False인지 확인하라
- 필터링이라고도 한다.
```python
df.loc[:, 'Population'] > 200000000
df.iloc[:,:] > 200000000
df[df['Population'] > 200000000] #데이터 프레임에서 ture인 행만 데이터 프레임으로 출력
```
## 4. 삭제