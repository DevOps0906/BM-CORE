# apps/web/app/api/v1

Route Handler. 입력 Zod 검증 → `requireSession('bm')` → 엔진·RPC 호출.

| 항목 | 내용 |
|---|---|
| 책임 | organizations·projects·versions·wizard·scenarios·calculations·hypotheses·experiments·scorecards·jobs(GET)·reports·share-links·ai 엔드포인트 |
| 금지 | 비즈니스 계산 구현, 코어 테이블 신규 생성(코어 RPC 호출만) |
| 담당 작업 ID | BM-06-012, 013, 015, 021, 023, 025, 027, 028, 030 |
| 근거 문서 | [ARCHITECTURE.md#2](../../../../../docs/ARCHITECTURE.md), [AGENT_PLAN.md#1](../../../../../docs/AGENT_PLAN.md), [API.md](../../../../../docs/API.md) |

상태: 기획 승인 전, 코드 없음
