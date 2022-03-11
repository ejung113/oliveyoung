#### 올리브영 데이터 전처리



```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
```

```python
df = pd.read_csv("olive_data_crawling.csv")
df
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>닉네임</th>
      <th>태그</th>
      <th>별점</th>
      <th>작성일</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
      <th>피부타입</th>
      <th>리뷰</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>혜요미</td>
      <td>복합성\n봄웜톤</td>
      <td>4</td>
      <td>2021.12.11</td>
      <td>보통이에요</td>
      <td>예상보다 짧아요</td>
      <td>보통이에요</td>
      <td>건성에 좋아요</td>
      <td>📦제품상태\n아..올리브영 온라인으로 시키는 물건들 처음 상태가\n좀 별로인 경우가...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>숑댕</td>
      <td>스킨케어 분야 탑리뷰어</td>
      <td>5</td>
      <td>2021.11.23</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>미 제품 미쳤어요\n저는 여기에 정착하려규요\n리뷰에 가격이 비싸다는 글이 많던데 ...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>여쿨라제품내줘</td>
      <td>지성\n여름쿨톤\n트러블\n홍조</td>
      <td>5</td>
      <td>2021.12.13</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>🌸여쿨라이트 20호(밝은 21호)🌸\n\n어며들었다..😲\n이러다간 듀틴트까지 구매...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>ho****</td>
      <td>지성\n웜톤\n모공\n블랙헤드</td>
      <td>5</td>
      <td>2021.12.16</td>
      <td>아주 만족해요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>젤리쿠션이라 그런지 수분감과 쿨링이 아주 맘에 드네요! 얇게 올라가서 스킨케어하는 ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>yuriful</td>
      <td>메이크업 분야 탑리뷰어</td>
      <td>4</td>
      <td>2021.11.03</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>21호 수부지💖\n올라이브에서 구매했는데 배송 정말 빠르게 왔어요🤭\n슬기 포토카드...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>523</th>
      <td>523</td>
      <td>ciel****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.11.02</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>건성에 좋아요</td>
      <td>촉촉 하면서 가볍고 건성이랑 들뜸 걱정했는데 \n펴버르기도 쉽고 성분도 괜찮아여\n...</td>
    </tr>
    <tr>
      <th>524</th>
      <td>524</td>
      <td>jenn****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.10.31</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>복합성에 좋아요</td>
      <td>너무 건조한걸 쓰면 떠버리는데 이상품은 안그런  것 같아요\n\n다음에 또 재구매 ...</td>
    </tr>
    <tr>
      <th>525</th>
      <td>525</td>
      <td>alsgmlwk****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.10.30</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
      <td>건성에 좋아요</td>
      <td>환절기에 사용하기 좋은 촉촉이 쿠션입니다. 그렇다고 해서 마스크에 묻어남이 많다거나...</td>
    </tr>
    <tr>
      <th>526</th>
      <td>526</td>
      <td>dmsdl****</td>
      <td>NaN</td>
      <td>5</td>
      <td>2021.10.30</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>복합성에 좋아요</td>
      <td>전에 버전은 만족했는데 저렴하게 구매해서 좋아요 이것도 좋겠주ㅡ</td>
    </tr>
    <tr>
      <th>527</th>
      <td>527</td>
      <td>tk****</td>
      <td>NaN</td>
      <td>4</td>
      <td>2021.11.05</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>복합성에 좋아요</td>
      <td>어뮤즈 팩트 사용하고 있어서 새로나와서 구매해봤어요\n아직 사용은 안해봤는데 리뷰보...</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 10 columns</p>



#### 1. 별점, 발색력, 지속력, 수분감만 DataFrame



```python
result_1 = df[["별점","발색력","지속력","수분감"]]
result_1
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>보통이에요</td>
      <td>예상보다 짧아요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>523</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>524</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>525</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>526</th>
      <td>5</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>527</th>
      <td>4</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 4 columns</p>



