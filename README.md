# SKN16-3rd-3Team
 LLM을 연동한 내외부 문서 기반 질의 응답 시스템

**기간:** 2025.09.16 ~ 2025.09.17    
**팀원:** 강동기, 박태규, 신지윤, 안주영, 이현민

---

## 1. 프로젝트 개요

### 프로젝트 소개
>**교통사고 전문 챗봇 '챗문철'**   
RAG 기술을 활용하여 교통사고 발생 시 법률 상담을 제공하는 챗봇 서비스

   
### ✅ 프로젝트 배경

![변호사 수임료](https://github.com/user-attachments/assets/338b7417-3990-40d1-aa23-321ef8778bd6)
#### 높은 법률 자문 비용:   
* 변호사 선임 비용에 대한 경제적 부담으로 법률 서비스 이용의 어려움

#### 다양해지는 사고 유형 및 급증하는 위험:   
* 낮아지는 운전면허 취득 문턱, 초보 운전자 증가   
* 고령 운전자 및 어린이보호구역 사고 급증   
* 급발진 등 예측 불가능한 사고 발생

||2014|	2015	|2016|	2017|	2018|	2019|	2020|	2021|	2022	|2023|
| :---: | :---: |:---: | :---: |:---: | :---: |:---: | :---: |:---: | :---: |:---: |
|사고(건)|223,552	|232,035	|220,917|	216,335	|217,148	|229,600|	209,654	|203,130|	196,836|	198,296|



#### 법률 정보에 대한 낮은 접근성:   
* 교통사고 위험은 높아지지만, 정확한 법률 및 처리 절차에 대한 인지 부족

### ✅ 프로젝트 목표

#### 경제적 장벽 해소:
* 무료 상담을 통해 누구나 부담 없이 법률 서비스를 이용할 수 있는 환경 조성
  
#### 맞춤형 법률 정보 제공:   
* 다양한 사고 유형에 따른 맞춤형 대처 방안 제시
* 과실비율 계산 및 벌금·형사처벌 예측 기능을 통해 사건 결과를 사전에 가늠할 수 있도록 지원

#### 법률 정보의 대중화:   
* 24시간 언제 어디서든 이용 가능한 챗봇으로 법률 정보 접근성 극대화

#### 한문철 변호사 패르소나 적용
* 실제 교통사고 전문 변호사 한문철의 화법·논리 전개 방식을 모사한 AI 에이전트

---

## 2. 기술 스택

| 카테고리 | 기술 스택 |
| :--- | :--- |
| **사용 언어** | ![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) |
| **AI & LLM** | ![OpenAI](https://img.shields.io/badge/OpenAI-412991?logo=openai&logoColor=white) ![LangChain](https://img.shields.io/badge/LangChain-0092B9?logo=langchain&logoColor=white) |
| **벡터 데이터베이스** | ![ChromaDB](https://img.shields.io/badge/ChromaDB-5542D0) ![OpenAI Embeddings](https://img.shields.io/badge/OpenAI_Embeddings-412991?logo=openai&logoColor=white) |
| **웹 인터페이스** | ![Gradio](https://img.shields.io/badge/Gradio-FF7C00?logo=gradio&logoColor=white) |
| **데이터베이스** | ![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white) |
| **문서 처리** | ![PyPDF](https://img.shields.io/badge/PyPDF-FFD43B) ![python-docx](https://img.shields.io/badge/python--docx-3776AB) |
| **보안 & 인코딩** | ![bcrypt](https://img.shields.io/badge/bcrypt-00BFFF) ![chardet](https://img.shields.io/badge/chardet-FF4500) |
| **데이터 분석** | ![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white) ![openpyxl](https://img.shields.io/badge/openpyxl-1C6BA0) |
| **배포 & 관리** | ![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?logo=googlecolab&logoColor=white) ![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white) |

---

## 3. 프로젝트 구조

```text
ChatMoonCheol/
├── chatmooncheol_redesigned.py    # 🎯 메인 애플리케이션 (올인원 구조)
│   ├── DatabaseManager            # 🗄️ SQLite3 통합 데이터베이스 관리 (6개 테이블)
│   ├── OptimizedRAGSystem         # 🔍 문서 검색 및 임베딩 시스템
│   ├── ConversationAnalyzer       # 🧠 대화 분석 및 17개 항목 분석
│   └── ChatMoonCheolSystem        # ⚖️ 메인 로직 및 한문철 페르소나
│
├── .env                           # 🔐 OpenAI API 키
├── requirements.txt               # 📦 의존성 패키지
├── README.md                      # 📚 프로젝트 설명서
│
├── chatmooncheol_redesigned.db    # 🗃️ SQLite 데이터베이스 (66개 필드)
├── chroma_db_redesigned/          # 🔍 ChromaDB 벡터 저장소
│   ├── chroma.sqlite3             # 벡터 인덱스 파일
│   └── collections/               # 컬렉션 데이터
│
├── uploaded_docs/                 # 📄 업로드 문서 임시 저장소
│   ├── temp_*.pdf                 # PDF 파일들
│   ├── temp_*.txt                 # 텍스트 파일들
│   ├── temp_*.docx                # 워드 문서들
│   └── temp_*.md                  # 마크다운 파일들
│
├── assets/                        # 🖼️ UI 정적 파일
│   ├── my_avatar.png              # 한문철 아바타
│   ├── user_17301067.png          # 사용자 아바타
│   └── bot_avatar.jpg             # 봇 아바타
│
└── exports/                       # 📊 데이터 내보내기
    └── chatmooncheol_data_*.xlsx  # Excel 내보내기 파일

```
---

## 4. 시스템 아키텍처 및 처리 흐름

### ✅ 시스템 아키텍처
ChatMoonCheol은 RAG(Retrieval-Augmented Generation) 기반 구조로 설계됨
<img width="2654" height="3840" alt="system architecture" src="https://github.com/user-attachments/assets/54700883-d95c-43f3-8e7f-edd7cea6ed9f" />

### ✅ 시스템 플로우
📌 구성요소
1. **질문 입력**   
사용자가 자연어로 질문이나 요청을 입력

2. **UI 인터페이스**   
Gradio UI를 통해 입력을 시스템으로 전달

3. **입력 처리**   
사용자의 입력을 전처리하여 텍스트/이미지 등 유형에 따라 분류

4. **문서 검색 (RAG DB & Database)**   
RAG DB와 Database를 통해 의미 유사도가 높은 문서나 데이터를 검색

5. **AI 처리 (Image AI / AI 응답생성)**   
이미지 관련 요청은 Image AI에서 처리   
텍스트 관련 요청은 AI 응답생성 모듈에서 답변 초안 작성

6. **분석기**   
AI 응답과 데이터 검색 결과를 분석·보완하여 답변의 정확성과 품질을 향상

7. **최종 응답 생성**   
분석된 결과를 종합해 최종 응답을 생성

8. **사용자 응답 출력**   
사용자 화면에 구조화된 최종 답변을 전달

![systemflow](https://github.com/user-attachments/assets/071d904f-a884-4e82-b9b9-20459cb43572)

```text
graph TD
    A[사용자 입력] --> B[Gradio UI]
    B --> C{입력 분류}
    C -->|텍스트| D[RAG 검색]
    C -->|이미지| E[GPT-4o Vision]
    D --> F[GPT-4o 응답생성]
    E --> F
    F --> G[ConversationAnalyzer]
    G --> H[14개 항목 분석]
    H --> I[SQLite DB 저장]
    I --> J[사용자 응답]
```

> **전체 구조 요약:**   
사용자 입력 → 인터페이스(UI) → 메인 처리 → (AI/DB 활용) → 분석 → 응답 생성 → 사용자 응답

---

## 5. 핵심 기술 상세
**AI 모델 구성**
|용도|	모델|	Temperature|	Max Tokens|	특징|
| :---: | :---: | :---: | :---: | :---: |
|메인 대화|	GPT-4o|	0.2|	1,800	|한문철 페르소나, 법률 상담|
|대화 분석|	GPT-4o|	0.1|	1,500	|17개 항목 분석, JSON 형식|
|요약 생성|	GPT-4o|	0.2	|기본값	|마크다운 형식 요약|
|이미지 분석|	GPT-4o Vision|	-	|500	|사고 현장 이미지 분석|

👥 **챗문철 페르소나 특징**
* 어조: 정중하고 전문적이면서도 친근한 존댓말
* 전문분야: 도로교통법, 과실비율 판정, 음주운전, 교통사고 처리절차
* 응답 스타일: 법적 근거 명시 + 구체적 과실비율 제시

📊 **데이터베이스 스키마**   
SQLite3 테이블 구조 (6개 테이블)
|테이블명	|용도|	주요 필드|
| :---: | :---: | :---: |
|users|	사용자 관리|	username, password_hash, user_type(guest/expert/admin)|
|conversations|	대화 세션|	session_id(UUID), user_id, title, total_messages|
|messages|	메시지 저장|	role, content, image_data, timestamp|
|case_analysis|	사건 분석 결과|	14개 분석 항목 (아래 상세 표 참조)|
|documents|	업로드 문서|	filename, file_type, chunk_count, processing_time|
|document_chunks|	RAG용 청크|	document_id, chunk_text, chunk_index|

🔍 **14개 사건 분석 항목**
|분류|	항목|	설명	|데이터 타입|
| :---: | :---: | :---: | :---: |
|기본 정보	|case_type|	criminal/civil/consultation/mixed|	ENUM|
||accident_type	|사고 유형 상세 설명	|TEXT|
||severity_level	|minor/moderate/severe|ENUM|
|과실 및 역할|	fault_ratio|	과실비율 (예: "70:30")|	TEXT|
||party_role|	perpetrator/victim/witness/neutral|	ENUM|
|법률 정보|	legal_violations	|위반 교통법규 목록|	JSON|
||applicable_laws	|적용 법률 조항	|JSON|
||recommended_actions|	권장 조치사항	|JSON|
|처벌 예상|	fine_amount	|예상 벌금액|	INTEGER|
||imprisonment_period|	예상 징역기간|	TEXT|
||driver_license_points|	운전면허 벌점	|INTEGER|
|기타|	settlement_amount	|예상 합의금	|INTEGER|
||apology_needed	|반성문 필요 여부|	BOOLEAN|
||analysis_confidence	|분석 신뢰도 (0.0~1.0) |REAL|

**핵심 기술 구현**   
최적화된 RAG 시스템
|전략|	청크 크기|오버랩|	적용 조건|
| :---: | :---: | :---: | :---: |
|Small|	600자|	80자	|5,000자 미만 문서|
|Medium	|1,000자|	120자	|5,000~20,000자 문서|
|Large|	1,500자|	200자	|20,000자 이상 문서|

**ChromaDB 설정**
```python
vectorstore_config = {
    "persist_directory": "./chroma_db_redesigned",
    "hnsw_space": "cosine",
    "hnsw_construction_ef": 200,
    "hnsw_M": 16
}
```

🌐 **다국어 인코딩 지원**
* 지원 인코딩: UTF-8, CP949, EUC-KR, ASCII
* 자동 감지: chardet + 한국어 패턴 매칭
* 신뢰도 임계값: 0.7 이상
* 다단계 시도: 4가지 인코딩 순차 시도

⚡ **성능 최적화**
* 병렬 문서 처리: ThreadPoolExecutor 4 워커
* 스트리밍 파일 읽기: 메모리 효율성 (100MB 지원)
* 배치 벡터 저장: 50개 청크 단위 처리
* 중복 콘텐츠 필터링: 해시 기반 중복 제거

---

## 6. 데이터베이스 스키마
📊 **SQLite 데이터베이스 구조 (6개 테이블, 66개 필드)**
```sql
-- 👥 사용자 관리 테이블 (7개 필드)
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    user_type TEXT NOT NULL CHECK(user_type IN ('guest', 'expert', 'admin')),
    email TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    last_login DATETIME
);

-- 💬 대화 세션 테이블 (8개 필드)
CREATE TABLE IF NOT EXISTS conversations (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER,
    session_id TEXT UNIQUE NOT NULL,
    title TEXT DEFAULT '새 상담',
    started_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    ended_at DATETIME,
    total_messages INTEGER DEFAULT 0,
    case_summary TEXT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

-- 📝 메시지 저장 테이블 (7개 필드)
CREATE TABLE IF NOT EXISTS messages (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    conversation_id INTEGER,
    role TEXT NOT NULL CHECK(role IN ('user', 'assistant')),
    content TEXT NOT NULL,
    message_type TEXT DEFAULT 'normal',
    image_data TEXT,                          -- Base64 인코딩된 이미지
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (conversation_id) REFERENCES conversations(id)
);

-- 🔍 사건 분석 결과 테이블 (17개 필드) ⭐ 핵심 테이블
CREATE TABLE IF NOT EXISTS case_analysis (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    conversation_id INTEGER,
    case_type TEXT CHECK(case_type IN ('criminal', 'civil', 'consultation', 'mixed')),
    accident_type TEXT,
    fault_ratio TEXT,
    severity_level TEXT CHECK(severity_level IN ('minor', 'moderate', 'severe')),
    legal_violations TEXT,                    -- JSON: 위반 법규 리스트
    recommended_actions TEXT,                 -- JSON: 권장 조치사항
    party_role TEXT CHECK(party_role IN ('perpetrator', 'victim', 'witness', 'neutral')),
    settlement_amount INTEGER DEFAULT 0,      -- 예상 합의금
    apology_needed BOOLEAN DEFAULT FALSE,     -- 반성문 필요 여부
    applicable_laws TEXT,                     -- JSON: 적용 법률 조항
    fine_amount INTEGER DEFAULT 0,           -- 예상 벌금
    imprisonment_period TEXT,                 -- 예상 징역기간
    driver_license_points INTEGER DEFAULT 0, -- 운전면허 벌점
    analysis_confidence REAL DEFAULT 0.0,    -- 분석 신뢰도 (0.0~1.0)
    raw_analysis_json TEXT,                  -- 원본 GPT 분석 결과
    analyzed_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (conversation_id) REFERENCES conversations(id)
);

-- 📄 업로드 문서 관리 테이블 (14개 필드)
CREATE TABLE IF NOT EXISTS documents (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    filename TEXT NOT NULL,
    original_filename TEXT NOT NULL,
    file_type TEXT NOT NULL,
    file_size INTEGER,
    encoding TEXT,                           -- 파일 인코딩 (UTF-8, CP949 등)
    uploaded_by INTEGER,
    upload_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    processed BOOLEAN DEFAULT FALSE,         -- 처리 완료 여부
    chunk_count INTEGER DEFAULT 0,          -- 생성된 청크 수
    processing_status TEXT DEFAULT 'pending', -- pending/completed/failed
    error_message TEXT,                      -- 처리 오류 메시지
    processing_time REAL DEFAULT 0.0,       -- 처리 시간(초)
    file_hash TEXT,                          -- 파일 중복 검사용 해시
    FOREIGN KEY (uploaded_by) REFERENCES users(id)
);

-- 📚 RAG용 문서 청크 테이블 (6개 필드)
CREATE TABLE IF NOT EXISTS document_chunks (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    document_id INTEGER,
    chunk_index INTEGER,                     -- 청크 순서
    chunk_text TEXT,                         -- 실제 텍스트 내용
    chunk_size INTEGER,                      -- 청크 크기(문자수)
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (document_id) REFERENCES documents(id)
);
```

📈 **데이터베이스 통계**
* 총 테이블: 6개
* 총 필드: 66개
* 핵심 분석 항목: 17개 (case_analysis 테이블)
* 관계: 5개 외래키 관계
* 제약조건: 8개 CHECK 제약

---

## 7. 챗문철 화면 구성

### I. 시작 화면
<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/8a80746b-582b-4f03-ac5c-c0276f321b19" alt="로그인" width="350"/></td>
    <td><img src="https://github.com/user-attachments/assets/27367343-d2ac-47b0-8e86-f7ab2c8d6fa7" alt="회원가입" width="350"/></td>
  </tr>
  <tr>
    <td align="center">로그인</td>
    <td align="center">회원가입</td>
  </tr>
</table>

### II. AI 상담
<img width="1030" height="561" alt="AI 상담" src="https://github.com/user-attachments/assets/81966e95-bc86-4ddd-9395-328253b79a89" />

### III. 이미지 + 텍스트
<img width="1089" height="392" alt="이미지+텍스트" src="https://github.com/user-attachments/assets/83d2683f-f269-46c0-b0e1-8ffc8b818ee9" />
<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/20048b01-7712-456b-88d1-5f119dd8a448" alt="1" width="250"/></td>
    <td><img src="https://github.com/user-attachments/assets/a8cc7749-8f1d-4e35-ac0b-2d4e4b2d95c9" alt="2" width="250"/></td>
    <td><img src="https://github.com/user-attachments/assets/d9f8a868-21f4-4a79-9dfb-0982da7eabbf" alt="3" width="250"/></td>
    <td><img src="https://github.com/user-attachments/assets/8f5baedb-4c98-421f-9f7a-81e56341d182" alt="4" width="250"/></td>
  </tr>
</table>   

### IV. 대화 요약
<img width="705" height="563" alt="대화요약" src="https://github.com/user-attachments/assets/f2eca9a8-6156-4338-afcf-40dbe811593a" />

### V. 문서 관리
<img width="549" height="563" alt="문서관리" src="https://github.com/user-attachments/assets/1baf06ea-8885-4a24-abec-533a08435c88" />

### VI. 사용자 관리
<img width="1290" height="494" alt="사용자관리" src="https://github.com/user-attachments/assets/c7f6335d-19b4-49d0-870c-0a4fc132ba50" />

---


## 8. 검증 및 성능 평가

### ✅ PDF 텍스트 추출 성능 비교 (코사인 유사도)   
코사인 유사도 기반으로 PDF의 텍스트, 이미지, 표를 가장 높은 성능으로 추출하는 라이브러리 선정
<img src="https://github.com/user-attachments/assets/c124434c-2d0d-4d24-9fa9-9f1f1086670b" alt="추출 비교" width="900"/>  

#### I. TEXT  
| 추출 도구 | 이미지 | 텍스트 일치도 |
|----------|----------------------------------------------------------------------------------------------------------------------------------------|---------------|
| GPT-4o      | <img src="https://github.com/user-attachments/assets/27c273ab-aa2c-4717-b538-3b960c167550" alt="gpt" width="400"/>      | 1.0000             |
| PyMuPDF  | <img src="https://github.com/user-attachments/assets/1efe5ed6-ff0c-4941-be67-f25fc14809e6" alt="pymupdf" width="400"/>  | 1.0000             |
| Plumber  | <img src="https://github.com/user-attachments/assets/87270dd2-4ee5-440a-b16c-a828661242a5" alt="plumber" width="400"/>  | 0.9981             |
| PyPDF    | <img src="https://github.com/user-attachments/assets/59fbe580-5593-42e9-be88-6e8185b74370" alt="pypdf" width="400"/>    | 0.9235             |



#### II. IMAGE  
| 추출 도구 | 이미지 | 전체 일치도 | 텍스트 일치도 | 이미지·표 일치도 |
|-----------|--------|-------------|---------------|------------------|
| GPT-4o    | <img src="https://github.com/user-attachments/assets/b469d79d-1a6f-405b-95f3-048cf52da6b5" alt="gpt" width="200"/> | 0.9971 | 0.9979 | 0.9946 |
| PyMuPDF   | <img src="https://github.com/user-attachments/assets/18c3d932-64f1-4814-9a82-3d60a8a99697" alt="pymupdf" width="200"/> | 0.9681 | 0.9752 | 0.9488 |
| Plumber   | <img src="https://github.com/user-attachments/assets/7db047bf-3714-4051-b3d8-75742bb23328" alt="plumber" width="200"/> | 0.9678 | 0.9885 | 0.9103 |
| PyPDF     | <img src="https://github.com/user-attachments/assets/b9a14fa0-e68b-4ee8-84b3-0443c1fa44b9" alt="pypdf" width="200"/> | 0.8541 | 0.9112 | 0.7025 |



#### III. TABLE
| 추출 도구 | 이미지 | 전체 일치도 | 텍스트 일치도 | 이미지·표 일치도 |
|-----------|--------|-------------|---------------|------------------|
| GPT-4o    | <img src="https://github.com/user-attachments/assets/5a5e4d23-0036-4bcc-bf08-c7907a651c1c" alt="gpt" width="200"/> | 0.9913 | 0.9958 | 0.9889 |
| PyMuPDF   | <img src="https://github.com/user-attachments/assets/25ea509e-3d3d-409e-bbf9-7f3f5f2d5369" alt="pymupdf" width="200"/> | 0.8250 | 0.9754 | 0.7981 |
| Plumber   | <img src="https://github.com/user-attachments/assets/071d43f5-a9fb-465b-a9fe-ee8300ebd5c5" alt="plumber" width="200"/> | 0.8116 | 0.9712 | 0.7833 |
| PyPDF     | <img src="https://github.com/user-attachments/assets/eebceb55-83f7-41e2-9f95-c5c2c3103ac9" alt="pypdf" width="200"/> | 0.7301 | 0.8995 | 0.6923 |


### ⭐ 최종 선정
| 추출 도구              | 전체 일치도 | 텍스트 일치도 | 이미지·표 일치도 |
|:-----------------------|:--------------------------:|:----------------------------:|:-------------------------------:|
| **ChatGPT (GPT-4o)**   |          **0.9971**        |          **0.9979**          |           **0.9946**            |
| PyMuPDF                |           0.9681           |           0.9752             |            0.9488               |
| Plumber                |           0.9678           |           0.9885             |            0.9103               |
| PyPDF                  |           0.8541           |           0.9112             |            0.7025               |


### ✅ 과실비율 예측 검증

| 구분        | 평균 근접도(%) | 과실비율 응답률(%) |법률 정확도|
|:-----------|:--------------:|:-----------------:|:-----------------:|
| No_RAG     |       94.44       |        90         |낮음|
| 법무법인 OO|       90       |        60         |높음|
| **ChatMoonCheol (RAG + 텍스트)** | **97** | **100** |**높음**|

- **평균 근접도**: 실제 과실비율과 예측값의 평균 오차율 기반  
- **과실비율 응답률**: 과실비율을 응답한 비율
- **개선 효과**:  
  - No_RAG 대비 **2.56%p** 향상 (평균 근접도)
  - 법무법인 OO 대비 **7%p** 향상 (평균 근접도)
  - 법무법인 OO 대비 **40%p** 향상 (응답률)

<img width="2400" height="1350" alt="image" src="https://github.com/user-attachments/assets/631c5b74-8db9-4a7b-8815-b9fe1188ab57" />
<img width="2400" height="1350" alt="image" src="https://github.com/user-attachments/assets/96fecbe5-2a40-4baa-bc9b-346e842dde95" />
<img width="2400" height="1350" alt="image" src="https://github.com/user-attachments/assets/30699da8-97f7-44dd-ae18-0bc9d4a279e9" />

### ✅ 검증 방법론 비교분석
* 평가 기준: 실제 과실비율과 예측값의 오차율 기반 근접도 측정
* 테스트 케이스: 10건의 실제 교통사고 사례
* 비교 대상: No_RAG vs 법무법인 텍스트 상담 vs 챗문철(RAG)
 
<img width="2323" height="1206" alt="image" src="https://github.com/user-attachments/assets/318cc4f2-60c5-43e8-b480-186ce8e2fd26" />

---


## 9. 주요 기능 및 차별점
🎭 **한문철 변호사 페르소나**
* 화법 특징: 직설적이고 실무적인 조언
* 전문성: 교통사고 판례 및 법규 기반 답변
* 사용자 맞춤: 가해자/피해자 입장별 차별화된 조언

🔍 **지능형 사건 분석**
* 자동 분류: 형사/민사/상담/복합 사건 구분
* 과실비율 산정: 사고 상황 기반 과실비율 예측
* 처벌 수위 예상: 벌금액, 면허점수, 구형량 추정
* 신뢰도 점수: 분석 결과의 확실성 수치화

📊 **관리자 대시보드**
* 상담 통계: 일별/월별 상담 현황
* 사건 분석: 사고 유형별 통계
* 문서 관리: 업로드된 법령/판례 현황
* Excel 내보내기: 상담 데이터 분석용 엑셀 파일 생성

🖼️ **멀티모달 분석**
* 사고 현장 분석: 사진을 통한 상황 파악
* 손상 정도 평가: 차량 파손 수준 분석
* 증거 자료 검토: 블랙박스, CCTV 영상 분석

🏆 **핵심 차별점**
* 업계 최고 과실비율 예측 정확도: 97% 근접도 달성
* 완전한 사건 분석: 17개 항목 자동 추출 및 분석
* 멀티모달 지원: 텍스트 + 이미지 종합 분석
* 실서비스 수준: 66개 필드 완전 DB 설계

🎨 **사용자 인터페이스**
Gradio 웹 인터페이스 특징
* 모던 디자인: 필렛 아이콘 기반 미니멀 UI
* 반응형 웹: 모바일/태블릿 최적화
* 아바타 이미지: GPT 스타일 채팅 인터페이스
* 3권한 시스템: Guest/Expert/Admin 차별화

**주요 기능별 탭**
* 💬 AI 상담: 실시간 채팅 + 이미지 첨부
* 📋 대화 요약: 14개 항목 분석 + 마크다운 요약
* 📚 문서 관리: RAG용 문서 업로드 (관리자)
* 👥 사용자 관리: 대화 통계 + Excel 내보내기 (관리자)

🔐 **보안 및 안전성**  
* 비밀번호 보안: bcrypt 해싱 (salt 포함)
* 세션 관리: UUID 기반 고유 세션
* SQL 인젝션 방지: 파라미터 바인딩
* 파일 검증: SHA256 해시 기반 중복 확인

**에러 핸들링**
* JSON 파싱 복구: 정규식 백업 파싱
* 인코딩 실패 대응: 다단계 인코딩 시도
* API 호출 실패: 기본 응답으로 서비스 연속성 보장
* 파일 처리 오류: 개별 파일 격리 처리

---


## 10. 코드 하이라이트
🔄  **적응형 텍스트 분할기**
```python
def choose_optimal_splitter(self, content_length: int) -> RecursiveCharacterTextSplitter:
    if content_length < 5000:
        return self.text_splitters['small']
    elif content_length < 20000:
        return self.text_splitters['medium']
    else:
        return self.text_splitters['large']
```

🌐 **고급 인코딩 감지**
```python
def advanced_encoding_detection(self, filepath: str) -> Tuple[str, float]:
    # 한국어 패턴 매칭을 통한 정확한 인코딩 감지
    korean_patterns = {
        b'\xed\x95\x9c': 'UTF-8',    # '한'
        b'\xc7\xd1': 'EUC-KR',       # '한'
    }
    # ... 구현 세부사항
```

🤖 **컨텍스트 기반 응답 생성**
```python
response = self.client.chat.completions.create(
    model="gpt-4o",
    messages=messages,
    temperature=0.2,
    max_tokens=1800,
)
```

---


## 11. 프로젝트 성과 및 차별점

✅ **비교 우위**
|기존 서비스|	챗문철|
| :---: | :---: |
|일반적인 법률 정보|	교통사고 전문화|
|단순 Q&A|	17개 항목 종합 분석|
|자세한 상담 지원X|A-Z 관리|
|텍스트만 지원|	멀티모달 (텍스트+이미지)|
|과실비율 90% 정확도|	과실비율 97% 정확도|
|응답률 60%|응답률 100%|
|일반 챗봇	|한문철 페르소나|

---


## 12. 확장성
✅ **단기**
* 모바일 최적화: React Native 기반 앱 개발
* 음성 인터페이스: STT/TTS 기능 추가
* 실시간 알림: 판례 업데이트 자동 알림
* 다국어 지원: 영어/중국어 서비스 확장
* API 서비스: REST API 공개
  
✅ **중장기**
* 보험사 연동: 보험금 산정 자동화
* 변호사 매칭: 실제 변호사 연결 서비스
* 판례 DB 확장: 대법원 판례 자동 수집
* AI 모델 고도화: 자체 법률 특화 모델 개발
 
---

## 13. 고찰
**팀 고찰**

이 프로젝트에서 가장 중요한 기술적 의사결정은 한문철 변호사 페르소나를 어떻게 구현할 것인가였다. 단순한 법률 정보 제공 챗봇이 아닌, 실제 변호사의 화법과 논리 전개 방식을 모사하는 것이 핵심이었다. 이를 위해 temperature 0.2로 낮춰 일관성을 확보하면서도, system prompt에서 "직설적이고 실무적인 조언", "과실비율 명시" 등 구체적인 행동 패턴을 정의했다.

PDF 전처리 파이프라인의 최적화 과정에서 가장 큰 기술적 도전이 있었다. 초기에는 단순한 PyPDF2를 사용했으나, 법률 문서의 복잡한 레이아웃(표, 각주, 다단 구성)에서 텍스트 추출 품질이 떨어졌다. 이를 해결하기 위해 4가지 PDF 추출 라이브러리(PyMuPDF, Plumber, PyPDF, GPT-4o Vision)를 비교 검증했고, 코사인 유사도 기준으로 GPT-4o Vision이 99.71%의 최고 성능을 보였다. 특히 표와 이미지가 포함된 문서에서 94.46%의 정확도를 달성한 것이 결정적이었다.

적응형 청킹 전략을 구현한 이유는 문서 길이에 따른 성능 차이를 발견했기 때문이다. 5,000자 미만 문서는 600자 청크로, 20,000자 이상 문서는 1,500자 청크로 처리하여 검색 정확도와 처리 속도를 모두 향상시켰다. 이는 단순한 하이퍼파라미터 튜닝이 아닌, 문서 특성에 맞는 전략적 접근이었다.

멀티모달 처리에서는 GPT-4o Vision을 활용한 사고 현장 이미지 분석이 핵심이었다. 단순히 이미지를 설명하는 것이 아니라, 차량 손상 정도, 사고 각도, 신호등 상태 등을 종합하여 과실비율 산정에 활용할 수 있도록 구조화된 정보를 추출하도록 설계했다.

데이터베이스 설계에서는 확장성을 고려한 정규화된 스키마를 구축했다. 특히 case_analysis 테이블의 17개 분석 항목은 실제 법률 상담에서 필요한 모든 요소를 추상화한 결과다. JSON 필드를 활용하여 복잡한 법률 정보(위반 법규, 적용 조항)를 구조화하면서도 SQLite의 단순함을 유지했다.

성능 최적화에서는 ThreadPoolExecutor 4 워커를 활용한 병렬 문서 처리, 배치 벡터 저장(50개 청크 단위), SHA256 기반 중복 파일 검사 등을 구현했다. 특히 ChromaDB의 HNSW 인덱스 파라미터(ef=200, M=16)를 튜닝하여 검색 속도와 정확도의 균형점을 찾았다.

에러 핸들링에서는 프로덕션 환경을 고려한 robust한 시스템을 구축했다. JSON 파싱 실패시 정규식 백업 파싱, 인코딩 감지 실패시 4단계 fallback 전략, API 호출 실패시 기본 응답 제공 등을 통해 서비스 연속성을 보장했다.

가장 뿌듯한 성과는 과실비율 예측 정확도 97% 달성이다. 이는 기존 No_RAG 시스템(94.44%) 대비 2.56%p, 법무법인 텍스트 상담(90%) 대비 7%p 향상된 수치다. 더 중요한 것은 응답률 100%를 달성한 것으로, 법무법인의 60% 응답률과 비교할 때 실질적인 사용자 경험 개선을 이뤄냈다.

**개인 고찰**

|이름|고찰|
|안주영|팀장으로서 가장 중요했던 의사결정은 한문철 페르소나 구현 전략이었다. 법률, 기준, 사례와 같은 무거운 PDF를 GPT5를 통해 가볍고 정확도 높은 txt 파일로 전처리 했다. Temperature 설정과 구체적 행동 패턴 정의를 통해 일관된 전문성을 확보했다. 결과적으로 검증을 통해 과실비율 예측 97% 정확도와 100% 응답률을 달성하여 기존 서비스 대비 실질적 성능 향상을 이뤄내서 정말 기뻤다. 파인튜닝을 하긴 했지만 구조적으로 루핑을 통해 파인튜닝을 하지 않아 추후에는 이런 부분들을 실현시키고 싶다.|


