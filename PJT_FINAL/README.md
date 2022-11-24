

 # Cucken

### 왜 Gucken 구큰 인가?

국카스텐(Guckkasten) : ‘Guck'(보다) + 'Kasten'(상자) , 만화경. 영화의 초시.

<img src="https://lh3.googleusercontent.com/q8ELCatxWuH5Rfm-zxe052EO6d8dVx0PXzC_LBdT4BeMeKqYqmmrq1rl_tolQplZIZR9DMO2CiQENEy3SPTHvHDH6rPoVhUrl5ra3KqvA3Pq-MpQhjsMi15QPgF3b7SMXQolD_iTjO2-F08UgWeU1v06p0cExqpvOddOsRRP0l6TK4XtZBfvbPM1nagLyQ" alt="img"  />



만화경처럼 함께 영화를 보고 대화를 나누는 영화 추천 기반 커뮤니티 웹 서비스를 제공하겠다는 의미에서 이름을 따옴. 또한 버튼을 누르면 다음 사진으로 넘어가는 만화경처럼 클릭하면 유저가 원하는 화면을 보여주는, 사용자 친화적 UI UX 를 디자인을 했음. 



# 가. 개발 기획



## 1) 개발 기간

📅 2022 11.16 ~ 2022.11.24 (9일)



## 2-1) 전략

OTT 시장의 어려움!

<img src="https://lh3.googleusercontent.com/Mio4i_0R4ZThdXJZ7dHi-xIHiXRBSbTHf7lLppAi-ipOhAZbce8TVkrkLPAL68L96FBtIy2Ni-MW5Tk45hB2kk64bZ1AE0_-4HM9Rg92Ine8XEhKSKmc_GUp4SI0yb09irScwHHsa_tLgoCu6ahrEEas7jmdfEjntJUS6UAAM8eNkDUytLwnd3U2CjfLYQ" alt="img" style="zoom:67%;" />

코로나 팬데믹으로인한 사회적 거리두기 해제 이후 사람들의 OTT 서비스에대한 관심사와 구독자와 관심수가 급감했다. 이에대한 해결책으로 Netflix CEO는 서비스에 게임을 제공하겠다고 했지만 발표 이후 주가 급락. (시장에서는 별로 설득력이 없다고 판단)



## 2-2) 우리의 전략은

 sns, 즉 영화기반 토론장을 만들고, 그 안에서 사람들간에 경쟁심을 부추긴다.특정 요건을 충족하는 충성 고객에게 벳지를 줘 보상한다.Follower가 많을수록, 영화에 평론을 많이 남길수록, 좋아요를 많이 받을수록 보상

<img src="https://lh5.googleusercontent.com/m2i6ENaBErlJpjUsxPyyLs5oerpHbuPZUfUv9pDKQJVW2a-I890KL9LwODS0uDDZ6UmJJ5KQHiyw1dkX1ypC9BCGWt6yWRxIYIz1iIm_sLGTDEVrClIBiNWqL84fhTkN36zkm913YbHQS8VjN6WAnDjxxXfhKoUNcEDa4QjO7QLH2i9XBa1PPSjOXnxFeg" alt="img" style="zoom: 33%;" />         <img src="https://lh6.googleusercontent.com/-W_YQYqDgQJjecfKnWrrhrICiYsigmXkW5PdYOuEIg0u67vJW114EtOt5PzyX4S9FZhDvA5KnLngI54jS0n9aigQ-zSBQ4zJ8suBqyNbBDkjZJnvTRIwNUFO6L_Bng-I1qTLSVz8F8MkDOLqagO3W-HQvlmGutVoQrSxbeGO5nKW8k6H0iEPafl7eQIJXg" alt="img" style="zoom:50%;" />

## 3) 구현 알고리즘

Top 10 영화에 가중치 반영(모든 유저) **Jellyfish** 검색(모든 유저) 코사인 유사도 기반 추천(가입 및 좋아요 남긴 유저)

###  ㄱ - Top 10 영화 가중치