##### 1\) 별점 오름차순 정렬



```python
df=result_1.sort_values(by="별점",ascending = True)
df
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>아주 만족해요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>다소 아쉬워요</td>
      <td>예상보다 짧아요</td>
      <td>매트해요</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
      <td>보통이에요</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>다소 아쉬워요</td>
      <td>예상보다 짧아요</td>
      <td>매트해요</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>다소 아쉬워요</td>
      <td>보통이에요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>아주 만족해요</td>
      <td>지속이 오래돼요</td>
      <td>아주 촉촉해요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 4 columns</p>



##### 2\) 발색력, 지속력, 수분감 수치화



```python
def color(x):
    if x=='다소 아쉬워요':
        return 1
    elif x=='보통이에요':
        return 2
    else:
        return 3
```

```python
df["발색력"]=df["발색력"].apply(color)
```

```python
def last(x):
    if x=='예상보다 짧아요':
        return 1
    elif x=='보통이에요':
        return 2
    else:
        return 3
```

```python
df["지속력"]=df["지속력"].apply(last)
```

```python
def water(x):
    if x=='매트해요':
        return 1
    elif x=='보통이에요':
        return 2
    else:
        return 3
```

```python
df["수분감"]=df["수분감"].apply(water)
df
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 4 columns</p>



##### 3\) 별점 기준 점수 평균치



```python
df_1 = df.groupby("별점").mean().transpose()
df_1
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>별점</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>발색력</th>
      <td>1.636364</td>
      <td>1.777778</td>
      <td>1.851852</td>
      <td>2.253165</td>
      <td>2.696517</td>
    </tr>
    <tr>
      <th>지속력</th>
      <td>1.363636</td>
      <td>1.888889</td>
      <td>1.777778</td>
      <td>2.113924</td>
      <td>2.544776</td>
    </tr>
    <tr>
      <th>수분감</th>
      <td>2.181818</td>
      <td>2.444444</td>
      <td>2.592593</td>
      <td>2.670886</td>
      <td>2.863184</td>
    </tr>
  </tbody>
</table>


#### 2. 문제점 보완해서 DataFrame



##### 1\) 가장 좋은 평가 제외 모두 zero 처리



```python
df = pd.read_csv("olive_data_crawling.csv")
```

```python
df = df[["별점","발색력","지속력","수분감"]]
```

```python
df=df.sort_values(by="별점",ascending = True)
```

```python
def color(x):
    if x=='아주 만족해요':
        return '발색력 좋아요'
    else:
        return 'zero'
```

```python
df['발색력']=df['발색력'].apply(color)
```

```python
def last(x):
    if x=='지속이 오래돼요':
        return '지속력 좋아요'
    else:
        return 'zero'
```

```python
df['지속력']=df['지속력'].apply(last)
```

```python
def water(x):
    if x=='아주 촉촉해요':
        return '수분감 좋아요'
    else:
        return 'zero'
```

```python
df['수분감']=df['수분감'].apply(water)
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>발색력 좋아요</td>
      <td>zero</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>수분감 좋아요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 4 columns</p>



##### 2\) 기능 열 추가



```python
df['기능']=df['발색력']+","+df['지속력']+","+df['수분감']
df
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>발색력</th>
      <th>지속력</th>
      <th>수분감</th>
      <th>기능</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>발색력 좋아요</td>
      <td>zero</td>
      <td>zero</td>
      <td>발색력 좋아요,zero,zero</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero,zero,zero</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero,zero,zero</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero</td>
      <td>zero,zero,zero</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>zero</td>
      <td>zero</td>
      <td>수분감 좋아요</td>
      <td>zero,zero,수분감 좋아요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>발색력 좋아요</td>
      <td>지속력 좋아요</td>
      <td>수분감 좋아요</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 5 columns</p>



```python
df_1 = df[["별점","기능"]]
df_1
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>기능</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>발색력 좋아요,zero,zero</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>zero,zero,zero</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>zero,zero,zero</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>zero,zero,zero</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>zero,zero,수분감 좋아요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 2 columns</p>



