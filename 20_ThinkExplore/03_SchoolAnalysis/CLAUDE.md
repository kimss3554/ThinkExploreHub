# 03_SchoolAnalysis — 생각탐구 관악구 고교분석 플랫폼

## ⚠️ 먼저 알아야 할 것

**이 폴더가 실제 운영 중인 배포 파일이다.** 상위 `ThinkExploreHub/CLAUDE.md` 65행에 "Obsidian의 관악구고교분석 로컬 백업본"이라고 적혀 있으나 **사실과 다르다.** Obsidian Vault의 `01_ObsidianVault/관악구고교분석/index.html`은 구버전 미러이고 UNI2028·renderUniCheck 등 주요 기능이 없다. 관악구 고교분석 관련 작업은 **반드시 이 폴더의 `index.html`**에서 한다.

- **실서비스 배포(2026-08-02~)**: `kimss3554/whyylab` — 이 허브와 무관한 **별도 저장소**. GitHub Pages + 커스텀 도메인 `whyylab.com` 연결됨. **이 폴더 `index.html`을 고쳐도 자동으로 반영되지 않는다** — 반드시 `whyylab` 저장소에도 같은 파일을 복사해 커밋·push해야 실제 사이트(whyylab.com)에 뜬다. 로컬 작업 시 세션 스크래치패드는 세션마다 사라지므로, 다음 세션에서는 `git clone https://github.com/kimss3554/whyylab.git`로 새로 받아서 index.html만 덮어쓰고 push하면 된다.
- **원본 보관(소스 오브 트루스)**: 이 폴더, `kimss3554/ThinkExploreHub` 하위 — 실사이트에는 반영 안 됨, 백업 겸 원본.
- 원본 자료: `G:\내 드라이브\ThinkExploreHub\01_ObsidianVault\wiki\raw\학교자료\관악구학교자료\{학교명}\`

## SEO/GEO — 앞으로 모든 작업의 기본 목표 (2026-08-02~)

이 사이트는 구글 검색·AI 검색(ChatGPT·Perplexity·구글 AI 개요 등)에 노출·인용되는 것을 실제 목표로 삼는다. 콘텐츠·구조를 바꿀 때 항상 이 관점을 기본으로 고려할 것:

1. **핵심 사실 콘텐츠는 정적 HTML로도 노출되어야 한다.** 지금 `#schoolGrid`·비교표 등 대부분이 빈 `<div>`에 JS로 렌더링되는 구조인데, JS를 실행하지 않는 크롤러(ChatGPT·Perplexity 등 다수 AI 크롤러)는 이 내용을 전혀 못 본다 — 2026-08-02 확인: 실 서버 응답이 `<div class="grid" id="schoolGrid"></div>`처럼 텅 비어 있었음(Googlebot은 JS를 실행해서 보지만 다른 크롤러는 대부분 못 봄). **학교명·진학률·순위 같은 핵심 수치는 JS 렌더링과 별개로 정적 텍스트/표로도 페이지 소스에 존재하게 하는 것이 이상적** — 아직 미착수, 다음 작업 후보.
2. 새 섹션·데이터를 추가/수정할 때 `<title>`·meta description·OG·JSON-LD 내용이 실제 페이지 내용과 어긋나지 않도록 같이 갱신한다.
3. canonical/OG/JSON-LD URL은 `https://whyylab.com/` 기준으로 쓴다(예전 github.io 경로 아님).
4. `robots.txt`/`sitemap.xml`은 `whyylab` 저장소 루트에 있다(허브 저장소 쪽엔 없음 — 다른 프로젝트와 섞이므로 의도적으로 안 둠).

## 아키텍처

`index.html` **단일 파일**(약 8,000줄). 빌드 없음. CSS는 `<style>`, JS는 여러 `<script>` 블록에 인라인. Chart.js는 CDN.

대상 11개교: 광신고·구암고·남강고·당곡고·문영여고·미림여고·삼성고·성보고·신림고·영락고·인헌고

## 데이터 모델

