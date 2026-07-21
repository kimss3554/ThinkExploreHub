# ThinkExploreHub — Claude Code 하네스

**목표**: Obsidian Vault + 개발 프로젝트를 통합하여 **홈페이지 제작 · 논문 작성 · 학생 탐구보고서 · 교재 제작** 파이프라인 운영

---

## 🏗️ 아키텍처 (하이브리드 저장소)

| 계층 | 경로 | 저장소 | 동기화 |
|------|------|--------|--------|
| **Obsidian Vault** | `01_ObsidianVault/` | Google Drive | ☁️ 자동 동기화 |
| **개발 프로젝트** | `03_Projects/` | 로컬 + GitHub | 💻 로컬 전용 |
| **참고 자료** | Zotero 앱 내부 | %APPDATA%\Zotero\ | Obsidian 연동 |

---

## 📁 저장소 구조

### **Google Drive** (클라우드)
```
G:\내 드라이브\
└── ThinkExploreHub/
    └── 01_ObsidianVault/          ☁️ Obsidian Vault 루트
        ├── 00_대시보드/
        ├── 10_논문/
        ├── 20_학생탐구보고서/
        ├── 30_교재/
        ├── 40_생각탐구site/       (웹사이트 기획·콘텐츠)
        ├── 50_수업자료/
        ├── 60_브랜드마케팅/
        ├── 99_AI_context/
        ├── wiki/                  (참고 자료 라이브러리)
        └── .obsidian/             (Obsidian 설정)
```

### **로컬** (개발 전용)
```
C:\Users\Kim\ThinkExploreHub/
├── 03_Projects/                   💻 개발 프로젝트 (로컬 + GitHub)
│   ├── thinkexplore-site/         🌐 홈페이지 (React/Next.js)
│   ├── thesis-gels2022/           📖 논문 데이터·분석
│   └── [기타 템플릿·프로젝트]
│
├── 00_Inbox/                      자료 수집함
├── 20_ThinkExplore/               기존 자료 (정리 중)
├── 99_Backup/                     로컬 백업
├── CLAUDE.md                      이 파일
└── .claude/                       Claude Code 설정
```

---

## 🎯 작업 영역 정의

### 1️⃣ **홈페이지 제작** (생각탐구 웹사이트)

**Obsidian**: `01_ObsidianVault/40_생각탐구site/`
- 페이지 구조, 콘텐츠, 섹션 기획

**개발 프로젝트**:
- `thinkexplore-site/` ← **주 프로젝트**
- `next-forge/`, `nextjs/` ← 참고용 템플릿
- `react-and-nextjs-data-visualization/` ← 차트·그래프 통합

**워크플로우**:
1. Obsidian에서 페이지 기획·작성
2. Claude Code에서 React/Next.js 구현
3. 개발 서버(`npm run dev`)로 실시간 확인
4. 배포

---

### 2️⃣ **논문 작성** (GELS 9차 데이터)

**Obsidian**: `01_ObsidianVault/10_논문/`
- 논문초안, 문헌노트, 분석결과, 이론적배경

**외부 자료**:
- `02_Zotero/` ← 참고문헌 관리
- `thesis-gels2022/` ← 데이터·분석 코드

**워크플로우**:
1. Obsidian에서 논문 구조 작성
2. 문헌 정리 (Zotero 연동)
3. Python 분석 코드 실행 (thesis-gels2022)
4. 결과를 Obsidian에 정리·시각화

---

### 3️⃣ **학생 탐구보고서**

**Obsidian**: `01_ObsidianVault/20_학생탐구보고서/`
- 템플릿, 학생별 탐구 주제

**개발 프로젝트**:
- `student-report-template/` ← 웹 기반 탐구보고서 생성기

**워크플로우**:
1. Obsidian에서 탐구 주제·평가 기준 정의
2. 학생이 웹 템플릿에서 작성
3. 결과를 Obsidian에 정리

---

### 4️⃣ **교재 제작** (수업 자료)

**Obsidian**: `01_ObsidianVault/30_교재/`
- 장별 콘텐츠, 학습 목표, 평가 문항

**개발 프로젝트**:
- `textbook-template/` ← 인터랙티브 교재 생성기

**워크플로우**:
1. Obsidian에서 교재 구성 기획
2. Claude Code에서 웹 버전 생성
3. 학생 피드백 수집 후 개선

---

## 🔧 Claude Code 통합

### **Obsidian 열기** (Google Drive 버전)
```
1. Obsidian 앱 실행
2. 좌하단 폴더 아이콘 클릭 → '다른 Vault 열기'
3. G:\내 드라이브\ThinkExploreHub\01_ObsidianVault 선택
4. 완료! (모든 기기에서 자동 동기화)
```

