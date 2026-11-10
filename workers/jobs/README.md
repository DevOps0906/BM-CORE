# workers/jobs

`core.jobs` 큐 워커 핸들러(큐·claim·재시도는 코어 사용).

| 항목 | 내용 |
|---|---|
| 책임 | 핸들러 `report.render`(큐 `bm.report`)·`ai.suggest`(큐 `bm.ai`), `reports/`(계측·운영) |
| 금지 | 도메인 판단(엔진·orchestrator 호출만), 큐 신규 구현, payload·로그에 비밀값·본문 |
| 담당 작업 ID | BM-06-027, 040(`reports/`) |
| 근거 문서 | [ARCHITECTURE.md#2·#4](../../docs/ARCHITECTURE.md), [AGENT_PLAN.md#1](../../docs/AGENT_PLAN.md), [API.md#4](../../docs/API.md) |

상태: 기획 승인 전, 코드 없음
