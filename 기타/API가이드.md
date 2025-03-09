# API 가이드

## 1. 데이터베이스 API
데이터베이스와 상호작용하는 API입니다.

| API | 설명 | 사용 예 |
|-----|------|--------|
| PostgreSQL API | PostgreSQL을 REST API로 접근 | 원격 DB 관리 |
| MySQL API | MySQL DB를 위한 API | SQL 쿼리 실행 |
| MongoDB Atlas API | MongoDB 클라우드 서비스 API | NoSQL 데이터 관리 |
| Firebase Firestore API | 구글의 NoSQL DB API | 실시간 데이터 저장 |

### 📌 PostgreSQL REST API 예제 (PostgREST 사용)
```http
GET http://localhost:3000/users
```
✅ PostgreSQL 데이터를 JSON 형태로 조회 가능

## 2. 클라우드 서비스 API
클라우드 기반의 데이터 저장, 컴퓨팅, 배포 등을 지원하는 API

| API | 설명 | 사용 예 |
|-----|------|--------|
| AWS API (S3, Lambda 등) | AWS의 다양한 서비스 API | 파일 업로드, 서버리스 실행 |
| Google Cloud API | 구글 클라우드 서비스 API | 머신러닝, 스토리지 |
| Azure API | MS Azure의 클라우드 API | 가상 머신, 데이터베이스 |

### 📌 AWS S3 파일 업로드 API (예제)
```http
PUT https://s3.amazonaws.com/bucket-name/file.txt
```
✅ S3에 파일을 업로드할 때 사용

## 3. 인증 및 보안 API
사용자 로그인 및 보안 강화를 위한 API

| API | 설명 | 사용 예 |
|-----|------|--------|
| OAuth 2.0 API | 토큰 기반 인증 API | 소셜 로그인, 인증 |
| JWT API | JSON Web Token 기반 인증 | 사용자 세션 관리 |
| Google OAuth API | 구글 로그인 API | 구글 계정 로그인 |
| Firebase Authentication API | 구글 Firebase 인증 | 이메일/소셜 로그인 |

### 📌 OAuth 2.0을 이용한 인증 요청 예제
```http
POST https://accounts.google.com/o/oauth2/token
```
✅ OAuth 인증을 통해 액세스 토큰을 발급받음

## 4. 결제 API
온라인 결제 및 금융 트랜잭션 API

| API | 설명 | 사용 예 |
|-----|------|--------|
| PayPal API | PayPal 온라인 결제 | 해외 결제 처리 |
| Stripe API | 카드 결제 API | 신용카드 결제 |
| Toss Payments API | 한국 카드 결제 API | 간편결제 지원 |
| Kakao Pay API | 카카오페이 결제 API | 카카오페이 결제 처리 |

### 📌 Stripe 결제 API 예제
```http
POST https://api.stripe.com/v1/charges
```
✅ 신용카드 결제 요청

## 5. 검색 & 데이터 분석 API
검색, 빅데이터 분석 API

| API | 설명 | 사용 예 |
|-----|------|--------|
| Elasticsearch API | 검색 엔진 API | 데이터 검색 및 분석 |
| Algolia API | 빠른 검색 API | 사이트 내 검색 구현 |
| Google Search API | 구글 검색 결과 API | 웹 크롤링 |
| BigQuery API | 빅데이터 분석 API | SQL 기반 데이터 분석 |

### 📌 Elasticsearch 검색 API 예제
```http
GET http://localhost:9200/products/_search?q=name:phone
```
✅ 제품 이름이 "phone"인 데이터를 검색

## 6. AI & 머신러닝 API
AI 기반의 서비스 API

| API | 설명 | 사용 예 |
|-----|------|--------|
| OpenAI API | ChatGPT 및 AI 모델 | 챗봇, 텍스트 생성 |
| Google Vision API | 이미지 분석 API | 얼굴 인식, OCR |
| IBM Watson API | 자연어 처리 API | 감정 분석, 번역 |
| Hugging Face API | 오픈소스 AI API | NLP 모델 호출 |

### 📌 OpenAI GPT API 예제
```http
POST https://api.openai.com/v1/chat/completions
```
✅ ChatGPT를 호출하여 텍스트 생성

## 7. 기타 API (지도, 번역, 메시징 등)

| API | 설명 | 사용 예 |
|-----|------|--------|
| Google Maps API | 지도 및 위치 검색 | 지도 표시, 경로 안내 |
| Kakao Maps API | 카카오 지도 API | 한국 지도 검색 |
| Google Translate API | 자동 번역 API | 언어 번역 |
| Twilio API | SMS & 전화 API | 문자 메시지 전송 |

### 📌 Google Maps API 예제 (위치 검색)
```http
GET https://maps.googleapis.com/maps/api/geocode/json?address=Seoul
```
✅ 서울의 위도/경도를 반환

## 📌 결론: API를 선택하는 방법

✅ 어떤 API를 선택해야 할까?
1️⃣ 데이터베이스 연동 → PostgreSQL, MySQL API
2️⃣ 클라우드 서비스 → AWS, Google Cloud API
3️⃣ 로그인 인증 → OAuth, Firebase Auth API
4️⃣ 결제 기능 추가 → PayPal, Stripe, Toss API
5️⃣ 검색 최적화 → Elasticsearch, Algolia API
6️⃣ AI 활용 → OpenAI GPT, Google Vision API
7️⃣ 지도, 번역, 메시징 → Google Maps, Twilio API

🚀 REST API를 활용하면 다양한 기능을 손쉽게 구현할 수 있으니, 필요에 따라 적절한 API를 선택하면 됩니다!