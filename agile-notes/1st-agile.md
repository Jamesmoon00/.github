# 📌 개발 기간
### 2024-07-23 ~ 2024-08-27

<br/><br/><br/>

# 🔃 개발 과정 
### 요구사항 정의
<img src="https://github.com/user-attachments/assets/15c4e175-1742-4650-b45f-79398287c139"  width="500"/>
<br/>

<img src="https://github.com/user-attachments/assets/458a06ce-a45d-459a-b852-cf22552cffa8"  width="500"/>
<br/>

<img src="https://github.com/user-attachments/assets/c6ee6063-5a0e-4a20-b06e-38927e47bd08"  width="500"/>
<br/>

<br/><br/>

### API 명세서

<br/><br/>

### 데이터베이스 (ERD)
<img src="https://github.com/user-attachments/assets/aabf7ec0-16c3-4b35-b4ec-ec9fd7e155bf" width="500"/>

<br/><br/>

### 일정 관리 (WBS)
<img src="https://github.com/user-attachments/assets/3d94314a-aa08-4438-8469-f9a1f350c4a9"  width="500"/>

<br/><br/><br/>

# 🗺️ 프로젝트 결과
<img src="https://github.com/user-attachments/assets/2032a535-03c4-4f7e-a3eb-363bee077b90"  width="500"/>

<br/><br/><br/>

# 🗨️ 후기

민정 - 🌈 3차까지 할 수 있을까요? 가 아니라 해야죠 화이팅 ! 💖

은진 - 룰루랄라 2차도 화이팅 :)  (이게 toy가 맞나요?)

종식 - 언제쯤 1인분을 할 수 있을까..?

해린 - 분명 1차때 다 할 수 있을 줄 알았는데 2,3차로 넘어가버리는 마술 … ? 🧙🏻

건우 - 저는 행복해요😊

<br/><br/><br/>

# 💣 이슈로그
**⚠️ 이모지 인코딩 오류 [데이터베이스]**

[문제] 리뷰 내용 데이터베이스 적재시 인코딩 문제로 인한 오류 발생

[해결] utf8mb4로 character set을 변경해주어 이모지 적재가 가능하도록 함 

```sql
ALTER TABLE review_tb CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

<br/>

**⚠️ 운영시간의 큰 형식 차이 [데이터 전처리]**

[문제] 요일마다 있는 곳도 있으며, 시간만 있는 곳도 있었으나 하나의 형식으로 맞추어야 했음

[해결] 요일마다 있더라도 대부분의 시간대가 동일하므로, 00:00 ~ 00:00 형식의 데이터 추출( & 정기 휴무)로써 통일화

<br/>


**⚠️ 전처리 코드 통일화 필요 [데이터 전처리]**

[문제] 크롤링을 분담하여 수행하다보니, 데이터 형식의 차이 존재

[해결] encoding : utf-8로 통일, 컬럼명 통일 과정 거침 (하나의 코드로 전처리 가능하도록)

<br/>

**⚠️ datetime type error [데이터 전처리]**

[문제] Python의 timestamp가 MySQL로 들어가지 못함

```python
>> Python 'timestamp' cannot be converted to a MySQL type
```

[해결] timestamp를 datetime으로 변환하여 적재 (pd.to_datetime 활용)

<br/>

**⚠️ 지도 시각화 버튼 인식 오류 [프론트엔드]**

[문제] 서울시의 중심이 기준으로 인식되어 버튼 호버→ 확대시 좌우, 상하 이동 발생

[해결] 구의 각 요소에 중심값을 설정하여 시각적으로 잘 확대되도록 해결

<br/>

**⚠️ 지도 클릭이 안되는 오류 [크롤링]**

[문제] 네이버 페이지 특성 상 Iframe으로 감싸져 있어 페이지 클릭이 안되는 오류 발생

[해결] 네이버 지도에서 가게 코드를 따와 모바일 버전 링크로 1차 크롤링 후 가게 정보, 리뷰에 대한 2,3차 크롤링 진행

<br/>

**⚠️  리뷰에 포함된 각종 태그 인식 오류 [크롤링]**

[문제] 원하는 태그를 가져올 때 제대로 인식이 안되서 에러 발생

[해결] 태그를 따로 지정해놓은 후 같은 태그가 있으면 저장하는 방법 사용

<br/>

**⚠️ 리뷰가 없는 가게 인식 문제 [크롤링]**

[문제] 리뷰가 없는 가게 무한 페이지 다운 오류 발생

[해결] break, continue 를 사용했을 때 정상적인 가게들의 리뷰 크롤링 마저 문제가 생겨 리뷰가 없는 가게 행 삭제

<br/>

**⚠️ 식당 정보 데이터 문제 [크롤링]**

[문제] 서울시 식당 정보 데이터를 받아왔으나, 프랜차이즈나 가게 명으로만 검색할 경우 여러개의 가게가 검색되거나 혹은 해당 가게가 검색되지 않는 오류 발생

[해결] 가게명과 주소 일부를 같이 작성해 검색함

<br/>

**⚠️ 식당 정보 데이터 문제 [크롤링]**

[문제] 폐업한 가게를 제외하고 검색했으나 해당 가게가 존재하지 않는 이슈 발생

[해결] 1차 애자일에서는 주소값이 없는 가게를 제외하고 크롤링 → 주소값이 없는 가게를 2차 크롤링을 할 지, 없는 가게로 칭할 지 아직 미정

<br/>

**⚠️  팝업 데이터 크롤링 지연 문제 [크롤링]**

[문제] 팝업 페이지를 크롤링 중 path값의 오류가 없음에도 크롤링이 진행되지 않는 문제 발생

[해결] WebDriverWait를 바탕으로 리소스별 로딩 대기 시간을 주어 해결함

<br/>


**⚠️ 리뷰 크롤링 시 더보기 버튼 오류 [크롤링]**

[문제] 리뷰 크롤링을 하다 보면 랜덤으로 몇몇 가게는 10개 이상의 리뷰가 있음에도 불구하고 더보기 버튼을 누르지 않아 10개의 리뷰만 긁어옴

[해결] 원인 파악 중

<br/>