# Meetory

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)
![SpringBoot](https://img.shields.io/badge/API-SpringBoot-6DB33F?logo=springboot&logoColor=white)
![MySQL](https://img.shields.io/badge/Database-MySQL-4479A1?logo=mysql&logoColor=white)

> **Meetory (Meetup + Story)**  
> 관심사가 같은 사람들과 모임을 만들고 참여하며 새로운 이야기를 만들어가는 커뮤니티 플랫폼입니다.

React + Vite 기반으로 개발된 Frontend 프로젝트이며 Spring Boot Backend와 REST API를 통해 통신합니다.

---

# 📌 목차

- 프로젝트 소개
- 기술 스택
- 주요 기능
- 프로젝트 구조
- 실행 방법
- API 연동
- 인증 방식
- 팀원 소개
- 향후 개발 계획

---

# 프로젝트 소개

Meetory는 관심사가 같은 사람들을 연결해주는 모임 플랫폼입니다.

사용자는

- 회원가입
- 로그인
- 온보딩
- 모임 생성
- 모임 참여
- 게시판 이용
- 모임 관리
- 마이페이지
- 쪽지 기능

등을 사용할 수 있습니다.

---

# Tech Stack

| 구분 | 스택 |
|---|---|
| Frontend | React 19, Vite 8, JavaScript(ES6+), Context API, Fetch API, CSS3, lucide-react |
| Backend | Java 21, Spring Boot 4, Spring Security, Spring Data JPA, MySQL, JWT(jjwt) |
| 공통 | REST API, JWT 인증, Git/GitHub |

---

## 전체 아키텍처

```
┌───────────────────────┐        HTTPS / JSON        ┌───────────────────────────┐
│   meetory-frontend     │ ─────────────────────────▶ │      meetory-backend       │
│   React 19 + Vite      │   Authorization: Bearer     │  Spring Boot 4 + Security  │
│   (localhost:5173)     │ ◀───────────────────────── │      (localhost:8080)      │
└───────────────────────┘        ApiResponse<T>        └─────────────┬─────────────┘
                                                                       │ JPA / Hibernate
                                                                       ▼
                                                               ┌───────────────┐
                                                               │    MySQL 8     │
                                                               └───────────────┘
```

- 개발 환경에서는 Vite의 `/api` 프록시 설정으로 프론트(5173) → 백엔드(8080) 요청이 그대로 전달되어, 백엔드에 별도 CORS 설정 없이도 로컬 연동이 가능합니다. (배포/외부 접근 환경을 위해 백엔드에도 CORS 설정이 포함되어 있습니다.)
- 모든 API 응답은 백엔드 공통 규격인 `ApiResponse<T> = { success, message, data }` 형태로 통일되어 있습니다.
- 인증이 필요한 요청은 `Authorization: Bearer {accessToken}` 헤더로 전달됩니다.

---

# 주요 기능 및 화면

## 🔐 로그인 / 회원가입

- 회원가입
- 로그인
- JWT 인증
- 자동 로그인
- 로그아웃

---

## 👤 온보딩

최초 로그인 이후

- 나이 입력
- 성별 선택
- 관심사 선택

사용자 정보를 입력할 수 있습니다.

---

## 👥 모임 모집

- 모임 목록 조회
- 카테고리 필터
- 모임 생성
- 모임 상세 조회
- 팀원 조회
- 모집 인원 Gauge
- 모임 신청

<p align="center">
<img src="https://github.com/user-attachments/assets/227d55fe-1091-4c92-baf5-e8bda15188fa" width="100%">
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/57aa874c-e25e-4220-87d1-797dacef748b" width="49%">
<img src="https://github.com/user-attachments/assets/ae4cda00-0f34-419f-80c9-69307b8e7496" width="49%">
</p>

---

## ⚙️ 모임 관리

리더 전용 기능

- 신청자 조회
- 신청 승인
- 신청 거절
- 현재 팀원 조회
- 팀 관리 페이지

<p align="center">
<img src="https://github.com/user-attachments/assets/db98d4dd-e169-4d79-a251-01772789781c" width="49%">
<img src="https://github.com/user-attachments/assets/164236c2-134d-4bf0-8be4-9f5bb6b7771e" width="49%">
</p>

---

## 📝 게시판

- 게시글 목록
- 게시글 작성
- 게시글 상세 조회

(Backend API 연동 진행 중)

---

## 💬 마이페이지 / 쪽지

- 내 정보 조회
- 로그아웃
- 읽은 쪽지
- 안 읽은 쪽지
- 쪽지 송수신

<p align="center">
<img src="https://github.com/user-attachments/assets/24cceae5-727b-460e-9f2e-bf3dcbadc98d" width="49%">
<img src="https://github.com/user-attachments/assets/abe46b35-f215-4e0a-ae3b-245b7cfdaabc" width="49%">
</p>

---

# 프로젝트 특징

- React Context 기반 인증 관리
- JWT 인증 방식
- Fetch API Wrapper
- 공통 Modal 컴포넌트
- Toast 알림
- Gauge UI
- 반응형 레이아웃
- Hero Banner
- User Menu
- 재사용 가능한 컴포넌트 구조

---

# 👥 팀원

| 이름 | 담당 |
|------|------|
| **이수현** | 로그인 / 회원가입 / 온보딩 / 마이페이지(개인정보) BE & FE |
| **정문구** | 게시판 BE & FE |
| **조성원** | 메인 화면 / 모임 모집 / 모임 관리 / 마이페이지(쪽지함) BE & FE |

---

# 향후 개발 계획

- 게시판 CRUD 고도화
- 댓글 기능
- 검색 기능
- 이미지 업로드
- Refresh Token
- Access Token 자동 재발급
- 실시간 알림
- 무한 스크롤
- 프로필 수정
- 모임 추천 기능

---

# 개발 환경

| 항목 | 버전 |
|------|------|
| Node.js | 20+ |
| npm | 10+ |
| React | 19 |
| Vite | 8 |
| Backend | Spring Boot |
| Database | MySQL |

--- 

더 자세한 내용은 각 파트의 README를 확인해 주세요.

- 📱 [Frontend README](https://github.com/URECA-Meetory/Meetory_FE/blob/main/README.md)
- ⚙️ [Backend README](https://github.com/URECA-Meetory/Meetory_BE/blob/main/README.md)