​		**![img](https://lh5.googleusercontent.com/q-gUqdjQsRdhkjxhrA-t8XutPoFNLzew4yWTi8CafPLVpV5pQFjmz7HcqWtukCAV05T_y0-mpbHHWXOTryK8gQ-VRyrDf8_vPO9Z2LGaj21CaWv6MELZTzxwvovPjtxPhA_PeCgFPzIxRlrV9--PUIpaD5KfoLT-i1bB7E0yh3mlsfPzcAv_vmAnJzwrvg)**

v = 영화 평가 수

R = 영화 평점 평균

m : 상위 10분위에 든 영화들 수

C = 모든 영화의 평점 평균 (TMDB 1만 기준 약 6)



### ㄴ - 영화 탐색(머신러닝)

**jaro_winkler_similarity**  

**‘아포칼’** 을 검색했을 때 유사도 높은 영화 5개

{'pk': 1579, 'title': '아포칼립토', 'similarity': 0.9066666666666667}, 

{'pk': 539064, 'title': '아포칼립스: 최후의날', 'similarity': 0.825}, 

{'pk': 531876, 'title': '아웃포스트', 'similarity': 0.6888888888888888},

{'pk': 17182, 'title': '아이 포 아이', 'similarity': 0.6507936507936508},

{'pk': 9045, 'title': '아멘', 'similarity': 0.611111111111111}



##  ㄷ - 코사인 유사도 기반<img src="https://lh4.googleusercontent.com/tS3GrSuQcWeW2Y527Rlyj_ouQtxknoF1risUYEHf6icoDv6PrPOP0OlCDWXftGXBU50zxwQbITHTsuqj0Jg1kqYiszSSnJEHZK97ukRs9u-KJn6z4HwzVV-3_cnBtKLJXJoFtuf8WVx04wrgjlfkADLalega8FYBeHAOiV8L70vdi9gmzDjKV4RxxZ8jew" alt="img" style="zoom:67%;" />



```python
from sklearn.feature_extraction.text import CountVectorizer

from sklearn.metrics.pairwise import cosine_similarity
```

1. 불용어 제거

   countVec = CountVectorizer(max_features=10000, stop_words='english')

2. 영화 키워드 벡터라이징

    dataVectors = countVec.fit_transform(xMovie).toarray()

3. 코사인 유사도

    similarity = cosine_similarity(dataVectors)

   


#### **데이터** : TMDB 사이트에서 1만 여개의 영화 정보

**참고** : Kaggle TMDB 5000 ‘인구 통계학적 필터링’, ‘ 컨텐츠 기반 필터링’ 모델



## 4) 와이어 프레임

 디자인 툴 **Figma**를 이용하여 제작 (

[Figma]: https://www.figma.com/file/BCFGbnuMcrwurTI2wEQMF3/JAY-PAK-x-LMH?node-id=0%3A1&amp;t=1kuXHcklbuDBJemQ-0	" Figma"

)

![image-20221123213432933](README.assets/image-20221123213432933.png)

- 페이지별 UI 구성 기획

- 페이지 옆 메모 기능을 활용해 팀원간의 비동기적 소통 및 기록



## 5) ERD

![Final_1](README.assets/Final_1.png)Django DB 구성에 필요한 roadmap 설계



## 6) API 설계



| HTTP verb | URL패턴            | 설명 |
| --------- | ------------------ | ---- |
|           | `admin`            |      |
|           | `movies/`          |      |
|           | `profile/`         |      |
|           | `accounts/`        |      |
|           | `accounts/user/`   |      |
|           | `accounts/signup/` |      |





| HTTP verb | URL 패턴                          | 설명 |
| --------- | --------------------------------- | ---- |
|           | `profile/<int:user_pk>/`          |      |
|           | `profile/<int:user_pk>/follow/`   |      |
|           | `profile/<int:movie_pk>/article/` |      |
|           | `profile/<int:user_pk>/update/`   |      |





| HTTP verb | URL 패턴                                                     | 설명 |
| --------- | ------------------------------------------------------------ | ---- |
|           | `movies/`                                                    |      |
|           | `movies/top/`                                                |      |
|           | `movies/popularity/`                                         |      |
|           | `movies/<int:user_pk>/recommendation/`                       |      |
|           | `movies/<int:movie_pk>/`                                     |      |
|           | `movies/<int:movie_pk>/addlist/`                             |      |
|           | `movies/search/genre/all/`                                   |      |
|           | `movies/search/genre/<int:genre_pk>/`                        |      |
|           | `movies/search/<str:movie_name>/`                            |      |
|           | `movies/<int:movie_pk>/articles/`                            |      |
|           | `movies/<int:movie_pk>/articles/<int:rating_pk>/`            |      |
|           | `movies/<int:movie_pk>/articles/<int:article_pk>/comments/`  |      |
|           | `movies/<int:movie_pk>/articles/<int:article_pk>/comments/like/` |      |





# 나. 프로젝트 소개

## 개발 도구



- BE: Django

- DB: Sqlite3

- FE: Vue, Vuex, VueBootStrap

- UI tool: Figma

  

## 주요 기능

ㄱ.  회원가입 페이지

<img src="README.assets/signup_AdobeExpress.gif" alt="signup_AdobeExpress" style="zoom:150%;" />

- 비밀번호 확인이 틀리거나, 이미 가입되어 있는 이메일이면 alert로 알려줌

- 회원가입 완료시 자동 로그인 -> 홈 화면으로 이동

- 가입 시 프로필 사진 생략 가능

- 이 경우 기본 이미지로 최초 설정

  

ㄴ.  로그인 페이지

<img src="README.assets/login_AdobeExpress.gif" alt="login_AdobeExpress" style="zoom:150%;" />

- 로그인시 바로 메인 페이지로 이동

- 회원가입 페이지 이동 버튼 배치

  

ㄷ.  로그아웃 및 비로그인 유저 기능 제한

<img src="README.assets/logout_AdobeExpress.gif" alt="logout_AdobeExpress" style="zoom:150%;" />

- 로그아웃 버튼 클릭시 확인을 위한 창 뜸

- 비로그인 유저는 마이페이지, 차트 페이지 클릭시 로그인 페이지로 이동
- 게시물 읽기, 검색은 되나 영화 like, 게시글 등록, 게시글 좋아요, 게시글 댓글 기능 제한 



ㄹ.  메인 페이지

![home_AdobeExpress](README.assets/home_AdobeExpress.gif)

- `Best Rating` : 10000개의 데이터를 가중치를 통해 10개 선정
- `Popularity` : 



ㅁ. 영화 검색 페이지

<img src="README.assets/movie_search_AdobeExpress.gif" alt="movie_search_AdobeExpress" style="zoom:150%;" />

- 장르별 영화 50개씩 추천

- 코사인 유사도 기반 검색 영화와 비슷한 제목을 가진 10개 추천

  

ㅂ.  영화 상세 페이지

![movie_detail_AdobeExpress](README.assets/movie_detail_AdobeExpress.gif)

ㅅ. 영화 상세 페이지 커뮤니티, 삭제, 좋아요

<img src="README.assets/movie_community_AdobeExpress.gif" alt="movie_community_AdobeExpress" style="zoom:150%;" />

ㅇ. 유저기반 영화 추천 페이지

![like_chark_AdobeExpress](README.assets/like_chark_AdobeExpress.gif)



ㅈ. 유저 프로필 페이지

<img src="README.assets/user_AdobeExpress.gif" alt="user_AdobeExpress" style="zoom:150%;" />


