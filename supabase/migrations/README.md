# supabase/migrations

`bm` 스키마 마이그레이션 2700~2740(번호는 10단위).

| 항목 | 내용 |
|---|---|
| 책임 | 2700 스키마·projects·versions·wizard_steps, 2710 모델 입력, 2720 경제성, 2730 검증·스코어, 2740 출력·전 테이블 RLS·GRANT |
| 금지 | `core.*` ALTER·신규 생성, `bm` 외 스키마 |
| 담당 작업 ID | BM-06-003(2700·2710), 004(2720~2740), 005(`*rls*.sql`) |
| 근거 문서 | [DATABASE.md#9](../../docs/DATABASE.md), [AGENT_PLAN.md#2](../../docs/AGENT_PLAN.md), [ARCHITECTURE.md#2](../../docs/ARCHITECTURE.md) |

상태: 기획 승인 전, 코드 없음
