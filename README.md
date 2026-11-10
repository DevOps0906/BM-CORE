# BM-CORE

사업 아이템의 사업모델(BM)을 **숫자와 증거로 검증**하고, 그 결과를 **사업계획서 재료**로 쌓아 두는 저장소입니다. BM 7단계 방법론, 비즈니스 모델 캔버스(9블록), 사업계획서(PSST) 매핑, 그리고 같은 방법을 SaaS로 만드는 BM-Core 기획서를 담습니다.

- 제품을 "무엇을 만드는가"(기획 정본)는 [platform-docs](https://github.com/DevOps0906/platform-docs)가, "왜 돈이 되는가"(고객·가격·단위경제·검증·점수)와 사업계획서 재료는 이 저장소가 맡습니다.
- 계산은 모델이 하지 않습니다. [nomad-agent-os](https://github.com/DevOps0906/nomad-agent-os)의 `bm-calc`가 계산하고, `/bm <아이템>`이 7단계를 진행합니다.
- 모든 수치는 가정(제안)이며 검증하면서 실제 데이터로 바꿉니다.

## 진행 현황 (2026-11-11 기준)

방법론·템플릿·매핑 문서와 BM-Core 기획서는 작성을 마쳤습니다. 실제 아이템의 BM(`projects/`)은 아직 없습니다.

| 영역 | 현재 상태 |
|---|---|
| 방법론 | BM 7단계, 루브릭(5축 × 4지표 × 0~5점), 증거 등급 A~E, 판정 구간 — 작성 |
| 캔버스 | 9블록 템플릿과 7단계 대응, BookForge 예시 — 작성 |
| 사업계획서 매핑 | PSST(문제인식·실현가능성·성장전략·팀 구성) 대응과 증거 인용 규칙 — 작성. 공고별 양식 세부는 미확인 |
| BM-Core SaaS 기획 | README, 01~09, CLAUDE.md — 작성(platform-docs에서 이동). SQL·개발은 기획 승인 후 |
| 아이템별 BM | 없음 |

### 다음 단계
- [ ] 첫 아이템 선정 후 `/bm <아이템>`으로 `projects/<아이템>/` 생성
- [ ] 린 검증(인터뷰·사전예약) 결과를 증거로 등록해 검증도 점수 갱신
- [ ] 지원사업 공고가 정해지면 PSST 매핑의 양식 항목 확정
- [ ] BM-Core 기획서 열린 결정(`product/01_PRD.md` 8장) 확정

## 콘텐츠 바로가기

| 콘텐츠 | 문서 | 쓰임 |
|---|---|---|
| BM 7단계 방법론 | [`method/BM_METHOD.md`](method/BM_METHOD.md) | 모든 아이템의 BM 작성 기준 |
| 비즈니스 모델 캔버스 | [`canvas/BMC_TEMPLATE.md`](canvas/BMC_TEMPLATE.md) | 9블록 작성, 7단계 결과 옮기기 |
| 사업계획서 매핑 | [`business-plan/PSST_MAPPING.md`](business-plan/PSST_MAPPING.md) | 캔버스·계산·증거 → 사업계획서 목차 |
| 아이템별 결과 | [`projects/`](projects/README.md) | BM.md · canvas.md · 증거 · 사업계획서 초안 |
| BM-Core SaaS 기획서 | [`product/`](product/README.md) | PRD, 아키텍처, 화면, API, 데이터, 작업 분해, 계산 엔진, 다이어그램 16종 |
| 원본 자료 | [`research/00_SOURCE_DESIGN.md`](research/00_SOURCE_DESIGN.md) | BM 7단계·BM-Core 설계안 정리본 |

전체 다이어그램 16종은 [`product/09_DIAGRAMS.md`](product/09_DIAGRAMS.md)에 있습니다.

## 사업계획서 연관 구조도

### 1. 전체 흐름
아이디어에서 지원사업 양식까지 BM 산출물이 흐르는 순서입니다.

```mermaid
flowchart LR
  idea["아이디어"] --> bm7["BM 7단계"]
  bm7 --> canvas["캔버스 9블록"]
  canvas --> econ["단위경제·검증·점수"]
  econ --> psst["사업계획서 PSST"]
  psst --> form["지원사업 양식"]
```

### 2. BM 7단계와 판정 분기
7단계 스코어를 blocking 조건과 80/60/40 구간으로 나누고, 낮은 구간은 6단계 검증으로 돌아갑니다.

```mermaid
flowchart TD
  s1["1 고객·문제"] --> s2["2 가치 제안"]
  s2 --> s3["3 수익모델·가격 가설"]
  s3 --> s4["4 단위경제"]
  s4 --> s5["5 파트 분리·공통비 배분"]
  s5 --> s6["6 린 검증 설계"]
  s6 --> s7["7 사업성 스코어"]
  s7 --> b1{"blocking 조건"}
  b1 -->|"있음"| hold["보류·폐기 on_hold"]
  b1 -->|"없음"| sc1{"총점 구간"}
  sc1 -->|"80 이상"| ready["개발·신청 ready"]
  sc1 -->|"60~79"| val["추가 검증 needs_validation"]
  sc1 -->|"40~59"| redo["축소 redesign"]
  sc1 -->|"40 미만"| hold
  val -->|"부족한 축 검증 후 복귀"| s6
  redo -->|"노코드 MVP로 축소 후 복귀"| s6
```

### 3. 비즈니스 모델 캔버스 구조
캔버스 9블록의 표준 배치입니다. 블록마다 답할 질문을 함께 적었습니다. 작성 양식은 [`canvas/BMC_TEMPLATE.md`](canvas/BMC_TEMPLATE.md)에 있습니다.

```mermaid
block-beta
  columns 5
  KP["핵심 파트너 KP<br/>누구와 함께 하는가"]
  block:left:1
    columns 1
    KA["핵심 활동 KA<br/>무엇을 해야 하는가"]
    KR["핵심 자원 KR<br/>무엇이 필요한가"]
  end
  VP["가치 제안 VP<br/>고객에게 무엇을 해결해 주는가"]
  block:right:1
    columns 1
    CR["고객 관계 CR<br/>고객과 어떻게 관계를 맺는가"]
    CH["채널 CH<br/>어떻게 고객에게 닿는가"]
  end
  CS["고객 세그먼트 CS<br/>누구를 위해 가치를 만드는가"]
  block:bottom:5
    columns 2
    COST["비용 구조 C$<br/>무엇에 돈이 드는가"]
    REV["수익원 R$<br/>고객이 무엇에 얼마를 내는가"]
  end
```

블록끼리 이어지는 흐름입니다. 왼쪽 블록(파트너·활동·자원)은 비용을 만들고, 오른쪽 블록(채널·관계·고객)은 수익을 만듭니다. 둘의 차이는 4단계 단위경제로 검증합니다. 작성 순서는 템플릿 3장을 따릅니다. 고객 세그먼트와 가치 제안을 먼저 쓰고, 수익원과 비용 구조를 이어서 쓴 다음, 나머지 블록을 채웁니다.

```mermaid
flowchart LR
  subgraph eff["효율 · 왼쪽"]
    KP["핵심 파트너"] --> KA["핵심 활동"]
    KR["핵심 자원"]
  end
  subgraph val["가치 · 오른쪽"]
    CH["채널"] --> CS["고객 세그먼트"]
    CR["고객 관계"] --> CS
  end
  KA --> VP["가치 제안"]
  KR --> VP
  VP --> CH
  VP --> CR
  CS -->|"결제"| REV["수익원"]
  KP --> COST["비용 구조"]
  KA --> COST
  KR --> COST
  REV --> PROFIT{"수익원 − 비용 구조"}
  COST --> PROFIT
  PROFIT -->|"4단계 공헌이익·BEP로 검증"| CHECK["단위경제"]
```

### 4. 7단계와 캔버스 9블록 대응
BM 7단계 각 단계의 산출물이 비즈니스 모델 캔버스의 어느 블록을 채우는지 보여줍니다.

```mermaid
flowchart LR
  subgraph bm["BM 7단계"]
    direction TB
    a1["1 고객·문제"]
    a2["2 가치 제안"]
    a3["3 수익모델·가격"]
    a4["4 단위경제"]
    a5["5 파트 분리"]
    a6["6 린 검증"]
    a7["7 사업성 스코어"]
  end
  subgraph cv["캔버스 9블록"]
    direction TB
    c1["고객 세그먼트"]
    c2["가치 제안"]
    c3["채널"]
    c4["고객 관계"]
    c5["수익원"]
    c6["핵심 자원"]
    c7["핵심 활동"]
    c8["핵심 파트너"]
    c9["비용 구조"]
  end
  a1 --> c1
  a2 --> c2
  a6 --> c3
  a5 --> c3
  a4 --> c4
  a5 --> c4
  a3 --> c5
  a4 --> c5
  a5 --> c6
  a7 --> c6
  a5 --> c7
  a6 --> c7
  a5 --> c8
  a4 --> c9
  a5 --> c9
```

### 5. 캔버스·7단계와 PSST 사업계획서 목차 대응
사업계획서 PSST 네 항목에 어떤 캔버스 블록과 단계 데이터가 들어가는지 보여줍니다. 실제 목차는 공고별로 확인합니다.

```mermaid
flowchart LR
  subgraph cv["캔버스 9블록"]
    direction TB
    c1["고객 세그먼트"]
    c2["가치 제안"]
    c3["채널"]
    c4["고객 관계"]
    c5["수익원"]
    c6["핵심 자원"]
    c7["핵심 활동"]
    c8["핵심 파트너"]
    c9["비용 구조"]
  end
  subgraph bm["BM 7단계"]
    direction TB
    t1["1 고객·문제"]
    t2["2 가치 제안"]
    t3["3 수익모델·가격"]
    t4["4 단위경제"]
    t5["5 파트 분리"]
    t6["6 린 검증"]
    t7["7 사업성 스코어"]
  end
  subgraph psst["사업계획서 PSST"]
    direction TB
    p1["문제인식"]
    p2["실현가능성"]
    p3["성장전략"]
    p4["팀 구성"]
  end
  c1 --> p1
  c2 --> p1
  c3 --> p1
  t1 --> p1
  t3 --> p1
  t7 --> p1
  c2 --> p2
  c7 --> p2
  t2 --> p2
  c6 --> p2
  t6 --> p2
  c5 --> p2
  t3 --> p2
  c3 --> p2
  c4 --> p2
  c9 --> p2
  t4 --> p2
  t5 --> p2
  c3 --> p3
  c4 --> p3
  t6 --> p3
  t5 --> p3
  c5 --> p3
  c9 --> p3
  t4 --> p3
  t7 --> p3
  c8 --> p3
  c6 --> p4
  t7 --> p4
  c8 --> p4
  t5 --> p4
  t4 --> p4
```

### 6. 증거 등급에서 사업계획서 근거 문장까지
증거 등급 A~E가 점수와 판정을 거쳐 사업계획서 근거 문장이 되는 경로입니다. E 등급은 채점하지 않고 가정으로만 표기합니다.

```mermaid
flowchart TD
  eA["A 실결제·계약·사용 로그"]
  eB["B 고객 행동·사전예약"]
  eC["C 인터뷰·설문"]
  eD["D 경쟁사·시장 조사"]
  eE["E AI 추정·창업자 가정 (미검증)"]
  eA --> sc["등급·출처·측정 방법 기록"]
  eB --> sc
  eC --> sc
  eD --> sc
  eE --> asm["가정으로만 표기 (채점 제외)"]
  sc --> axis["축별 점수 (5축 x 20점)"]
  axis --> tot["총점 0~100과 판정 구간"]
  tot --> sent["사업계획서 근거 문장"]
  asm --> sent
```

### 7. 단위경제 계산 흐름
ARPU에서 공헌이익을 거쳐 LTV, CAC 상한, 회수 기간, 손익분기와 월 영업손익까지 이어지는 계산 순서입니다.

```mermaid
flowchart TD
  rev["기간 매출"] --> arpu["ARPU 매출 / 평균 유료 고객"]
  cust["평균 유료 고객 수"] --> arpu
  var["고객당 변동비 합"] --> cm["공헌이익 CM 매출 - 변동비"]
  arpu --> cm
  cm --> cmr["공헌이익률 CM / 매출"]
  churn["월 이탈률"] --> ltv["단순 LTV CM / 이탈률"]
  cm --> ltv
  ltv --> ratio["LTV/CAC 실제 CAC 기준"]
  cac["실제 CAC 가정"] --> ratio
  ltv --> ceil["CAC 상한 LTV / 목표 배수"]
  cm --> payback["CAC 회수 기간 CAC / CM"]
  cac --> payback
  fixed["월 고정비"] --> bep["손익분기 고객 수 고정비 / CM 올림"]
  cm --> bep
  cm --> tcm["총 공헌이익 CM x 고객 수"]
  cust --> tcm
  tcm --> op["월 영업손익 총 CM - 고정비"]
  fixed --> op
```

### 8. 사업성 평가 상태 전이
스코어카드가 draft에서 시작해 점수와 blocking 조건에 따라 보류, 재평가, 승인 경로로 이동하는 상태 흐름입니다.

```mermaid
stateDiagram-v2
  [*] --> draft
  draft --> validating
  validating --> scored
  state "보류·폐기" as on_hold
  state "개발·신청" as ready
  state "추가 검증" as needs_validation
  state "축소 재설계" as redesign
  state "승인" as approved
  scored --> on_hold : blocking 있음 또는 40 미만
  scored --> ready : 80 이상
  scored --> needs_validation : 60~79
  scored --> redesign : 40~59
  ready --> approved : owner admin 승인
  ready --> on_hold : owner admin 보류
  needs_validation --> draft : 재평가
  redesign --> draft : 재평가
  on_hold --> draft : 재평가
  approved --> [*]
```

### 9. 데이터 구조
프로젝트, 캔버스, 가설, 증거, 점수, 보고서(사업계획서 출력) 테이블의 관계입니다. 05_DATA_MODEL.md 1절 요약을 따릅니다.

```mermaid
erDiagram
  PROJECTS ||--o{ PROJECT_VERSIONS : "버전"
  PROJECT_VERSIONS ||--o{ CUSTOMER_SEGMENTS : "고객"
  PROJECT_VERSIONS ||--o{ VALUE_PROPOSITIONS : "가치"
  PROJECT_VERSIONS ||--o{ HYPOTHESES : "가설"
  PROJECT_VERSIONS ||--o{ ECONOMIC_SCENARIOS : "시나리오"
  PROJECT_VERSIONS ||--o{ SCORECARDS : "점수"
  PROJECT_VERSIONS ||--o{ REPORTS : "보고서"
  HYPOTHESES ||--o{ EXPERIMENTS : "실험"
  EXPERIMENTS ||--o{ EVIDENCE : "증거"
  ECONOMIC_SCENARIOS ||--o{ CALCULATION_RUNS : "계산"
  RUBRICS ||--o{ SCORECARDS : "루브릭"
  SCORECARDS ||--o{ SCORE_ITEMS : "항목"
  SCORE_ITEMS }o--o{ EVIDENCE : "근거"
```

### 10. 레포 관계
BM-CORE, platform-docs, nomad-agent-os가 맡는 역할과 연결 지점입니다.

```mermaid
flowchart LR
  pd["platform-docs 제품 기획 정본"] <-->|"BM 근거 링크"| bmc["BM-CORE 사업성·사업계획서 근거"]
  bmc <-->|"/bm 결과 저장·방법론 정본"| nomad["nomad-agent-os /bm·bm-calc"]
```

## 연관 저장소

| 레포 | 역할 |
|---|---|
| [platform-docs](https://github.com/DevOps0906/platform-docs) | 제품 기획 정본, 가격 플랜(`Price_Plans/`). 2026-11-11 BM 문서를 이 저장소로 옮김 |
| [nomad-agent-os](https://github.com/DevOps0906/nomad-agent-os) | `/bm` 명령, `bm-model` 스킬, `bm-calc` 계산기 |
