# first
## 첫번째 작업
### 테스트
- 리스트1
- 리스트2

[네이버](http://www.naver.com)

[구글](http://google.com)

# sourcecode.py : 데이터 처리 파일
## Question 1: 설문조사에 참여한 사람들이 가장 많이 사용하는 소셜미디어는 무엇인가?
dataset에서 사람들이 가장 많이 사용하는 소셜 미디어 플랫폼을 분석한다. 두 개의 dataset data1과 data3를 결합하여 분석 결과를 제공한다.

# class Question1
data1과 data3 dataset을 받는다. self.smp는 'Social Media Platform' 문자열을 저장한다.

# app_dataset1: data1에서 응답자들이 자주 사용하는 앱을 추출하고, 새로운 dataframe을 만든다.
1. 분할:
data1에서 'Apps that you are frequently using' 열을 선택한다. 열의 각 값을 쉼표와 공백을 기준으로 분할하여 리스트로 만든다. 그리고 각 리스트의 요소에서 공백을 제거한다.
2. 리스트 생성:
for문을 이용해 모든 앱을 하나의 큰 리스트로 만든다.
3. 앱의 빈도 계산:
리스트를 pandas Series로 변환 후, 각 앱의 등장 빈도를 계산한다. 그리고 결과를 새로운 dataframe으로 만든다.
4. dataframe 생성:
새로운 dataFrame의 열 이름을 "Social Media Platform"와 "Count"로 설정한 후 dataframe을 반환한다.
