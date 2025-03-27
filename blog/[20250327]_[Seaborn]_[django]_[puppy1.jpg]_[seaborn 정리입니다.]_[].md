# 데이터 시각화 정리

***1. 데이터 시각화 개요***

데이터를 효과적으로 표현하기 위해 여러 시각화 기법을 사용할 수 있습니다. Seaborn 라이브러리는 강력한 시각화 기능을 제공하며, 다양한 테마와 스타일을 적용할 수 있습니다.

***2. 막대 그래프 (Bar Plot)***

```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt

# 데이터 불러오기
df = pd.read_csv('파일경로')

# 기본 막대 그래프
sns.barplot(data=df, x='컬럼명', y='컬럼명')
plt.show()
```

추가 옵션

```python
sns.set_theme(rc={'figure.figsize': (7, 6)}, style='dark')  # 스타일 및 크기 설정
sns.barplot(data=df, x='컬럼명', y='컬럼명', errorbar=None, hue='그룹컬럼')
plt.show()
```

• figure.figsize: 그래프의 가로, 세로 크기 조절
• style: 배경 스타일 지정 (dark, whitegrid 등 가능)
• hue: 추가적인 그룹핑 정보 표현

• errorbar=None: 에러바 제거

***3. 선 그래프 (Line Plot)***

```python
sns.set_theme(rc={'figure.figsize': (7, 6)}, style='dark')
sns.lineplot(data=df, x='컬럼명', y='컬럼명', errorbar=None, hue='그룹컬럼')
plt.show()
```

Seaborn 스타일 옵션

pastel, muted, colorblind 등 다양한 테마 지원

font='폰트명'을 사용하여 폰트 설정 가능

***4. 점 그래프 (Strip Plot)***

```python
sns.stripplot(data=df, x='컬럼명', y='컬럼명', hue='그룹컬럼')
plt.show()
```

Tip: 값들이 겹쳐서 보기 어려운 경우 swarmplot을 사용하면 더욱 보기 쉬운 그래프가 됩니다.

```python
sns.swarmplot(data=df, x='컬럼명', y='컬럼명', hue='그룹컬럼')
plt.show()
```

***5. 박스 플롯 (Box Plot) & 바이올린 플롯 (Violin Plot)***

```python
sns.boxplot(data=df, x='컬럼명', y='컬럼명')
plt.show()

sns.violinplot(data=df, x='컬럼명', y='컬럼명')
plt.show()
```

• 박스 플롯: 데이터의 분포와 이상치를 확인하는 데 유용함
• 바이올린 플롯: 박스 플롯과 밀도 플롯을 결합한 형태로, 분포를 더 직관적으로 볼 수 있음
• 흰 점은 중간값(median)을 나타냄

***6. 히스토그램 (Histogram)***

```python
sns.histplot(data=df, x='컬럼명', bins=10, multiple='stack')
plt.show()
```

• KDE Plot (확률 밀도 함수 그래프)

```python
sns.kdeplot(data=df, x='컬럼명', bw_adjust=0.5)
plt.show()
```

***7. 산점도 (Scatter Plot) & 회귀선 (Regression Line)***

```python
sns.set_theme(rc={'figure.figsize': (5, 5)}, style='dark')
sns.scatterplot(data=df, x='컬럼명', y='컬럼명')
plt.show()

sns.regplot(data=df, x='컬럼명', y='컬럼명')
plt.show()
```

***8. 상관 관계 분석 (Correlation Analysis)***
• 상관 계수 계산 (Correlation Coefficient)

```python
df.corr(numeric_only=True)
```
피어슨 상관계수: -1(강한 음의 상관), 0(상관 없음), 1(강한 양의 상관)

```python
df.corr(numeric_only=True)['특정 컬럼'].sort_values(ascending=True)
```
• 특정 컬럼과 다른 컬럼들의 상관 관계를 정렬하여 확인

***히트맵 (Heatmap)***

```python
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
plt.show()
```
• 데이터 간 상관관계를 한눈에 파악할 수 있는 시각화 기법