### **개발 서버 실행**
```bash
cd C:\Users\Kim\ThinkExploreHub\03_Projects\thinkexplore-site
npm run dev
# http://localhost:3000에서 확인
```

### **작업 흐름**
1. **Obsidian에서 계획** → 마크다운으로 기획서 작성
2. **Claude Code에서 구현** → 마크다운 링크 참고하며 코드 작성
3. **브라우저에서 확인** → 개발 서버로 실시간 미리보기
4. **Obsidian에서 정리** → 작업 결과·학습 내용 기록

---

## 🎨 프로젝트 템플릿

### **새 홈페이지 기능 추가**
1. `01_ObsidianVault/40_생각탐구site/` 에 마크다운 페이지 추가
2. `03_Projects/thinkexplore-site/` 에서 React 컴포넌트 구현
3. 로컬 개발 서버 확인 후 커밋

### **새 논문 챕터 작성**
1. `01_ObsidianVault/10_논문/논문초안/` 에 마크다운 작성
2. Zotero 링크로 참고문헌 연결
3. `thesis-gels2022/` 에서 분석 실행 후 결과 임베드

### **새 탐구보고서 템플릿**
1. `01_ObsidianVault/20_학생탐구보고서/` 에 기본 구조 정의
2. `03_Projects/student-report-template/` 에서 웹 폼 구현
3. 학생 입력 시 자동으로 보고서 생성

---

## 📋 작업기준 (체크리스트)

### **홈페이지**
- [ ] 기획서 작성 (`40_생각탐구site/site_작업기준.md`)
- [ ] 마크다운 페이지 작성
- [ ] React 컴포넌트 구현
- [ ] 스타일링 (Tailwind CSS / Styled Components)
- [ ] 로컬 테스트
- [ ] 배포

### **논문**
- [ ] 개요 작성 (`10_논문/논문_작업기준.md`)
- [ ] 선행연구 정리
- [ ] 데이터 분석
- [ ] 챕터별 초안 작성
- [ ] 피드백 반영
- [ ] 최종 검수

### **탐구보고서**
- [ ] 템플릿 정의 (`20_학생탐구보고서/학생탐구보고서_기본템플릿.md`)
- [ ] 학생별 주제 배정
- [ ] 웹 폼 구현
- [ ] 자동 생성 로직
- [ ] 평가·피드백

### **교재**
- [ ] 목차 기획 (`30_교재/목차.md`)
- [ ] 장별 콘텐츠 작성
- [ ] 학습 목표·평가 기준 정의
- [ ] 인터랙티브 요소 추가
- [ ] 학생 테스트

---

## ☁️ 동기화 및 협업

### **Google Drive 자동 동기화**
- Obsidian Vault: G:\내 드라이브\ThinkExploreHub\01_ObsidianVault
- 모든 기기에서 실시간 동기화 (PC, 태블릿, 휴대폰 등)
- 필요한 자료만 Google Drive에 업로드 (대용량 프로젝트는 제외)

### **Zotero 연동**
- 논문 작성 시 Obsidian에서 Zotero 자동 임베드
- 참고문헌 자동 생성
- Obsidian 플러그인 사용 (Zotero Citation 등)

### **GitHub 백업** (개발 프로젝트)
- 03_Projects는 로컬에서 Git 관리
- 정기적으로 GitHub으로 푸시 (버전 관리 및 백업)

---

## 📝 변경 이력

| 날짜 | 변경 내용 | 대상 | 사유 |
|------|----------|------|------|
| 2026-07-21 | 폴더 정리 및 Google Drive 동기화 | 전체 | Obsidian을 Google Drive로 이동하여 다중 기기 동기화 지원 |
| 2026-07-21 | 중복 폴더 삭제 | 02_Zotero, 04_Cloud_Shared, .obsidian | 불필요한 백업 제거, 저장소 단순화 |
| 2026-07-16 | 초기 구성 | 전체 | ThinkExploreHub 통합 설정 |

---

## 🎯 다음 단계

1. **Obsidian 설정 완료** ✅
   - Google Drive의 01_ObsidianVault를 Vault로 설정
   - 모든 기기에서 자동 동기화 확인

2. **프로젝트 개발 환경 구성**
   - `C:\Users\Kim\ThinkExploreHub\03_Projects\thinkexplore-site/` 에서 `npm install` 실행
   - 로컬 개발 서버 실행: `npm run dev`

3. **워크플로우 시작**
   - Google Drive에서 Obsidian으로 콘텐츠 작성
   - 로컬 개발 환경에서 코드 구현
   - 변경 사항은 자동으로 Google Drive에 동기화
   - 완성된 코드는 GitHub으로 푸시

---

*이 파일은 작업 진행에 따라 계속 갱신됩니다.*
