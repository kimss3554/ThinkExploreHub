# 홈페이지 콘텐츠 선별 폴더

> 생각탐구 홈페이지 Phase 3 자료 조사용 임시 폴더
> Git 저장소가 아님 (임시 작업용)

---

## 폴더 구조

```
07_Website_Content_Staging/
├─ 00_Brand/           ← 로고, 원장 사진 등 브랜드 자산
├─ 01_Books/           ← 출간 도서 표지 이미지
├─ 02_Elementary/      ← 초등 글쓰기, 질문노트, 활동 등
├─ 03_Middle/          ← 중등 탐구, PPT, 포스터, 발표 등
├─ 04_Reviews/         ← 학부모·학생 후기
├─ 05_Results/         ← 대회 수상, 영재원, 진학 소식
├─ 06_Director/        ← 원장 소개 이미지·자료
└─ 07_External_Links/  ← 외부 링크 정보 (관악구 학군분석 등)
```

---

## 첫 배치 범위 (1차)

**목표**: 12~15개로 제한

### 필수 포함
```
초등 성장 세트: 5개
중등 탐구 세트: 4개
브랜드·도서·원장: 4~6개
```

### 2차 배치로 미루기
```
후기 (3~5개)
수상·진학 소식 (2~3개)
외부 링크 (1개)
```

**왜 처음부터 모두 하지 않나?**

초등과 중등의 **과정 연결성**이 첫 와이어프레임을 결정합니다.
후기와 결과물은 초등·중등 사례가 확정된 후 추가해도 늦지 않습니다.

---

## 자료 배치 원칙

### ✅ 배치 가능 자료

- 이미지 (PNG, JPG, JPEG, WebP, SVG)
- 영상 (MP4, WebM)
- 문서 (PDF, PPTX, DOCX)
- 텍스트 메모 (TXT, MD)
- 외부 링크 정보

### ❌ 배치 금지 자료

**다음 자료는 이 폴더에 절대 넣지 마세요**:

```text
❌ 학교생활기록부 (PDF, 사진, 캡처)
❌ 성적표
❌ 학번이 표시된 자료
❌ 학교 제출 자료 원본
❌ 현재 고등학생 수행평가 결과물
❌ 현재 고등학생 탐구보고서 원본
❌ 자기평가서 원본
❌ 학생 이름과 학교명이 함께 표시된 자료
❌ 전화번호, 카카오톡 프로필이 포함된 자료
```

---

## 파일명 규칙

**학생 이름과 학교명을 파일명에 사용하지 않습니다**.

### 권장 파일명 예

#### 브랜드 / 도서
```
BRAND-LOGO-01.png
BRAND-LOGO-02.svg
BOOK-COVER-01.jpg
BOOK-COVER-02.jpg
DIRECTOR-PROFILE-01.jpg
DIRECTOR-PROFILE-02.jpg
```

#### 초등
```
ELEM-WRITING-BEFORE-01.jpg
ELEM-WRITING-AFTER-01.jpg
ELEM-WRITING-BEFORE-02.jpg
ELEM-WRITING-AFTER-02.jpg
ELEM-MINDMAP-01.jpg
ELEM-MINDMAP-02.jpg
ELEM-ACTIVITY-01.jpg
ELEM-ACTIVITY-02.jpg
ELEM-PRESENTATION-01.jpg
ELEM-REVIEW-PARENT-01.txt
```

#### 중등
```
MIDDLE-INQUIRY-PLAN-01.jpg
MIDDLE-RESEARCH-01.jpg
MIDDLE-WRITING-01.jpg
MIDDLE-PPT-01.jpg
MIDDLE-POSTER-01.jpg
MIDDLE-PRESENTATION-01.jpg
MIDDLE-PROJECT-01.jpg
MIDDLE-REVIEW-PARENT-01.txt
MIDDLE-REVIEW-STUDENT-01.txt
```

#### 성과
```
RESULT-AWARD-01.txt
RESULT-GIFTED-01.txt
RESULT-ADMISSION-01.txt
```

---

## 각 폴더 상세 설명

### 00_Brand/
- 생각탐구 로고 (PNG, SVG)
- 원장 프로필 사진
- 브랜드 컬러 팔레트 (선택)
- 기타 브랜드 요소

**목표**: 로고 1~2개, 원장 사진 1~2개

### 01_Books/
- 출간 도서 표지 이미지 (JPG, PNG)
- 도서 소개 텍스트 (TXT)

**목표**: 도서 표지 1~2개

### 02_Elementary/
- 처음 쓴 글 (전, 스캔 또는 사진)
- 수정된 글
- 완성 글
- 질문 노트 (사진 또는 스캔)
- 마인드맵 (이미지)
- 독서활동 사례
- 탐구활동 사례
- 발표 자료 또는 사진
- 학부모 후기 (별도 04_Reviews 폴더)

**목표**: 사례 5~8개

### 03_Middle/
- 탐구 질문 또는 계획
- 자료 조사 과정 (사진 또는 스캔)
- 출처 확인 기록
- 구조 글쓰기 사례
- PPT (파일 또는 스크린샷)
- 포스터 (이미지)
- 발표 자료 또는 사진
- 대회 프로젝트
- 학부모·학생 후기 (별도 04_Reviews 폴더)

**목표**: 사례 8~10개

### 04_Reviews/
- 학부모 후기 (학생명 및 학교명 제거)
- 학생 후기 (이름 제거)
- 졸업생 후기

**형식**:
- TXT (텍스트)
- 사진 (개인정보 제거됨)

**목표**: 후기 3~5개

### 05_Results/
- 대회 수상 소식 (텍스트)
- 영재원 합격 소식 (텍스트)
- 특목·자사고 진학 소식 (텍스트)
- 대학 진학 소식 (텍스트)

**기록 방식**:
```
학생 이름 ❌
학교명 ❌
학년 ✅ (선택)
지역 ✅ (선택)
수상·합격·진학 사실만 ✅
```

**목표**: 소식 2~3개

### 06_Director/
- 원장 소개 이미지
- 원장 약력 (TXT)
- 저서 정보

### 07_External_Links/
- 관악구 학군분석 배포 URL
- 교재·콘텐츠 판매 서비스 URL
- 기타 외부 링크 정보

**형식**: TXT 또는 MD

---

## 자료 배치 후 진행

자료 배치 완료 시 다음과 같이 알려주세요:

```
"자료 배치 완료"
```

그러면 Claude Code가 다음을 수행합니다:

1. 폴더별 파일 목록화
2. 각 자료의 공개 가능 상태 분류
3. 대표 콘텐츠 후보 선별
4. 부족한 자료 확인
5. ASSET_INVENTORY.md 작성
6. CONTENT_GAPS.md 작성
7. CONTENT_SHORTLIST.md 작성

---

## 주의사항

### 금지 사항
- ❌ 학생부 파일을 이 폴더에 넣기
- ❌ 성적표 넣기
- ❌ 현재 고등학생 과제 원본 넣기
- ❌ 개인정보 포함 자료 그대로 넣기

### 필수 확인
- ✅ 학생·학부모 공개 동의 확인
- ✅ 학교명·학생명 제거
- ✅ 파일명 익명화
- ✅ 개인 식별정보 제거

---

## 이 폴더에 대해

- **Git 저장소**: ❌ 아님
- **PROJECT_REGISTRY에 등록**: ❌ 아님
- **용도**: 임시 자료 선별 및 조사용
- **최종 위치**: 홈페이지 저장소로 이동 (필요시)

---

*마지막 수정: 2026-07-19*