| 상수 | 역할 | 비고 |
|---|---|---|
| `SCHOOL_STATS` | **정본(canonical)**. students/transfer/grad 3개년 | 여기를 먼저 고친다 |
| `TRANSFER_DATA` | 카드·차트용 최신연도 스냅샷 | `SCHOOL_STATS`와 반드시 동기화 |
| `ADV_RATE` | 4년제 진학률(%) | `SCHOOL_STATS.grad` 최신연도 `univ4/total`과 일치해야 함 |
| `META` | 카드 요약(`adv` 문자열 포함) | `ADV_RATE`와 같이 고칠 것 |
| `ARATE` | 1학년 A비율. `'5'`=현 고2, `'9'`=현 고3 | 카드 "강점"은 `'5'` 사용 |
| `TREND` | 5과목 3년 성취도 | 카드 스파크라인 |
| `SCHOOL_DETAIL` | 상세 모달 본문(`graduates`, `transfer` 등 **서술문에 수치가 박혀 있음**) | 데이터 바꾸면 여기도 반드시 갱신 |
| `SCHOOL_REPORTS`, `COMMENTS`, `COMMENTS_SHORT` | 리포트·한줄평 | 수치·순위 표현 포함 |

> **중복 주의**: 과거 `SCHOOL_YEARLY`가 같은 데이터를 3중으로 들고 있다가 값이 어긋나 실제로 오판을 유발해 2026-08-02에 제거했다. 새 중복 구조를 만들지 말 것.

### 연도 기준 (헷갈리기 쉬움)

- `transfer` = **학년도** (2025학년도 = 2025.3~2026.2)
- `grad` = **졸업 연도(2월 졸업)**. **2025년 졸업 = 2024학년도 졸업생 = 2025년 11월 공시**
- 두 지표는 공시 시차 때문에 실제 대상 코호트가 다르다. 화면 문구에 이 점을 명시할 것.

## 원자료 파싱 함정 (반복해서 당함)

1. **`.xls`가 실제로는 HTML 표다.** 학교알리미 엑셀 내보내기는 확장자만 xls이고 내용은 HTML. `openpyxl`·`xlrd` 둘 다 실패한다 → 태그 제거 후 텍스트 파싱할 것. 과거 파싱 실패본(`extracted/`, `extracted_root/`)에 "Excel 파싱 실패"가 남아 있는데, 이걸 보고 "자료 없음"으로 오판하지 말 것.
2. **졸업생 진로 원본에는 연도가 없다.** 파일명 접미사((1),(2))도 학교마다 순서가 달라 신뢰 불가(신림고 반례). → **`students[연도].g3`(3학년 재적)와 `grad[연도+1].total`을 대조**해 확정한다. 실제로 남강고 216명·영락고 등에서 이 방법으로 확정했다.
3. **중복 다운로드 파일 주의.** 남강고·영락고는 3개 파일 중 2개가 동일 공시분이라 한 해가 비어 있었다. 값이 완전히 같으면 중복을 의심할 것.
4. 검증 앵커: 계산한 11개교 평균 학업중단율이 **공시 관악구 평균(1.9%)** 과 맞는지, 재적수가 `students` 총계와 맞는지 확인.

## 프리미엄(로그인) 게이팅

- 상태: `localStorage.sjtg_unlocked === '1'`
- 테스트: 콘솔에서 `localStorage.setItem('sjtg_unlocked','1')` 후 리로드
- 잠금 탭은 `LOCK_CONTENT_ID` 맵 + 공용 `#premium-lock` 배너를 활성 탭으로 옮겨 표시
- `#pwInput`은 `type=password`로 마스킹 처리되어 있다(2026-08-02 수정). 단, `PREMIUM_PASSWORD` 상수는 클라이언트 JS에 평문으로 남아 있어 view-source로는 확인 가능 — 백엔드 없이는 근본적으로 못 숨긴다. 관리자 비번은 노출 안 함.
- **후기(`#full-reviews`)는 로그인 없이 항상 노출**되어야 한다. 반드시 **모든 `.tab-panel` 바깥**에 둘 것 — 탭 안에 있으면 `setTab()`이 그 패널을 숨기는 순간 스크롤 대상이 사라진다(실제 발생했던 버그).

## 작업 규칙

- **`git add index.html`만.** `git add -A`/`.` 금지 — 허브 저장소에 무관한 다른 프로젝트 변경이 항상 섞여 있다. 새 이미지 에셋 추가 시에만 그 파일명을 함께 add.
- **push는 매번 명시적으로 물어본 뒤에만.** 이전에 승인받았다고 다음 push까지 자동 진행하지 않는다.
- 커밋 메시지는 한국어로, 무엇을·왜 바꿨는지 적는다.

## 검증 절차

