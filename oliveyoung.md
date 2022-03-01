### 리뷰 분석



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



#### 1) 별점 오름차순정렬



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



#### 2) 발색력, 지속력, 수분감 수치화



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



#### 3) 별점 기준 점수 평균치



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

```python
plt.rc('font',family = "Malgun Gothic")
sns.lineplot(data=df_1)
```

![png](data:image/png;base64,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)



### 2. 문제점을 보완해 새롭게 DataFrame



#### 1) 가장 좋은 평가 제외 모두 zero처리



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



#### 2) 기능 열 추가



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



#### 3) 별점에 따른 기능 구분



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

