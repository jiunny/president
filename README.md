# :scroll: 대한민국 대통령 취임사 Wordcloud :scroll:
wordcloud of president in Korea

## :point_up: 파일구조
```

├─ Master
  ├─ README.md
  ├─ wordcloud                  - Worldcloud 이미지
  │      김대중_wordcloud.png
  │      ...
  └─ 사진원본                    - Wordcloud 그리기 위한 테두리 이미지
  │      김대중2.jpg
  │      ...
  └─ 연설문                      - 역대 대통령 취임사 데이터
  │      김대중.txt
  └─  wordcloud.ipynb

```

```

├─ /sample/
  ├─ README.md
  ├─ requirements.txt 
  ├─ asset
  ├─ data
  │     sample.csv
  ├─ query
  │     sample.sql
  │      ...
  └─ proc                      - raw data를 전처리한 data
  │      ...
  └─ notebook                   
  │     sample.ipynb
  └─  ...


```

## :point_up: 분석방법
   &nbsp;&nbsp; 역대 대한민국 대통령의 취임사를 txt파일로 저장한 뒤에 **tf-idf 가중치** 를 계산하여 DTM을 생성하였다. <br/>
   &nbsp;&nbsp; tf-idf 가중치는 여러 개의 문서에서 공통적으로 빈번하게 등장하는 단어들은 작은 값을 부여하고, 특정 문서에서 많이 나오는 단어들은 높은 가중치를 부여하기 때문에 불용어 처리에 유용하다.
   ### 1. 불용어처리
   &nbsp;&nbsp; 과거에는 ~읍니다, ~임니다 라고 끝맺는 경우가 많았기 때문에, 읍니다는 '습니다'로, 임니다는 '입니다'로 바꾸어주었다. <br/>
   &nbsp;&nbsp; 특수기호들은 모두 제거하였다.
   
   ### 2. 형태소분석
   &nbsp;&nbsp; 한국어는 특성상 복합명사가 많기 때문에 형태소를 작은 단위로 나누게 될 경우 문맥을 따라가지 못하는 경우가 생긴다. 따라서 적절한 크기로 형태소를 나누어야 하기 때문에 5개의 형태소 분석기 중 **hannanum**을 사용하였다. 형태소 중에서 **체언, 용언, 수식언** 만을 추출하였다.
   
## :point_up: Wordcloud
&nbsp;&nbsp; 사진의 테두리에 따라서 Wordcloud를 그리고 싶다면, **원하는 테두리를 제외한 부분은 모두 흰색**이어야한다. 샘플 사진은 사진원본 폴더를 참고하면 된다. <br/>
&nbsp;&nbsp; 사진이 준비되면, Python의 ImageColorGenerator를 사용하여 사진의 색상을 추출해 내고, 이를 Wordcloud 글자색에 지정하면 된다.<br/>
&nbsp;&nbsp; 아래 사진은 노무현 대통령 취임사를 분석한 Wordcloud 예시이다.

<img src="https://user-images.githubusercontent.com/59464528/96473904-28ca1680-126d-11eb-8383-ac9a518d5654.png" width="300" height="350">