```bash
# 1) 모든 <script> 블록 문법 검사
node -e "const h=require('fs').readFileSync('index.html','utf8');
[...h.matchAll(/<script(?:\s[^>]*)?>([\s\S]*?)<\/script>/g)].forEach((m,i)=>{
  try{new Function(m[1])}catch(e){console.log('script',i,e.message)}});console.log('OK')"

# 2) 로컬 서버 (캐시버스팅 ?v=N 매번 변경)
python -m http.server 8800
```

데이터 정합성은 `SCHOOL_STATS` ↔ `TRANSFER_DATA` ↔ `ADV_RATE` 3자 일치와 11개교×3년 결측 0을 스크립트로 확인한다.

### 이 환경의 브라우저 제약 (중요)

Browser 패널이 프레임을 합성하지 않아 다음이 **모두 실패하거나 오해를 부른다**:
- 스크린샷 → "not compositing frames" 타임아웃
- Chart.js 캔버스 → 크기가 계속 `0×0` (코드 문제가 아님)
- `scroll-behavior:smooth` → 애니메이션이 돌지 않아 스크롤 직후 측정하면 `0`

→ **`javascript_exec`로 DOM을 측정해 검증한다.** `Chart.getChart(el)`로 차트 데이터 확인, `getComputedStyle`/`getBoundingClientRect`로 레이아웃 확인, 스크롤은 `window.scrollTo`를 가로채 호출 좌표를 확인. 시각 확인이 꼭 필요하면 사용자에게 요청할 것.

## 디자인 시스템

`.claude/skills/snu-design-system/SKILL.md` 참조 (서울대 스타일). 요점:
- 각진 모서리(`border-radius:0`) 전면 적용
- 색상 규칙: 네이비=브랜드, 초록=개선/성공, 빨강=악화/경고, 회색=중립. **앰버는 좁게만** ("너무 컬러풀하다"는 피드백 반복됨)
- 가치판단이 애매한 지표(전입·전출 증감 등)는 색을 주지 말고 중립 회색
- 표는 전 항목 가운데 정렬, 명조는 타이틀에만
- 폰트 굵기 추가 시 Google Fonts import에도 반드시 추가(안 하면 가짜 볼드로 흐릿해짐)

## 진행 상황 (2026-08-02)

**완료** — 11개교 × 2023·2024·2025 전출입·진학률 데이터 완비(결측 0). 진행 중 발견해 교정한 오류: 진학률 4건(구암고는 2년 낡은 값, 당곡·문영·인헌은 추정치), 광신고 진로 구성비, 성보고 "관악구 최저" 서술. 학업중단율은 항목별 꺾은선 3종 + 수치표 + 해석으로 재구성, 진학률은 4년제·전문대 3개년 대조 차트 추가.

**미완** — **메뉴 2depth 개편**. 계획서: `C:\Users\Kim\.claude\plans\clever-twirling-possum.md`. 한 페이지에 전부 나열되는 현재 구조를 1depth(11개교/학교비교/수행평가/선택과목/입시달력) → 2depth 서브메뉴로 바꾸는 작업. 미결 질문 4가지가 남아 있다:
1. 선택과목 9개 카드를 평면 나열할지 2그룹으로 묶을지
2. 메뉴에 연결 안 된 죽은 탭 `data-tab="gib"`(생기부 강점 분석) 처리 — 합칠지/두 될지/삭제할지
3. 드로어 아코디언에 화살표 아이콘을 넣을지
4. 한 번에 전체 진행할지 11개교 탭만 파일럿으로 먼저 할지

**남은 자료 과제** — 대학별 진학 현황(SKY·수도권 등) 미확보. 취업·국외진학 세부도 미수집.

## 진행 상황 (2026-08-02, 도메인·SEO)

**완료** — whyylab.com 도메인 구매(가비아) 및 GitHub Pages 연결, HTTPS 인증서 발급·Enforce HTTPS 적용, Google Search Console 도메인 속성 소유권 확인(TXT 레코드), robots.txt·sitemap.xml 추가. meta description·canonical·OG·Twitter Card·JSON-LD(EducationalOrganization) 추가.

**완료** — "SEO/GEO 원칙" 1번 실행: `#schools` 섹션에 11개교 진학률·학업중단율 정적 `<table>` 추가(schoolGrid 위, JS 없이도 원본 HTML에 노출). raw.githubusercontent.com으로 캐시 우회해 실제 반영 확인함.

**다음 후보** — Search Console에 sitemap 제출 여부 미확인. 다른 탭(학교비교·수행평가·선택과목 등)도 같은 문제(JS 전용 렌더링)가 있는지 점검 필요.
