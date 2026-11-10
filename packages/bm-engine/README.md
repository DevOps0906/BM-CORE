# packages/bm-engine

계산 엔진. 공식·배분·시나리오·스코어를 순수 함수로 구현한다.

| 항목 | 내용 |
|---|---|
| 책임 | `fixtures/`·`tests/`(선행), `domain/`(money·metrics·pricing·cost-allocation·scenarios·scorecard), `calculators/`·`validators/` |
| 금지 | I/O, React, Supabase, 시계, 난수, 금액 부동소수점. 기존 테스트 하나라도 실패 시 병합 금지 |
| 담당 작업 ID | BM-06-018(테스트 선행), 019, 020, 025(`domain/scorecard`) |
| 근거 문서 | [ARCHITECTURE.md#2](../../docs/ARCHITECTURE.md), [AGENT_PLAN.md#1](../../docs/AGENT_PLAN.md), [CALCULATION_ENGINE.md](../../docs/CALCULATION_ENGINE.md) |

상태: 기획 승인 전, 코드 없음