```python
def func(x):
    if x=='발색력 좋아요,zero,zero':
        return '발색력 좋아요'
    elif x=='zero,지속력 좋아요,zero':
        return '지속력 좋아요'
    elif x=='zero,zero,수분감 좋아요':
        return '수분감 좋아요'
    elif x=='zero,지속력 좋아요,수분감 좋아요':
        return '지속력 좋아요,수분감 좋아요'
    elif x=='발색력 좋아요,zero,수분감 좋아요':
        return '발색력 좋아요,수분감 좋아요'
    elif x=='발색력 좋아요,지속력 좋아요,zero':
        return '발색력 좋아요,지속력 좋아요'
    elif x=='zero,zero,zero':
        return 'zero'
    else:
        return '발색력 좋아요,지속력 좋아요,수분감 좋아요'
```

```python
df_1['기능']=df_1['기능'].apply(func)
df_1
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>기능</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>1</td>
      <td>발색력 좋아요</td>
    </tr>
    <tr>
      <th>312</th>
      <td>1</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>58</th>
      <td>1</td>
      <td>zero</td>
    </tr>
    <tr>
      <th>507</th>
      <td>1</td>
      <td>수분감 좋아요</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>245</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>244</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>243</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
    <tr>
      <th>263</th>
      <td>5</td>
      <td>발색력 좋아요,지속력 좋아요,수분감 좋아요</td>
    </tr>
  </tbody>
</table>
<p>528 rows × 2 columns</p>



##### 3\) 별점에 따른 기능 count



```python
df_2=df_1.loc[df_1.기능.str.contains("좋아요")]
df_2
df_2.to_csv("team_3")
```

```python
df_3=df_2.loc[df['별점']==5]
print(len(df_3.loc[df_3.기능.str.contains("발색력")]))
print(len(df_3.loc[df_3.기능.str.contains("지속력")]))
print(len(df_3.loc[df_3.기능.str.contains("수분감")]))
```

```html
290
230
347
```



##### 4\) 별점에 따른 기능 나눠서 count



```python
df = pd.read_csv('team_3') 
data = []
for i,v in enumerate(df_2['기능'].values):
    for j in v.split(','):
        data.append({'별점':df.iloc[i][df.columns[1]],'기능': j.split()[0]})
```

```python
df = pd.DataFrame(data)
df
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>별점</th>
      <th>기능</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>발색력</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>수분감</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>수분감</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>발색력</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>수분감</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>991</th>
      <td>5</td>
      <td>지속력</td>
    </tr>
    <tr>
      <th>992</th>
      <td>5</td>
      <td>수분감</td>
    </tr>
    <tr>
      <th>993</th>
      <td>5</td>
      <td>발색력</td>
    </tr>
    <tr>
      <th>994</th>
      <td>5</td>
      <td>지속력</td>
    </tr>
    <tr>
      <th>995</th>
      <td>5</td>
      <td>수분감</td>
    </tr>
  </tbody>
</table>
<p>996 rows × 2 columns</p>



##### 5) 별점에 따른 피부타입 dataframe



```python
df = pd.read_csv("olive_data_crawling.csv")
```

```python
df = df[["별점","피부타입"]]
```

```python
data = pd.DataFrame(df)
print(data)
```

```html
     별점      피부타입
0     4   건성에 좋아요
1     5   건성에 좋아요
2     5   건성에 좋아요
3     5   건성에 좋아요
4     4   건성에 좋아요
..   ..       ...
523   5   건성에 좋아요
524   5  복합성에 좋아요
525   5   건성에 좋아요
526   5  복합성에 좋아요
527   4  복합성에 좋아요

[528 rows x 2 columns]
```

