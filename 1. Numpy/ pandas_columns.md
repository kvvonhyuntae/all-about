#헤더가 여러줄일때 한번에 불러오는 방법
```python
cols = pd.read_csv('pima-indians-diabetes.csv', header=None, delimiter='\t')    #1. 데이터 파일을 불러온다.
cols = cols[:9]  #2. 헤더의 마지막줄까지 불러온다.
colnames = cols[0].map(lambda x: x[5:]).values #3. 앞에 불필요한 요소 제거
df = pd.read_csv('pima-indians-diabetes.csv', skiprows = 9, header=None) #4. 다시 데이터 파일을 불러온다. 
df.columns = colnames       #이전에 불러온 헤더를 새로운 데이터 파일의 헤더로 지정해준다.
df.head()
```
