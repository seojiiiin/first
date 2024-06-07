# SNS가 정신건강에 미치는 영향
SSU Python Programming Final Project

# Libraries
-pandas
-numpy
-matplotlib.pyplot
-seaborn
-Counter in collections
    
# Datasets
-data1과 data2 : [SMA22](https://www.kaggle.com/datasets/zaranaramani/analysis-and-reducing-social-media-addiction)의 collected_dataset
-data3 : [SG](https://www.kaggle.com/datasets/globalmediadata/social-media-data-sg-1)의 Social_Media_Data_SG_2

# sourcecode.py : 데이터 처리 파일

## Question 1 : 설문조사에 참여한 사람들이 가장 많이 사용하는 소셜미디어는 무엇인가?
dataset에서 사람들이 가장 많이 사용하는 소셜 미디어 플랫폼을 분석한다. 두 개의 dataset data1과 data3를 결합하여 분석 결과를 제공한다.
### class Question1
data1과 data3 dataset을 받는다. self.smp는 'Social Media Platform' 문자열을 저장한다.
#### app_dataset1: data1에서 응답자들이 자주 사용하는 앱을 추출하고, 새로운 dataframe을 만든다.
1. 분할:
data1에서 'Apps that you are frequently using' 열을 선택한다. 열의 각 값을 쉼표와 공백을 기준으로 분할하여 리스트로 만든다. 그리고 각 리스트의 요소에서 공백을 제거한다.
2. 리스트 생성:
for문을 이용해 모든 앱을 하나의 큰 리스트로 만든다.
3. 앱의 빈도 계산:
리스트를 pandas Series로 변환 후, 각 앱의 등장 빈도를 계산한다. 그리고 결과를 새로운 dataframe으로 만든다.
4. dataframe 생성:
새로운 dataFrame의 열 이름을 "Social Media Platform"와 "Count"로 설정한 후 dataframe을 반환한다.
#### app_dataset2: data3에서 응답자들이 자주 사용하는 앱을 추출하고, 새로운 dataframe을 만든다.
1. 데이터 추출, 빈도 계산:
data3에서 응답자들이 자주 사용하는 앱을 추출하고, Counter를 이용해 빈도를 계산한다. 
2. dataframe 생성:
count_app 딕셔너리를 DataFrame으로 변환하고, 열 이름을 'Social Media Platform'과 'Count'로 설정한다. 
#### combine_data: 처리한 두 dataframe을 결합한다.
1. 결합:
concat을 이용해 정리된 두 dataframe을 결합한다. 
2. 그룹화, 합산:
groupby를 이용해 각 SNS 별 사용 빈도를 합산한다. 
3. 정렬:
sort_values를 이용해 "Count" 값이 큰 순서대로 행을 정렬한다.
4. 결과 반환:
병합된 새로운 dataframe을 return한다.
#### app_age: 나이대별로 가장 많이 사용하는 앱을 시각화한다.
1. 분할:
나이대를 기준으로 자주 사용하는 앱을 추출한다.
2. 스택 및 변환:
나이대별 자주 사용하는 앱 이름들을 인덱스와 함께 하나의 긴 Series로 만든다. stack된 값을 'App' 열로 변환한다.
3. dataframe 생성:
나이대별 각 앱의 빈도를 계산한 새로운 dataframe을 생성한다.
4. 시각화:
최종 dataframe을 산점도로 시각화한다.
#### run_analysis: 위에서 만든 함수를 호출하고 결합된 데이터를 반환한다.
#### plot_results: 결합된 최종 데이터의 결과를 막대 그래프로 시각화한다.
### 전체 흐름
1. app_dataset1 및 app_dataset2에서 데이터를 추출하고 각 앱의 빈도를 계산한다.
2. combine_data에서 데이터를 결합하고 정리한다.
3. run_analysis에서 전체 분석을 수행하고 결과를 반환한다.
4. plot_results에서 분석 결과를 시각화한다.

## Quesition 2 : SNS를 사용하는 평균 시간과 불안 수준, 수면의 질 간의 상관관계는 어떻게 되는가?
data3에서 사람들의 불안수준과 수면의 질 점수를 SNS 사용시간대별로 분석하여 SNS가 개인의 감정 상태에 얼마나 영향을 주는지 알아본다. 
### Function Question2
1. 사용시간대별로 그룹을 나누고 그룹별 수면의 질 점수, 불안수치의 평균을 계산한다.
2. 사용시간, 수면의 질 점수, 불안수치를 나타내는 새로운 데이터프레임을 생성한다.
3. 최종 데이터프레임을 막대그래프로 시각화하여 SNS사용시간대 별 수면의 질 점수와 불안수치를 나타낸다.

## Question 3 : SNS 사용의 가장 큰 폐해는 무엇인가?
data1에서 SNS 사용의 부정적인 영향에 대해 응답자들이 동의한 경우를 필터링하여, 각 부정적인 영향에 대한 응답의 개수를 계산하고 이를 시각화한다.
### Function Question3
1. 응답 필터링:
data1에서 SNS 사용의 부정적인 영향에 대한 질문에 "often", "very often", "Agree", "Strongly agree"로 응답한 행들을 필터링한다.
각 부정적인 영향에 대해 필터링된 행의 개수를 계산한다.
2. 딕셔너리 생성:
부정적인 영향과 해당 영향에 대한 응답의 개수를 저장하는 딕셔너리를 생성한다. 
부정적인 영향은 'Urge to use social media more.', 'Avoidance of problems', 'Being restless without social media', 'A sense of incompetence','Lost confidence'이다.
3. dataframe 생성:
생성한 딕셔너리를 dataframe으로 변환한다.
4. 시각화:
최종 dataframe을 막대 그래프로 시각화하여, 각 부정적인 영향에 대해 얼마나 많은 응답자들이 동의했는지를 나타낸다.

## Question 4 : SNS를 사용하는 평균 시간에 따른 중독 치료법의 효과는 어떻게 다른가?
### Function Question4
1. 중독 치료법을 나타내는 열 번호를 추출한다.
2. 효과 수치별 빈도수를 계산한다. (process_group)
3. 사용 시간대 별로 그룹을 나누고, 그룹별 치료방법의 효과수치 빈도를 계산한다.
4. 가장 효과적인 방법을 찾는다. (get_best_methods)
5. 사용시간대에 따른 가장 효과적인 중독 치료방법을 나타내는 데이터프레임 생성한다.

# test.py : 데이터 분석 테스트 파일
# main.py : 데이터 분석 수행 파일

# Reproduce
1. 위의 Datasets를 다운받는다.
2. 같은 폴더 내에서 다운받은 data들과 sourcecode.py, main.py를 연다.
2. main.py를 실행한다.
